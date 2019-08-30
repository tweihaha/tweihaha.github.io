---
layout: page
title: Guitar Solo Transcription
permalink: research/solo-transcription/
subtitle: Guitar Solo Transcription on Real-world Recordings
---

*September, 2018*

This is part of the [SoloLa project](https://musicai.citi.sinica.edu.tw/project/SoloLa){:target="_blank"}, which aims at creating a complete system for transcribing guitar solo from audio signal to accurate symbolic notation, and this subproject designed the core algorithm of it. Instead of playing each note separately, guitar solo usually contains lots of inter-note playing techniques, e.g., bend, vibrato, slide. The employment of these playing techniques makes it difficult to transcribe notes using general note tracking algorithms, which only analyze the fundamental frequency of the audio signal but not the precise variation of frequency through time. However, these variations are possible locations for the playing techniques. By analyzing the playing techniques, we have proved to get more detailed symbolic notation (sheet music) for guitarists as well as improving the accuracy of note tracking.

To accomplish this goal, we introduced a new model called Technique-Embedded Note Tracking, or TENT, primarily designed for transcribing guitar solo. The whole algorithm is explained in [our journal paper](https://transactions.ismir.net/articles/10.5334/tismir.23){:target="_blank"}. Here we only show the flowchart and some demo of the algorithm.


### Flowchart

<img src="/assets/img/solo-transcription/System_overview.png">

### Demo

Example 1: 
<audio controls controlsList="nodownload">
  <source src="/assets/audio/solo-transcription/examples/lick_7.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>

<img src="/assets/img/solo-transcription/lick_7.png">


Example 2: 
<audio controls controlsList="nodownload">
  <source src="/assets/audio/solo-transcription/examples/lick_25.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>

<img src="/assets/img/solo-transcription/lick_25.png">


Example 3: 
<audio controls controlsList="nodownload">
  <source src="/assets/audio/solo-transcription/examples/lick_73.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>

<img src="/assets/img/solo-transcription/lick_73.png">

Example 4: 
<audio controls controlsList="nodownload">
  <source src="/assets/audio/solo-transcription/examples/lick_27.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>

<img src="/assets/img/solo-transcription/lick_27.png">


Example 5: 
<audio controls controlsList="nodownload">
  <source src="/assets/audio/solo-transcription/examples/lick_15.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>

<img src="/assets/img/solo-transcription/lick_15.png">


Example 6: 
<audio controls controlsList="nodownload">
  <source src="/assets/audio/solo-transcription/examples/lick_38.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>

<img src="/assets/img/solo-transcription/lick_38.png">

