---
layout: page
title: Time and Perception in Music and Computation
---

_This is an excerpt from the chapter "Time and Perception in Music and Computation," which appears in the book [New Computational Paradigms for Computer Music](https://www.editions-delatour.com/gb/science-of-music/1426-new-computational-paradigms-for-computer-music-9782752100542.html), G. Assayag and A. Gerzso Eds., Editions Delatour France / IRCAM, 2009, pp. 125-146.  
Some of the references have been updated._


The Oxford English Dictionary deﬁnes music as “the art or science of combining vocal or instrumental sounds to produce beauty of form, harmony, melody, rhythm, expressive content, etc.” Composers and performers of music invent and produce sounds, carefully organized with the intent and purpose to trigger emotional responses from the listeners, usually humans. Creating music therefore involves deep understanding and mastery, whether intuitive of explicit, of the human auditory perceptual and cognitive apparatus.

A reﬂexion on the nature of the phenomena involved points towards the ability of the mind to move in and out of ﬂows of time, real or imaginary, as a defining feature of perceptual and cognitive activities. A comprehensive computational paradigm for computer music must afford the modeling of this ability.


## Middle World

[Richard Dawkins](http://richarddawkins.net/) remarks that brains have evolved to help animals survive within the orders of magnitude of size and speed at which their bodies operate. He calls Middle World (MW) this relatively narrow range of phenomena directly and intuitively accessible to perceptual and cognitive processes [[6](#ref-6)]. Dawkins invokes the human brain’s evolutionary entanglement with MW to explain humans' difficulty in grasping, and coping with, the physical realities of the universe outside of its familiar conﬁnes, from the sub-atomic scales of quantum physics to the universe-size scales of relativity.  But the fundamental properties of MW can also help characterize the nature of the tasks at which brains came to excel, in particular the fundamentally dynamic nature of these tasks.

Everything in MW is subject to what the human brain perceives and understands as time, “the continuum of experience in which events pass from the future through the present to the past” ([Wordnet](http://wordnet.princeton.edu/)). MW time (MWT) cannot be altered in any way: in particular, its ﬂow cannot be slowed, stopped or reversed. The implications are deep. First, nothing in MW can ever happen again, every and any experience is that of an ever changing environment, by an ever changing observer. Exact reproduction of an experience, such as a musical performance, is a practical impossibility both for the performer and for the listener. Second, mathematical abstractions, such as randomness, synchrony, or inﬁnity, do not exist in MW (David Cope discusses randomness in [[5](#ref-5)]). Mathematics deﬁne an idealized world of spatio-temporal invariants, which in some respects models aspects of MW, and aspects of the universe outside of MW that are difficult for MW-evolved brains to grasp.

Mathematics provide a framework for MW brains to characterize and manipulate invariants in a way that is consistent, completely and absolutely predictable, independent of time and space; in particular, these invariants are not sub ject to, and allow the abstraction of, the ﬂow of MWT. The theory of computation came about to formalize actions and operations in the mathematical world, where they must abide by the principles of consistency, predictability, universality. This requires not only that the notion of time be abstracted, but also that the resulting abstract manifestation of time in computing be enforced as a strong invariant. The mathematical properties of computation, especially the abstraction and immutable crystallization of the ﬂow of time, constitute major obstacles to the useful computational modeling of many important MW phenomena.

## The Brain in Middle World

Even though perpetual contingency characterizes MW, the underlying dynamics are not random. On the contrary, their complexity thinly veils a rich variety of spatio-temporal patterns [[19](#ref-19)]. The term pattern, here, denotes “a regular and intelligible form or sequence discernible in certain actions or situations; esp. one on which the prediction of successive or future events may be based” (Oxford English Dictionary). Under such conditions, the brain has evolved into a highly effective spatio-temporal pattern detection and prediction system [[11](#ref-11)]. Moreover, the brain exhibits an “infovorous” behavior [[2](#ref-2)]: it craves for new experiences. More specifically, studies have linked sensory novelty and surprise to pleasure and reward activity in the brain. This is consistent with the continuous reﬁnement of the prediction system through acquisition of new knowledge.

Both the creation and performance of music play directly into these fundamental brain mechanisms [[13](#ref-13)], taking advantage of the pleasure systems wired in the brain. From rhythmic patterns to more intangible tonality systems, the brain naturally picks-up, processes, and responds to, spatio-temporal structures in music. If too predictable, a piece of music or a performance are simply boring; on the other hand, the listener might not be able to make sense of a piece or a performance that is "too" unexpected. The art of creating music, or any other artifact intended to stimulate human interest, hinges on striking a delicate balance between familiarity and surprise; establishing a frame of anticipation, and venturing outside of this frame in such a way that prompts the listener to adapt her own frame of reference.

These observations point to a highly dynamic notion of music making and listening. If the musical expertise, and expectations, of brains change every time they experience music, then what constitutes interesting music and interesting performance changes constantly, both at the individual and at the cultural levels. The computational modeling of such concepts as musical appreciation must therefore characterize how context, both individual and collective, plays out in the dynamics of the particular perceptual and cognitive processes involved.


## Time and Perception

Scales of time in MW play a crucial role in the recognition and interpretation of temporal patterns, by the brain, as symbolic relationships such as causality and synchrony.

Events that are perceived as shortly following each other in time tend to be interpreted in a causality relationship. Brains learn the range of latencies that may separate an action and the perception of its effect in MW. The quantitative characterization of acceptable latencies is crucial to the understanding of interaction. Human-computer interaction researchers [[14](#ref-14)][[3](#ref-3)] categorize acceptable time delays into three orders of magnitude, which coincide with Newell’s cognitive band in his time scale of human actions [[15](#ref-15)]: the 0.1s (100ms) scale characterizes perceptual processing, perceived instantaneous reaction; the 1s scale characterizes immediate response, continuous ﬂow of thought (consistent with the notion of psychological present [[7](#ref-7)]); and, the 10s scale characterizes unit tasks, continued and sustained attention. These orders of magnitude define relatively narrow ranges of applicability for different levels of cognitive activities, especially when compared with the longer time order ranges that characterize other activities in MW: the rational band (100-10000s, i.e. minutes to hours), the social band (100000-10000000s, i.e. days to months) and the historical band (100000000-10000000000s, i.e. years to millenia).

Ensemble musical performance requires both interaction and synchronization. Synchrony, deﬁned as the exact co-occurrence of several observations, is a perceptual abstraction. The different, and ﬁnite, speeds at which light and sound travel imply that events whose percepts occur in absolute synchrony would hardly ever have occurred synchronously in MW, or would never have occurred naturally at all. For example, explosions in movies usually occur as if sound and light traveled at the same speed in the air. In MW, sound travels quite slowly, about 33cm in 1ms, whereas light travels so fast that travel times are negligible. Events that do occur simultaneously cause in an observer a variety of percepts that are not received synchronously, but that exhibit speciﬁc - and predictable - temporal patterns, which brains learn to understand as signs of a common cause, and thus synchronous origin in MWT. This is especially relevant in music making (and enjoying), due to the relatively low speed of sound travel in air.

Fraisse offers a comprehensive analysis of psychophysical experiments that aim to characterize the perceptual limits of time properties: event succession and duration [[7](#ref-7)]. Exact numbers depend on many factors, including task modality, and stimulus type, intensity, and duration. Pierce places the time resolution of the ear on the order of 1ms [[16](#ref-16)], which leads him to question whether human’s acute time resolution is actually of any use in music. Certainly the brain perceives as simultaneous auditory events that the ear detects as distinct. Pierce cites, among others, an experiment by Rasch, which revealed that synchronization in performed small ensemble music is only accurate to 30-50ms [[18](#ref-18)]. Incidentally, this range also characterizes the travel time of sound between the opposite end of an orchestral stage. Each individual musician in the orchestra experiences the performance in a necessarily speciﬁc and unique way. Yet the musicians are collectively capable, under the direction of the conductor, of producing an expert and consistent ensemble rendering of a musical piece. Experiments by Chew et al. [[4](#ref-4)] on sound latency in ensemble performance have shown that, under favorable conditions, professional musicians can deliver a meaningful musical performance while experiencing delays as high as 65ms. This number recalls the experimental fact, also reported by Pierce, that humans perceive no echo when a strong reﬂected sound occurs within 60-70ms after the direct sound.

These experimental results illustrate the impressive plasticity of brain processes with respect to the perception of MWT. Abstract temporal concepts, such as synchrony, bear limited relevance to the modeling of the MW perceptual and cognitive phenomena that inspired their invention.

## Time and the Brain

If the ﬂow of MWT is immutable, the human brain hardly perceives it as such. Gooddy, in his book _Time and the Nervous System_ [[10](#ref-10)], distinguishes between Personal Time (PT) and Government Time (GT). The former marks the ﬂow of time (MWT) as perceived by the individual brain; the latter refers to the passage of time as measured by a collectively recognized reference clock, from the brain’s perspective an external synchronization device to MWT. Alteration in the perception of time, of the ﬂow of one’s PT, occur within the perceiving agent’s mind.

Fraisse emphasizes the necessity to separate the perception of duration, which takes place in the psychological present, and the estimation of duration which “takes place when memory is used either to associate a moment in the past with a moment in the present or to link two past event” [[7](#ref-7)]. Memory frees the mind from the continuous, irreversible ﬂow of MWT. The mind can manipulate memories, events taken out of MWT, and place them in ﬂows of time, that extend in the past and future (including the ﬂow of MWT). Gooddy captures this ability in his observation that “the \[human\] brain is the place or mechanism or medium by which time is converted into space and space into time.”

Musical tasks constantly engage the ability of the brain to move information in and out of the ﬂows of times (going back and forth between time and space): memorizing a piece of music, performing it from memory, writing a piece of music as a score, performing a piece of music from a score. A musical notation system affords spatial representation of the perception of time through music; a performance is the re-creation of this perception from its spatial representation. The goal of a music notation system that effectively supports total communication between the composer and the performer remains elusive. Technology relatively recently afforded exact recording and recreation of performances. But a recording only captures one single, permanently frozen, physical manifestation of the musical material, with no place for re-creation or re-interpretation. The recording is super-naturally faithful to the performance, but does not explicitly encode, nor allows the full recovery of, the full depth of intent of the source material. Furthermore, the exactness of the reproduction is not necessarily a signiﬁcant, or desirable, feature from the listener’s point of view. The human brain is approximate; memory is event-based and selective. Each experience, each performance are different, and bring the prospect of renewed excitement to the listening brain. Successive re-experiences of a recording only remain interesting to a listener as long as she herself keeps changing from the experience.

Considerations about the nature and meaning of notation extend to the performing arts, such as dance and theater, and beyond. The thinking brain in MW ﬁnds itself in a constant struggle between the desire to stop time and the necessity to live (and experience) in the present. Bamberger has studied extensively the evolution of the spatialization (notation) of temporal patterns (rhythms) during child development. She reﬂects [[1](#ref-1)]:

> We necessarily experience the world in and through time. How and why, then, do we step off these temporal action paths to selectively and purposefully interrupt, stop, and contain the natural passage of continuous actions/events?  
> How do we transform the elusiveness of actions that take place continuously through time, into representations that hold still to be looked at and upon which to reﬂect?  
> Perhaps the very notion of complexity lies in engaging the resilient paradoxes that emerge when we confront the implications of our static, discrete symbolic conventions with our immediate experience of always “going on.”

The ability to control the ﬂow of one’s PT allows the brain to take temporal experiences out of the immutable ﬂow of MWT, contemplate or otherwise manipulate these experiences outside of MWT, and later re-create them in the ﬂow of MWT. This ability enables individuals to adapt, learn, generalize, create. Without it, symbolic thought would be impossible, or at least completely detached from, and therefore irrelevant to, life in MW.

## Time in Computation

The notion of computation was explicitly created for use outside of the ﬂow of MWT.  Models of computation provide primitives for describing processes in a purely timeless context (computability), or in an artiﬁcial and abstract ﬂow of time marked by computational operations (algorithmic complexity). The resulting abstract manifestation of time in computing is enforced as a strong invariant, universally and implicitly relied upon.

This state of affairs has serious implications for the design and use of computing artifacts in MW. Music exists at the conﬂuence of creation, representation and performance, where inherent limitations of time representations in computation become evident. Music systems fall into two broad categories: online or real-time systems, and off-line system. The signiﬁcance of these categories in the context of interaction is explored in [[8](#ref-8)]. Henkjan Honing more speciﬁcally analyses and classiﬁes the issues related to the representation of time in music computing [[12](#ref-12)].

Process-oriented systems, which address real-time needs such as sound synthesis or performance (sequencing), adopt either tacit or implicit representations of time. Tacit representations restrict the notion of time to the “now,” the ﬂow of MWT. Implicit representations tie the ﬂow of time in the system to that of MWT in a direct, ﬁxed and inescapable relation. For example, the Max paradigm in its various forms, e.g. [Max/MSP](http://www.cycling74.com/) and [Pure Data](http://puredata.info/), embraces this approach. Composition and editing systems, on the other hand, manipulate static representations of music, with explicit modeling of time relationships in their mathematical abstraction, outside of any ﬂow of time. [OpenMusic](http://recherche.ircam.fr/equipes/repmus/OpenMusic/) is a representative member of this category. The dataﬂow model of OpenMusic maps to the functional programming model, and does not provide for the creation and manipulation of a ﬂow of time in relation to MWT.

These orthogonal representations of time, and the computational models they support, serve their particular needs well. However, the dichotomy they introduce with respect to time representations seems irreversible. Puckette for example denounces the divide between processing and representation paradigms as a major obstacle to creating a comprehensive system for music making [[17](#ref-17)]. Musical improvisation requires a seamless blend of composition (representation) and real-time performance (processing), the ability to move freely in and out of ﬂows of PT and MWT. The design of a real-time interactive musical improvisation system, such as the multimodal interactive improvisation system [MIMI](http://mimi-improv.blogspot.com), requires to bridge the representation/processing gap. Past efforts in this area have leveraged existing programming models to produce ad hoc solutions; MIMI beneﬁts from the use of a new computational paradigm that offers a general solution.

## The Hermes/dl design language

Hermes/dl [[9](#ref-9)] adopts an asynchronous concurrent computation model. Its data model distinguishes volatile data, in a ﬂow of time, from persistent data outside of any ﬂow of time. As a result, the language primitives afford the modeling of concurrent ﬂows of time and computation, and of processes that take information in and out of these ﬂows.

Arrangements of language primitives consistently associated with speciﬁc functionalities or behavior constitute patterns of the language; they can be used as models or guides for system design. The patterns of primitives and interactions that characterize the transfer of information from a ﬂow of time into persistent form constitute instances of the Aggregator pattern. The patterns of primitives and their interactions that characterize the transfer of information from persistent form into a speciﬁc ﬂow of time constitute instances of the Sampler pattern. The next section introduces the Hermes/dl design language in the wider context of the motivations that lead to its creation.


## References

[<a id="ref-1">1</a>] Jeanne Bamberger. Evolving meanings: Revisiting Luria and Vygotsky. In G. O. Mazur, editor, _Thirty Year Commemoration to the Life of A. R. Luria_. Semenenko Foundation, New York, 2008.

[<a id="ref-2">2</a>] I. Biederman and E. A. Vessel. Perceptual pleasure and the brain. _American Scientist_, 94:249–255, 2006.

[<a id="ref-3">3</a>] Stuart K. Card, George G. Robertson, and Jock D. Mackinlay. The information visualizer, an information workspace. In _Proceedings of the SIGCHI Conference on Human Factors in Computing Systems (CHI)_, pages 181–186, 1991.

[<a id="ref-4">4</a>] E. Chew, A.A. Sawchuk, R. Zimmermann, V. Stoyanova, I. Tosheff, C. Kyriakakis, C. Papadopoulos, A.R.J. Francois, and A. Volk. Distributed Immersive Performance. In _Proceedings of the 2004 Annual NASM Meeting_, San Diego, CA, USA, November 2004.

[<a id="ref-5">5</a>] David Cope. _Computer Models of Musical Creativity_. MIT Press, 2005.<br />

[<a id="ref-6">6</a>] Richard Dawkins. _The God Delusion_. Houghton Mifflin Harcourt, 2006.  See also Dawkins' [TED](http://www.ted.com/) Talk: [Why the Universe Seems So Strange](https://www.ted.com/talks/richard_dawkins_why_the_universe_seems_so_strange).

[<a id="ref-7">7</a>] Paul Fraisse. Perception and estimation of time. _Annual Review of Psychology_, 35:1–36, 1984.

[<a id="ref-8">8</a>] Alexandre R.J. François and Elaine Chew. An architectural framework for interactive music systems. In _Proceedings of the International Conference on New Interfaces for Musical Expression_, Paris, France, June 2006.

[<a id="ref-9">9</a>] Alexandre R.J. François, "An Architectural Framework for the Design, Analysis and Implementation of Interactive Systems," [_The Computer Journal_](https://academic.oup.com/comjnl) (2011), vol. 54, no. 7, pp. 1188-1204. doi: [10.1093/comjnl/bxq081](https://doi.org/10.1093/comjnl/bxq081). First published online November 10, 2010.

[<a id="ref-10">10</a>] William Gooddy. _Time and the Nervous System_. Praeger Pub, 1988.

[<a id="ref-11">11</a>] Jeff Hawkins and Sandra Blakeslee. _On Intelligence_. Times Books, 2004.

[<a id="ref-12">12</a>] Henkjan Honing. Issues in the representation of time and structure in music. _Contemporary Music Review_, 9:221–239, 1993.

[<a id="ref-13">13</a>] David Huron. _Sweet Anticipation: Music and the Psychology of Expectation_. MIT Press, 2006.

[<a id="ref-14">14</a>] Robert B. Miller. Response time in man-computer conversational transactions. In _Proceedings of the AFIPS Fall Joint Computer Conference_, volume 33, pages 267–277, 1968.

[<a id="ref-15">15</a>] Allen Newell._Uniﬁed Theories of Cognition_. Harvard University Press, 1990.

[<a id="ref-16">16</a>] John R. Pierce. The nature of musical sound. In Diana Deutsch, editor, _The Psychology of Music, Second Edition (Cognition and Perception)_, pages 1–24. Academic Press, 1998.

[<a id="ref-17">17</a>] Miller S. Puckette. A divide between ‘compositional’ and ‘performative’ aspects of Pd. In _Proceedings of the First International Pd Convention_, Graz, Austria, 2004.

[<a id="ref-18">18</a>] R. A. Rasch. Synchronization in performed ensemble music. _Acustica_, 43:121–131, 1979.

[<a id="ref-19">19</a>] Ken Richardson. _A Mind for Structure: Exploring the Roots of Intelligent Systems_. Brown Walker Press, 2006.
