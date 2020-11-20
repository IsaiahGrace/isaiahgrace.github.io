---
layout: page
title:  "MIPS CPU summary"
categories: mips-cpu
---

## Overview

This is a summary of my class project for Purdue's Computer Architecture class. Over the course of the class I worked with another student to cooperatively design a MIPS based CPU. We completed a single-stage processor core in the first four weeks, and then spent the remainder of the course implementing several optimizations present in high performance CPU cores.

## Tools

  * SystemVerilog
  * Makefile
  * Mentor Graphics ModelSim
  * Altera FPGA

## Instruction Set

## Register File verilog code:

{% highlight verilog %}
module register_file (input logic CLK, 
		      input logic nRST, 
		      register_file_if.rf rfif
		      );

   
   word_t [WORD_W-1:0] registers;
   word_t [WORD_W-1:0] nxt_registers;

   // Outputs are always active
   assign rfif.rdat1 = registers[rfif.rsel1];
   assign rfif.rdat2 = registers[rfif.rsel2]; 

   always_ff@(negedge CLK, negedge nRST) begin
      if (nRST == 1'b0) begin
	 registers <= '0;
      end
      else begin
	 registers <= nxt_registers;
      end
   end
   
   always_comb begin
      nxt_registers = registers; // default case
      if (rfif.WEN == 1'b1) begin
	 nxt_registers[rfif.wsel] = rfif.wdat;
      end
      nxt_registers[5'd0] = '0; // 0 is constant value
   end
endmodule // register_file{% endhighlight %}
