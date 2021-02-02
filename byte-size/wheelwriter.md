---
title:  "IBM Wheelwriter30"
parent: "Byte-size projects"
categories: "Byte-size"
nav_order: 1
---

# Introduction
My friend and I bought an IBM Wheelwriter30 on a whim from the Purdue surplus store almost two years ago. We had vague ideas of refurbishing it, or at the very least taking the keyboard off and turning it into a USB keyboard using an Arduino. But, like so many other pipe dreams, the typewriter languished in my basement until I graduated and had to move out of my college house. I threw away the bulky typewriter machine but kept the keyboard. It had only two flexible printed circuit connectors, a manufacturing date of 1989 printed on the back, and absolutely no documentation.

**TODO: add image of the front and back of the keyboard**

# Reverse engineer the matrix
This isn't quite as challenging or as flashy as the section header might imply! What we want to do here is make sense of the two headers coming out of the keyboard so that we can program a micro-controller to understand the keyboard layout. The way engineers build a keyboard without having to make a wire for each key is to create a matrix (or grid) and detect key-presses based on their unique row & column combination. The creators of the QMK firmware wrote a good explanation, check it out [here](https://docs.qmk.fm/#/how_a_matrix_works). So, based on the two headers coming out of the board we have a 14x8 matrix, or maybe that's 8x14? I didn't know how to orient the grid at first, but that's okay. Labelling the deminsions rows and columns is arbitrary, and if the layout is sensible, it should be easy to tell which way is up once we know where things go. I used a multimeter to test for continuity and a spreadsheet to record my findings. Below is the keyboard matrix laid bare. There are some strange keys, but most are familiar!

**TODO: add image of the matrix spreadsheet**


# Translate the matrix into a keymap for QMK
The QMK firmware is impressivly configurable, and there are some frameworks we can use to help us translate the hardware key matrix into a sensible keymap that we can assign semantic meaning.

# Select the pins for the hardware matrix

# Plan out the physical construction and PCB

# Solder, test, debug repeat!
