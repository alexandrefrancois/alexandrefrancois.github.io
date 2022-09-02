---
layout: post
title: Digital Resonator (II)
date: 2022-09-02 20:22:09 UTC
updated: 2022-09-02 20:22:09 UTC
comments: false
categories: music physics oscillators
---

I's been a productive week off! I published the first version of the [Oscillators app](/Oscillators/), [available for download](https://apps.apple.com/us/app/oscillators/id1641353759) on the Apple App Store, and I released a first version of the code for my resonator implementation (and more) as a [Swift package](https://github.com/alexandrefrancois/Oscillators).

I outlined the main ideas underlying my digital resonator model in my last post: [Digital Resonator](/music/physics/oscillators/2022/08/08/Digital-Resonator.html). In this post I give a few more geeky details.

Just to be clear about the objectives, the really exciting fun starts from something like this: a bank of oscillators tuned at a range of frequencies, that resonate in real-time with the input signal from the microphone, and possibly interact with each other. Getting to this requires a model that captures the resonance behavior, and that can be implemented efficiently (a reference point for comparison would be the ubiquitous FFT).

### Basic concepts

Human perception is fundamentally dynamic: it's about change over time. A quantity that varies over time is called a _signal_. Acoustic signals consist of pressure waves that cause the air to vibrate. A microphone converts an acoustic signal into an electric signal. Because digital computers can only manipulate discrete data, this analog electric signal must be converted into a _digital signal_. All it means is that the signal cannot be represented in the computer with infinite precision, so the quantity can only take discrete values (_quantization_) and we only know the values at certain discreet times (_sampling_). For sound the samples are usually taken at constant intervals (expressed in seconds), whose inverse is the _sampling rate_ (expressed in Hz, equivalent to "per second"), that is the number of samples per unit of time. A common sampling rate for sound is 44100Hz, and we'll see why in a bit.

A _periodic signal_ repeats the sequence of values exactly after a fixed length of time, known as the _period_. The _frequency_ (in Hz) is the inverse of the period duration (in s), i.e. the number of times the period is repeated per seconds. A periodic signal is entirely specified by one period, as the values repeat indefinitely. 

