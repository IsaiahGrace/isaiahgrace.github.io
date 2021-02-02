---
title:  "Musical-lights system"
categories: musical-lights
has_children: false
nav_order: 4
---

# Introduction

Page under construction
{: .label .label-yellow }

TODO: Write an introduction to the project and explain the goals

project goal:
* Use individually addressable LEDs to create unobtrusive mood lighting for my room based on the current song playing on my Spotify account.


![Musical-lights-top-level](../media/Musical-lights-top-level.png)

### The LEDs custom protocol *(coming soon)*
I'm using the very common individually addressable IIIIII LEDs. There are great libraries for Arduino and Raspberry Pi controllers. The LEDs themselves only need one signal for data transfer, and because of this, the timings matter quite a bit and convey information. In this post I'll go though the confusing data-sheet and explain the communication protocol, as well as describe the libraries that I use to interface with the LEDs.

### Converting music to color *(coming soon)*
I'm only using one parameter from the Spotify API to determine the color of my lights. This becomes a math problem because I am trying to map a one dimensional input space (song *mood*) to a three dimensional output space (red green blue). There are trade-offs that must be made and tweaks we can make so that the output is reasonable.

### Managing the Finite State Machine *(coming soon)*
I'm using a finite state machine to model the functionality of the desktop server software. This has many advantages compared to my first draft which was little more than an enormous ```while(True):``` loop. I've decided to use 

### The Raspberry Pi client *(coming soon)*
While the Raspberry Pi zero is activly controlling the two LED segments, the Python processes use about 40% of the processing power available. I wanted to reduce the CPU loads while staying inside the python ecosystem, so I implemented some optimizations that can place the Python scripts into an idle state. This reduces the system load to less then 1% when no music is playing on my desktop. I'll also go through my use of a Python scheduling library.

### The QMK keyboard client *(coming soon)*
Almost a year after I started this project, I bought a new keyboard that has individually addressable LEDs under each key, and runs an open source firmware! My first thought was: Musical lights! In this post I'll walk thought the C code I wrote and integrated into the QMK ecosystem to control the LEDs on my keyboard.

# Tools
  * Raspberry Pi zero W
  * Planck EZ GLOW (STM32F303 microcontroller)
  * QMK keyboard firmware
  * Systemd
  * Python
  * C
