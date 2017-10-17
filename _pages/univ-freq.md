---
layout: page
title: Universe of Frequency
permalink: projects/univ-freq/
subtitle: Universe of Frequency
---

It is an universe controlled by frequency. Every planet will be attracted by a specific frequency. You have to use the corresponding frequencies to attract and absorb the planets. 

This is the homework of MUSIC 256A (CS 476A) at Stanford University.

### Collect All the Planets!

<img width="60%" src="/assets/img/univ-freq/univfreq.png">

To start the game, snap your fingers, the nearer to the microphone the better. Or you can choose to open a can, clap your hands, break a glass, or press 'R' button on your keyboard.

You'll see eight planets appear on the screen. If you want to hear the voice of collisions, press 'I'. It can switch between the collision sound mode and the input voice mode. 

Most of the planets have different colors, which means they will be resonated by different frequencies. When they are resonated, they will also be attracted by the black hole in the middle of the screen. If they stay there too long, they will be absorbed. To generate the frequency, try to yell, sing, whistle, or make some noise to your microphone. If you are tired yelling at it, try to press 'S', 'D', 'F', 'G', 'H', 'J', 'K', and 'L' button on your keyboard.

When you have absorbed all the planets, you can press 'P' and listen to a melody according to the order of planets you absorb.

<img width="60%" src="/assets/img/univ-freq/univfreq2.png">

Here is a brief demo video.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JB88okFcF-o" frameborder="0" allowfullscreen></iframe>

### Technical Issues

- This program is powered by RtAudio, OpenGL, and ChucK, and the code was written in C++.
- The collisions between the planets are elastic collisions, and the gravity of blackhole is created using Newton's law of universal gravitation. (Sorry, there is no gravity between the planets in this world.)
- Since this program will not only read the input voice, but also generate some sounds, I have to deal with the feedback. My approach is to close the output volume of audio input when generating sounds (using envolope in ChucK file), and vice versa.
- In this program, I also have to detect the dominating (or main) frequency of all time. I select the two highest peaks and convert their frequencies into the corresponding pitch notes (C, D, E, F, etc. ). For example, 440Hz and 220Hz will be converted to A, 262Hz and 131Hz will be converted to C. The highest peak will be weighted by 2 units, and the second by 1. Then, in 20 consecutive buffers, if the pitch note with highest value is more than 40 units, it will be chosen as the main frequency.
- The color of the background stars will change according to the main frequency.



