---
layout: post
title:  "SystemJ - frequency relay"
date:   2018-03-17 20:13:00 +1300
categories: [systemj, freq]
---

SystemJ can also be used for various types of application. The frequency relay
is a low-cost system aimed at households that interfaces directly with the
power network to measure current frequency and rate of change of frequency in
real-time and then controls the overall load by switching off or on individual
devices/appliances using triacs (Triode for Alternating Current) connected to a
fuse box that supplies power to the household.

An overview of the frequency relay is show below:

![freq](/images/freq.png)

The system consists of three main modules:

1. Moving averaging filter: The role of this filter is to remove noise in a raw
	 data samples and enables detection of maxima and minima of input waveform.
2. Correlation calculator: This module computes auto-correlation values of the
	 filtered signal at any points of time that indicates symmetrical property of
   the input waveform.
3. Peak detector: This module uses the correlation values received to detect a
	 distance between the maximal and the minimal point of the input waveform at
	 any given time

The main control-flow of the system is written in SystemJ's kernel statements
that describe the system's reactivity and concurrency whereas the signal
analysis part is implemented in Java.

The frequency relay can be simulated on a desktop computer where the modules
run as a simple web-service and consumed via http requests. A simplified view
of the simulated version of the frequency relay is shown below.

![freqarch](/images/freqarch.png)

Below is a screenshot of the frequency relay simulator where sampling
frequency, averaging block size, symmetry block size, waveform equation, and
time duration (seconds) are passed as arguments.
![freqweb](/images/freqweb.png)

The complete implementation of the frequency relay can be found
[here](https://github.com/hjparker/frequency-relay).