Examples of periodic signals include sine, square, triangle and saw waves, and there are many apps and online sites that offer tools to generate sound from such simple periodic signals (tones), see for example [Michael Gieson](https://www.gieson.com/)' [ToneGen](https://www.gieson.com/Library/projects/utilities/tonegen/). Explore the richness of digital synthesis in electronic music at [Music Makers Machines](https://artsandculture.google.com/project/music-makers-and-machines) (but please come back here I'm not done - even better, save it for later).

A few hundred years ago, long before electronic digital computers, [Fourier](https://en.wikipedia.org/wiki/Joseph_Fourier) posited that any periodic signal can be expressed as an infinite sum of sines and cosines (_Fourier expansion_), a powerful concept that underlies [harmonic analysis](https://en.wikipedia.org/wiki/Harmonic_analysis), and relates to how humans perceive sound. Discrete versions of the associated mathematical tools, suitable for efficient implementation on early digital computers, reinforced the success of these techniques (for example the ubiquitous Fast Fourier Transform or FFT) and their wide adoption in a variety of fields. The FTT takes a portion of signal (values over time) and computes the values for each frequency band in the appropriate discrete truncated Fourier expansion (the frequency range is limited by the duration of the signal portion).

I am exploring a completely different approach, in which the signal is fed possibly in real-time to a resonator tuned to a specific frequency, and the resulting amplitude of oscillations captures the presence of the resonant frequency in the input signal. A bank of such resonators tuned at various frequencies arguably captures valuable information about the incoming signal, akin to (but in many ways fundamentally different from) what the FFT captures.

But before we move on to oscillators and resonators, one important constraint when digitizing a periodic signal is that the sampling rate must be twice the frequency of the highest frequency component to be captured. This is known as the _Nyquist frequency_. The audible range of frequency is roughly 20Hz to 20000Hz, which is why sampling an audio signal at 44100kHz ensures that all audible frequencies in the signal are captured in the resulting digital version.

For real-time audio signal processing, we'll need to do some computations at the sampling rate, i.e. several tens of thousand times per second. We can leverage GPUs to perform floating point operations efficiently, especially if we can parallelize some of the work.

### Oscillator design

An oscillator is entirely specified by its frequency (or period duration), waveform and amplitude.

The sampling rate (or sample duration) turns out to be an important parameter that is worth imposing as a fixed input parameter.
Indeed, introducing the constraint that **the period duration be a multiple of the sample duration** greatly simplifies the model and the computations. In this case, the components of the model are the amplitude (a scaling factor) and an array, whose length is the number of samples in the period, and which contains the waveform value at each sample time.

This means however that by design, such oscillators cannot be tuned to any arbitrary frequency, but only to frequencies that correspond to a period duration that is a multiple of the sample duration.

To generate a signal at the chosen sampling rate, all that is needed is a pointer that keeps track of the oscillator's position in the period, in this case an index into the waveform.

At each tick of the clock (driven by the sampling rate of the output signal),
- advance the pointer to the next position
  - if past the end of the waveform, go back to first position (= repeat the period)
- take the waveform value at the current position,
- output the value scaled by the amplitude

Again, this is extremely simplistic; there are much more sophisticated models for signal synthesis, which is not our main concern here.

### Resonator design

A resonator is an oscillator which, when submitted to an input signal, oscillates with a larger amplitude when its resonant frequency is present in the input signal.

A resonator is characterized by its (resonant) frequency and the shape of its periodic signal, captured in the oscillator model as the waveform array.

The resonator's amplitude is updated at each tick of the clock, i.e. for each input sample, from the resonator's current amplitude value _a_ (in [0,1]), its current position in the oscillation period (waveform value _w_, in [-1,1]), and the input sample value _s_ (in [-1,1]):  
_a <- (1-k) * a + k * s * w_  

The pattern _v <- (1-k) * v + k * s_, where k is a constant in [0,1] is known as a low-pass filter, as it smooths out high frequency variations in the input signal. The constant _k_ dictates the "smoothing", in this case the dynamic behavior of the system, i.e. how quickly it adapts to variations in the input signal.

The instantaneous contribution of each input sample value to the amplitude is proportional to _s * w_, which intuitively will be maximal when peaks in the input signal and peaks in the resonator's waveform are both equally spaced and aligned, i.e. when they have same frequency and are in phase.

Note that this is where traditions would suggest essentially taking the signal offline and maybe doing a convolution with the waveform as the kernel (or just do an FFT and be done with it!), but I would rather recognize and accept that we don't know the future and we cannot always afford to wait for it to become the past, and thus favor a more dynamic approach.

In order to account for phase offset, the above calculation is performed for various phases, and the resonator's amplitude is set to the maximum value across all phases. The phase offset resolution is also conveniently the sample duration so the resonator model adds to the oscillator model an array of same length as the resonator's period, where each position stores the amplitude amplitude value for the corresponding phase offset.

The floating-point calculations to carry for each input sample can be performed in parallel for each phase, so perfectly suited to leverage GPU acceleration. The complexity is linear in the number of phases, i.e. the number of samples in one period, which for low frequencies in the audible spectrum typically reaches a few thousands.

This means a reasonable implementation on modern hardware should easily handle the computations per sample for any frequency. For real-time audio processing, these computations must typically be carried several tens of thousands of times per second. So while the computations themselves should be cheap, the setup overhead (for example copying data to/from GPU memory where required) could become a limiting factor, especially when running a number of resonators in the context of a music analysis app.

I implemented several versions of this model, all leveraging the Accelerate framework: the first proof of concept uses Swift arrays, a much more efficient version in Swift uses "unsafe pointers", and I also made a C++ version, wrapped in Objective-C++ to bridge with Swift. The Swift arrays overhead proved prohibitively significant, so the app features the Swift "unsafe arrays" and the C++ implementations, in the exact same setting, so that the computation times can be directly compared. The C++ implementation seems to consistently outperform the Swift implementation - but this should of course be explored and confirmed in a more thoroughly and and systematically.

<table align="left" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: left;"><tbody>
<tr><td>Frequency</td><td>Samples / period</td><td>ns / sample</td></tr>
<tr><td>2205Hz</td><td>20</td><td>S: 395<br>C++:210</td></tr>
<tr><td>441Hz</td><td>100</td><td>S: 550<br>C++:350</td></tr>
<tr><td>110.25Hz</td><td>400</td><td>S:990 <br>C++:830</td></tr>
<tr><td>20Hz</td><td>2,114</td><td>S: 1500<br>C++:1200</td></tr>
<tr><td colspan=3 style="text-align: center;">Representative approximate processing time per sample for various frequencies observed on an iPhone 13 mini</td></tr>
</tbody></table>

### Demonstrations

Check out the Oscillators playlist on my YouTube channel for fun expriments with the Oscillators app.

<iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLVcB_ABiKC_djwV2PXnSCWkvXOXt8PRMC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Then go explore [Music Makers Machines](https://artsandculture.google.com/project/music-makers-and-machines) :-)