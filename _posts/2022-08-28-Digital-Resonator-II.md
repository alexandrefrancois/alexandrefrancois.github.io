---
layout: post
title: Digital Resonator (II)
date: 2022-08-28 20:22:08 UTC
updated: 2022-08-29 20:22:08 UTC
comments: false
categories: music physics oscillators
---

With the first version of the [Oscillators app](/Oscillators/) now available (for free!) on the App Store, I thought I'd share a few geeky details of my resonator implementation.

Just to be clear about the objectives, the really exciting fun starts from something like this: a bank of oscillators tuned at a range of frequencies, that resonate in real-time with the input signal from the microphone, and interact with each other.

Getting to this requires a model that captures the resonance behaviour, and that can be implemented efficiently (a reference point for comparison would be the now ubiquitous FFT).

### Basic concepts

The physical phenomenon we experience as sound consists of a pressure wave that causes the medium to vibrate.

A _signal_ is a quantity that varies over time. For sound, the quantity is pressure. A microphone converts pressure variations into an electric signal. Because digital computers can only manipulate discrete data, this analog electric signal must be converted into a _digital signal_. All it means is that the signal cannot be represented with infinite precision, so the quantity can only take discrete values (_quantization_) and we only know the values at certain discreet times (_sampling_). For sound the samples are taken at constant intervals (expressed in seconds), whose inverse is the sampling rate (expressed in Hz, equivalent to "per second"), that is the number of samples per unit of time. A common sampling rate for sound is 44100Hz, and we'll see why in a bit.

A _periodic signal_ repeats the sequence of values exactly after a fixed length of time, known as the _period_. The _frequency_ (in Hz) is the inverse of the period duration (in s), i.e. the number of times the period is repeated per seconds. A periodic signal is entirely specified by one period, as the values repeat indefinitely. 

Examples of periodic signals include sine, square, triangle and saw waves, and there are many apps and online sites that offer tools to generate sound from such simple periodic signals (tones), see for example [Michael Gieson](https://www.gieson.com/)' [ToneGen](https://www.gieson.com/Library/projects/utilities/tonegen/).

Fourier showed that any periodic signal can be expressed as an infinite sum of sines and cosines (Fourier expansion), an extremely powerful concept that forms the basis for harmonic analysis, and relates closely to how humans perceive sound. Discrete versions of the associated mathematical tools, suitable for efficient implementation on early computers (for example the famous and now ubiquitous Fast Fourier Transform or FFT), contributed to the success and wide adoption of these techniques in a wide variety of fields.

One important constraint when digitizing a periodic signal is that the sampling rate must be twice the frequency of the highest frequency component to be captured. This is known as the Nyquist frequency. The audible range of frequency is roughly 20Hz to 20000Hz, which is why sampling an audio signal at 44100kHz ensures that all audible frequencies in the signal are captured in the resulting digital version.

For real-time audio signal processing, we'll need to do some computations at the sampling rate, i.e. many thousand times per second. We can leverage GPUs to perform floating point operations efficiently, especially if we can parallelize some of the work.

### Oscillator design

An oscillator is entirely specified by its frequency (or period duration), waveform and amplitude.

The sampling rate (or sample duration) turns out to be an important parameter that is worth considering a fixed input parameter.
Indeed, introducing the constraint that **the period duration be a multiple of the sample duration** greatly simplifies the model and the computations. In this case, the components of the model are the amplitude (a scaling factor) and an array, whose length is the number of samples in the period, and which contains the waveform value at each sample time.

This means however that by design, such oscillators cannot be tuned to any arbitrary frequency, but only to frequencies that correspond to a period duration that is a multiple of the sample duration.

To generate a signal at the chosen sampling rate, all that is needed is a pointer that keeps track of the oscillator's position in the period, in this case an index into the waveform.

At each tick of the clock (driven by the sampling rate of the output signal),
- advance the pointer to the next position
  - if past the end of the waveform, go back to first position (= repeat the period)
- take the waveform value at the current position,
- output the value scaled by the amplitude

### Resonator design

A resonator is an oscillator which, when submitted to an input signal, oscillates with a larger amplitude when its resnonant frequency is present in the input signal.

A resonator is characterized by its (resonant) frequency and the shape of its periodic signal, captured in the oscillator model as the waveform array.

The resonator's amplitude is updated at each tick of the clock, i.e. for each input sample, from the resonator's current amplitude value _a_ (in [0,1]), its current position in the oscillation period (waveform value _w_), and the input sample value _s_ (in [0,1]):  
    _a <- (1-k) * a + k * s * w_  

The pattern _v <- (1-k) * v + k * s_, where k is a constant in [0,1] is known as a low-pass filter, as it smoothes out high frequency variations in the input signal. The constant _k_ dictates the "smoothing", in this case the dynamic behaviour of the system, i.e. how quickly it adapts to variations in the input signal.

The contribution of each input sample value to the amplitude comes down to _s * w_, which intuitively will be maximal when peaks in the input signal and peaks in the resonator's waveform are both equally spaced and aligned, i.e. when they have same frequency and are in phase.

**figure**

Note that this is where mathematicians would rather take the signal offline and maybe do a convolution with the waveform as the kernel (or just do an FFT!), but we accept that we don't know the future and we cannot afford to wait for it to become the past, and thus take a more dynamic approach.

In order to account for phase offset, the above calculation is performed for various phases, and the resonator's amplitude is set to the maximum value across all phases. The phase offset resolution is also conveniently the sample duration so the resonator model adds to the oscillator mopdel an array of same length as the resonator's period, where each position stores the amplitude amplitude value for the corresponding phase offset.

The floating-point calculations to carry for each input sample can be performed efficiently on modern GPU architectures. The complexity is linear in the number of phases, i.e. the number of samples in one period, which for low frequencies in the audible spectrum reaches a few thousands.

This means a reasonable implementation on modern hardware should be able to handle these computations per sample relatively easily. But for real-time processing, these computations must typically be carried several tens of thousands of times per second. So while the computations themselves should be cheap, the setup overhead (for example copying data to GPU memory) could become a limiting factor. Especially when running a number of resonators in the context of a music analysis app.

I implemented several versions of this model, all leveraging the Accelerate framework: the first proof of concept uses Swift arrays, a much more efficient version in Swift uses "unsafe pointers", and I also made a C++ version wrapped in an Objective-C++ wrapper to bridge with Swift. The Swift arrays overhead proved significant, so the app features the Swift "unsafe arrays" and the C++ implementations in the exact same setting, so that the computation times can be directly compared. The C++ implementation seems to consistently outperform the Swift implementation - but this should of course be confirmed in a more thorough and systematical approach.

<table align="left" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: left;"><tbody>
<tr><td>Frequency</td><td>Samples / period</td><td>ns / sample</td></tr>
<tr><td>2205Hz</td><td>20</td><td>S: 395<br>C++:210</td></tr>
<tr><td>441Hz</td><td>100</td><td>S: 550<br>C++:350</td></tr>
<tr><td>110.25Hz</td><td>400</td><td>S:990 <br>C++:830</td></tr>
<tr><td>20Hz</td><td>2,114</td><td>S: 1500<br>C++:1200</td></tr>
<tr><td colspan=3 style="text-align: center;">Representative approximate processing time per sample for various frequencies observed on an iPhone 13 mini</td></tr>
</tbody></table>

The code for the oscillator, generator and resonator models featured in the app is available in the open source Swift package [Oscillators](https://github.com/alexandrefrancois/Oscillators).


https://musiclab.chromeexperiments.com/Oscillators/

https://artsandculture.google.com/project/music-makers-and-machines
