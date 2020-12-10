---
title:  "Tetris hand-held console summary"
categories: "Tetris"
has_children: true
---

# Introduction

[![Click to see the whole album](https://i.imgur.com/9mwxCgN.jpeg)](https://imgur.com/gallery/V4nO59C)

This is a write-up of a class project I am very proud of. In the spring of 2019 three classmates and I set out to build "something interesting" for our final project in our class on embedded systems. We brainstormed some ideas, and quickly settled on Tetris. It's simple, It's fun, and most importantly, It's instantly recognizable. There's no explanation necessary. It's Tetris, you know what to do. 

Our class used a 32-bit ARM micro-controller from STMicroelectronics, and the one requirement of the final project was to use it. Our team divided up the initial tasks, and I got to work finding an appropriate screen to use. I settled on a small LCD screen that used a serial line to communicate with the micro-controller. That screen was a blessing and a curse. It took days of tweaking the driver code to get it to work, but once it did we found it to be reliable and high quality. The serial communication was simple and intuitive, but very slow. It took almost two seconds to update every pixel on the screen. We found ways around that limitation, and in our driver, only the pixel changes were transmitted to the screen. The result was a snappy and responsive game of Tetris. The blocks moved as soon as you pressed the buttons.

The pages below outline some of my favorite design and engineering challenges of the project. I hope that each one contains enough context to be read independently. Nothing would please me more than answering your questions, or taking feedback if things are confusing.
### Watch it in action!
<iframe width="560" height="315" src="https://www.youtube.com/embed/Zn4HCWd0aRU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### [How to store a Tetris board using only 27 words](/tetris/board.html)
In this post I talk about the internal data structure that I developed to represent the Tetris board. I'll talk about some of the benefits and draw-backs of the solution I chose. One main advantage is that the whole board only uses 27 32-bit words!
	
### Rotation == the devil
One day before the project deadline everything worked, except the rotation of the falling blocks! What's Tetris if you can't rotate the blocks!! We got together and spent one long evening in the lab figuring out just what happens when you rotate a falling block. Our solution was slick! It was fast and memory efficient.
		
### It's random, but all the same
We used ```rand()``` from ```stdlib.h``` to generate our sequence of falling blocks. It worked great! But after a few test rounds of Tetris we noticed that something was off... The sequence of blocks were always the same! Our random number generator generates the same sequence every time! I'll discuss this issue and show our solution to this quirk of the library. 
	
### Semaphore signaling
I developed a collection of functions for de-bouncing the user input buttons based on periodic hardware interrupts. When we integrated the input functions with the game loop, we discovered that things felt clunky. There was a delay between pressing a button and a block moving. This post describes how we bridged the gap between the asynchronous user input and the synchronous game loop logic.
	
### The theme song
What's Tetris without the theme song! We wanted to include the classic Tetris musical score with our design. Our microcontroller was not even close to capable of streaming audio. We had kilobytes of space for the entire project. But we did have a PWM hardware peripheral! 
	
### The STM32F051 and the ILI9225
The display I selected for the project was a cheap generic from Amazon. I found an Arduino driver library that provided an API for drawing primitives and displaying text. This post will discuss how I ported the Arduino library to our STM32, and created two layers of C++ abstraction that ultimately provided a simple API that my project partners used to render the game board and menu screens.

### The custom PCB and the case
The custom PCB was the icing on the cake of our project. It elevated the final project from a breadboard monstrosity to a slick and portable experience. One of our project members took ownership of the PCB and did a phenomenal job with the layout. Because of her diligence, version 1 of our PCB was all that was needed.

<!-- ### C++, C, and Assembly all in the same file -->

# Tools
  * C, C++, and ARM Assembly
  * Eclipse IDE
  * Makefiles
  * STM32F051 32bit ARM M0+ micro-controller
  * ILI9225 TFT Display module
