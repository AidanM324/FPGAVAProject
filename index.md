---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---
Aidan Malone - G00423306@atu.ie

Welcome to the FPGA VGA Driver Project, this project aims to outline the step by step process showing the complexities of completing
a simulated personal design working on the Basys3 board, utilising synthesis and implementation to achieve the design.

## **Template VGA Design**
### **Project Set-Up**
Starting with the project set-up we had to first initialise it as an RTL project which enables the addition of source files and contraints, this then allows us to add in our
given VGA.Top.v, VGASync.v, VGAColourCycle.v and Testbench.v files, providing essential code to integrate the use of RBG colour count for our design, the contraints file Basys3_Master.xdc was then added, used to inform the software what physical pins on the FPGA that we plan on connecting, with additional code to to describe the behaviour of the FPGA.
The Project part 'xc7a35tcpg236-1' was selected using Artix-7 to initialise the board being used. 
Set-up Complete!

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/ProjectSummary.png?raw=true">
### **Template Code**
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

The demo of both the Colour Cycle and Colour Stripes template demonstrates both the use of clock cycles and different colour grading techniques that can 
be achieved using the Basys3 board. As seen below.

//png of colour cycle vid an dcolour stripe photo.

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).

During the Design Edit phase, I decided to go for a more complex approach, instead of choosing a static image design I began to brainstorm an idea that involved moving parts.
I was aware that this specific design was tasking to do but  I aimed to test my capabilities in understanding and writing VGA code,
utilizing the template code that was given from both the colour cycle and colour stripe designs, then incorperating the two design choices to create a rotating colour stripe 
image that would rotate each colour in sequential order.

### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.

To adapt the code I used the colour stripe template given by our lecturer which contained the correct sizing and binary of each colour stripe,
this was a good starting point as I could work on adapting the code into multiple different static images, rotating between eachother,

I the  used the CLK counter state loop from the Colour Cycle template code and incorperated
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

This video demonstrates the sequential Colour Stripes video, through the use of the Basys3 Clock counter, moving each colour to the next column through each clock cycle, the design was successful.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/SourcesView.png?raw=true">
