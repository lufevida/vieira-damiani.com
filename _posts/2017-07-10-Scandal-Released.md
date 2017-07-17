---
layout: post
title: Scandal Released
date: 2017-07-10
author: Luis F. Vieira Damiani
tagline: Scandal is an entirely new programming language and framework designed to manipulate sound objects.
image: assets/Scandal/splash.png
category: electroacoustic
---

<span class="image right">![Plectrum]({{ site.baseurl }}/assets/Scandal/splash.png)</span>
Scandal is both a Java framework and a programming language designed to manipulate sounds and make music. It utilizes the [ASM](http://asm.ow2.org) framework for compiling its domain-specific language. Plots are made possible by the [JFreeChart](http://www.jfree.org/jfreechart) and the [JCommon](http://www.jfree.org/jcommon) libraries. Scandal is being developed by [Luis F. Vieira Damiani](http://vieira-damiani.com) under the orientation of [Dr. Beverly Sanders](https://www.cise.ufl.edu/people/faculty/sanders).

### Installation

Go to the [releases](https://github.com/lufevida/Scandal/releases) page on Github and download the `Scandal.zip` file. Open [Sublime Text](https://www.sublimetext.com) and go to

```
Sublime Text -> Preferences -> Browse Packages...
```

Drop the decompressed `Scandal` folder in there. To use the framework alone, import the `Scandal.jar` file using your preferred IDE.

### Printing device and settings information

```
string devices = info
print(devices)
```

### Plotting waveforms

```
array lisa = read("monoLisa.wav", mono)
plot("Lisa", lisa, 2000)
```

### Capturing audio into a buffer and exporting to a file

```
/* start talking... */
array recording = record(3000)
/* stop talking... */
play(recording, mono)
write(recording, "test.wav", mono)
```

### Embedding an array into an audio track

```
array lisa = read("monoLisa.wav", mono)
float amplitude = 0.7
float panorama = -0.3
array vocals = track(lisa, 7, amplitude, panorama)
play(vocals, stereo)
```

### Mixing tracks

```
array lisa = read("monoLisa.wav", mono)
array firstVoice = track(lisa, 1000, 0.7, -0.3)
array secondVoice = track(reverse(lisa), 1441, 0.5, 0.3)
array mixdown = mix(firstVoice, secondVoice)
play(mixdown, stereo)
```

### Adjusting the gain

```
array lisa = read("monoLisa.wav", mono)
lisa = gain(lisa, 0.5)
play(lisa, mono)
```

### Adjusting the panorama

```
array lisa = read("monoLisa.wav", mono)
lisa = pan(lisa, -0.3)
play(lisa, stereo)
```

### Reversing the direction of playback

```
array lisa = read("monoLisa.wav", mono)
lisa = reverse(lisa)
play(lisa, mono)
```

### Changing the speed of playback

```
array lisa = read("monoLisa.wav", mono)
lisa = speed(lisa, 0.7)
play(lisa, mono)
```

### Looping portions of a buffer

```
array lisa = read("monoLisa.wav", mono)
/* Parameters: array, start sample, end sample, count */
lisa = loop(lisa, 0, 4410, 9)
play(lisa, mono)
```

### Splicing buffers together

```
array lisa = read("monoLisa.wav", mono)
array loop1 = loop(lisa, 0, 4000, 8)
array loop2 = loop(lisa, 4000, 8000, 8)
array loop3 = loop(lisa, 8000, 12000, 8)
lisa = splice(loop1, loop2, loop3)
play(lisa, mono)
```

### Creating a delay effect

```
array lisa = read("monoLisa.wav", mono)
/* Parameters: array, milliseconds, feedback, mix */
lisa = delay(lisa, 700, 0.5, 0.5)
play(lisa, mono)
```

### Producing a tremolo effect

```
format channels = mono
array lisa = read("monoLisa.wav", channels)
float depth = 0.9
int frequency = 12
waveform shape = cosine
lisa = tremolo(lisa, depth, frequency, shape)
play(lisa, channels)
```

### Applying a low-pass filter

```
format channels = mono
array lisa = read("monoLisa.wav", channels)
int cutoff = 1000
float resonance = 1.0
filter mode = hipass /* allpass, bandpass, bandstop, lowpass, hipass, lowshelf, hishelf, peaking */
lisa = biquad(lisa, cutoff, resonance, mode)
play(lisa, channels)
```

### Synthesizing classic waveforms

```
int duration = 2000
float amplitude = 0.5
float frequency = 440.0
waveform shape = sawtooth /* cosine, sawtooth, square, triangle, noise */
array saw = oscillator(duration, amplitude, frequency, shape)
play(saw, mono)
```

### Defining automation lines

```
int size = 512
array breakpoints = [2, 1, 3.14, 0, 5]
array envelope = line(size, breakpoints)
plot("A scandalous automation line", envelope, size)
```

### Screenshots

<div class="box alt">
	<div class="row uniform">
		<div class="6u"><span class="image fit"><img src="{{ site.baseurl }}/assets/Scandal/Screenshot.png" alt="" /></span></div>
		<div class="6u"><span class="image fit"><img src="{{ site.baseurl }}/assets/Scandal/Plot.png" alt="" /></span></div>
</div>
