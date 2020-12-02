---
#layout: page
title:  "Tetris hand-held console summary"
categories: tetris
has_children: true
---

# Overview

This is a write-up of a class project I am very proud of. In the spring of 2019 three classmates and I set out to build "something interesting" for our final project in our class on embedded systems. We brainstormed some ideas, and quickly settled on Tetris. It's simple, It's fun, and most importantly, It's instantly recognizable. There's no explanation necessary. It's Tetris, you know what to do. 

Our class used a 32-bit ARM micro-controller from STMicroelectronics, and the one requirement of the final project was to use it. Our team divided up the initial tasks, and I got to work finding an appropriate screen to use. I settled on a small LCD screen that used a serial line to communicate with the micro-controller. That screen was a blessing and a curse. It took days of tweaking the driver code to get it to work, but once it did we found it to be reliable and high quality. The serial communication was simple and intuitive, but very slow. It took almost two seconds to update every pixel on the screen. We found ways around that limitation, and in our driver, only the pixel changes were transmitted to the screen. The result was a snappy and responsive game of Tetris. The blocks moved as soon as you pressed the buttons.

The pages below outline some of my favorite design and engineering challenges of the project. I hope that each one contains enough context to be read independently. Nothing would please me more than answering your questions, or taking feedback if things are confusing.



# Tools
  * C, C++, and ARM Assembly
  * Eclipse IDE
  * Makefiles
  * STM32F051 32bit ARM M0+ micro-controller
  * ILI9225 TFT Display module

# Pages

## Planned
  * How to store a tetris board using only 27 words
  * Rotation == the devil
  * C++, C, and Assembly all in the same file
  * It's random, but all the same
  * Semaphore signaling
  * The theme song
  * The STM32F051 and the ILI9225
  * The custom PCB and the case
