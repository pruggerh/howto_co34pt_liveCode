# SuperCollider Addons I'd recommend 

==============

Here is a list of Extensions and Quarks that are crucial to my live performances. If you want to be able to use all of the resources in this repo, you should install them.

## Extensions

Extensions have to be inserted into SuperCollider manually. See [this](http://doc.sccode.org/Guides/UsingExtensions.html) document for more information. Note sc3-plugins have to be compiled on Linux. See the sc3-plugins readme on GitHub for more information.

### [sc3-Plugins](https://github.com/supercollider/sc3-plugins)

'This repository contains the community collection of unit generator plugins for SuperCollider. An installation extends the functionality of SuperCollider by additional UGens that run on scsynth, the SuperCollider audio synthesis server.'

sc3-plugins is a mixed bag of tools, and contains a lot of things I don't use, but it's pretty essential for getting the most out of SuperCollider. Some of the sc3-plugins are fairly scantily-documented, and fall into the 'sounds cool, but no idea what it does or how it works' category.

Particular tools from sc3-plugins I use regularly:

- [Concat](http://doc.sccode.org/Classes/Concat.html) and [Concat2](http://doc.sccode.org/Classes/Concat2.html)
Tools for [concatenative synthesis](https://en.wikipedia.org/wiki/Concatenative_synthesis). Particularly useful when dealing with speech and sampling - I've used them to 'reconstruct' speech using existing samples.

- [Decimator](http://doc.sccode.org/Classes/Decimator.html) and [SmoothDecimator](http://doc.sccode.org/Classes/SmoothDecimator.html)
[Bitcrushing](http://www.musicradar.com/tuition/tech/distortion-saturation-and-bitcrushing-explained-549516) effect Ugens for that classic digital destruction sound. SmoothDecimator has a smoothing option to take some of the digital bite out of the bitcrushing sound.

- [SawDPW](http://doc.sccode.org/Classes/SawDPW.html) (and [PulseDPW](http://doc.sccode.org/Classes/PulseDPW.html))
Alternatives to SuperCollider's native [Saw](http://doc.sccode.org/Classes/Saw.html) and [Pulse](http://doc.sccode.org/Classes/Pulse.html) Ugens, which alias much less, use less CPU and sound an awful lot better especially during additive synthesis. Can also get really wild at unusual frequencies.

- [DFM1](http://doc.sccode.org/Classes/DFM1.html)
A really fantastic sounding digitally-modelled analog filter. Great both as a scuzzy-sounding filter on existing sounds and when pushed into self oscillation to make rich drones. Sounds good both in moderation and absurdity.

- [CrossoverDistortion](http://doc.sccode.org/Classes/CrossoverDistortion.html)
A savage distortion. I don't really have a lot more to say about it.

- [WaveLoss](http://doc.sccode.org/Classes/WaveLoss.html)
An effect for dropping sections of waveforms in either a deterministic or random fashion. Produces a 'degradation' effect from slight dropouts all the way to isolated spluttering.


### [BenoitLib](https://github.com/cappelnord/BenoitLib)

A set of SuperCollider extensions used by Benoît and the Mandelbrots.

The main tool I install this for is Pkr, a pattern proxy for synchronising control rate Ugens inside of patterns, which is a technique I will be covering in this repo. It's a small part of the extension but is totally invaluable for my performances.

There's also some super useful stuff in BenoitLib for collaborative performance which I have used before in a performance with [Shelly Knotts](https://shellyknotts.wordpress.com/), including MandelHub and MandelClock

## Quarks

Quarks can be installed from within SuperCollider, either by installing them manually (`Quarks.install('BatLib')` for example), or using `Quarks.gui` to bring up a gui install them there.

### [Bjorklund Quark](https://github.com/supercollider-quarks/Bjorklund)

The Bjorklund quark implements Euclidean Rhythms, a concept outlined in [this paper](http://cgm.cs.mcgill.ca/~godfried/publications/banff.pdf), involving taking a number of onsets and a number of possible steps, and spaces out the onsets as equally as possible in the given number of steps. A verbal explanation of this doesn't really do it any justice, so I'd encourage you to use [this cool web app](https://reprimande.github.io/euclideansequencer/) which visually and aurally explains what these rhythms are. I've found Euclidean rhythms a great way to program rhythm that is dynamic and interesting, but also sits well within a set of metric dance music. The class I use from this quark is Pbjorklund2, which gives an array of durations for euclidean rhythms.

### [BatLib Quark](https://github.com/supercollider-quarks/BatLib)

BatLib contains StageLimiter, a class that puts a basic [limiter](https://music.tutsplus.com/tutorials/a-beginners-introduction-to-limiters--audio-1071) across all sounds in the SuperCollider server. StageLimiter doesn't really have any effect on the sound the server makes unless you exceed an amplitude of +/- 1 (the top and bottom of the default SuperCollider scope), and when you do push harder than that, you can use it creatively to get 'side-chaining' type effects. I'd recommend always running StageLimiter unless you have a specific reason not to anyway, as an amplitude value that is accidentally out by a factor of ten can be _really_ painful.

### [ddwSnippets Quark](https://github.com/jamshark70/ddwSnippets)

ddwSnippets is a 'Rudimentary snippets facility for ScIDE, implemented in sclang'. I've found [snippets](https://en.wikipedia.org/wiki/Snippet_(programming)) are very useful for any piece of text that will be typed multiple times during a performance, or to lay the groundwork for 'basic' musical patterns without having to write them from scratch (see my comments in 0-2 about SuperCollider's verbosity). I use ddwSnippets to realise musical ideas more quickly when performing, especially using Ugens or patterns that have a lot of arguments, without having to copy-paste from a 'template' file containing the snippets.

==================

sc3-plugins and BenoitLib have to be installed manually.
a note for compiling sc3-plugins on Linux is that my /path/to/scsource is /usr/local/include/SuperCollider, and I would assume that would be a typical path for most users
To install all quarks listed in this document, execute the following in SuperCollider:

```supercollider
(
Quarks.install("Bjorklund");
Quarks.install("BatLib");
Quarks.install("ddwSnippets");
)
```

If you have trouble installing `ddwSnippets`, execute this too:

```supercollider
(
Quarks.install("https://github.com/jamshark70/ddwSnippets.git");
)
```
