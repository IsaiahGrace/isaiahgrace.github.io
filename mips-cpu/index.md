---
title:  "MIPS CPU"
has_children: true
has_toc: false
---

## Overview

**TODO: flesh out this page more, provide an outline of the rest of the pages, and provide some context** 

This is a summary of my class project for Purdue's Computer Architecture class. Over the course of the class I worked with another student to cooperatively design a MIPS based CPU. We completed a single-stage processor core in the first four weeks, and then spent the remainder of the course implementing several optimizations present in high performance CPU cores.

## Tools

  * SystemVerilog
  * Makefile
  * Mentor Graphics ModelSim
  * Altera FPGA


## Pages

These pages build on one another and are meant to be read in order. The first few will take a look at some of the simpler hardware modules, and then I will explain a little about the verification process. Once I've gone through the basic modules of the CPU, I'll discuss and describe some of the optimizations we performed on our designs to increase performance. I'll talk about how we created a dual-core processor, the performance enhancements that brings, and the design challenges it entails. Finally I'll talk about some of the weaknesses of this particular design, and how I would change things If I wanted to develop a *real* dual-core CPU.

  * [The Instruction Set](isa.html)
  * [The ALU](alu.html)
  * [The Register File](reg.html)
