---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---
Aidan Malone - G00423306@atu.ie

Welcome to the FPGA VGA Driver Project, this project aims to outline the step by step process showing the complexities of completing
a simulated personal design working on the Basys3 board, utilizing synthesis and implementation to achieve the design.

## **Template VGA Design**
### **Project Set-Up**
Starting with the project set-up we had to first initialise it as an RTL project which enables the addition of source files and contraints, this then allows us to add in our
given VGA.Top.v, VGASync.v, VGAColourCycle.v and Testbench.v files, providing essential code to integrate the use of RBG colour count for our design, the contraints file Basys3_Master.xdc was then added, used to inform the software what physical pins on the FPGA that we plan on connecting, with additional code to to describe the behaviour of the FPGA.
The Project part 'xc7a35tcpg236-1' was selected using Artix-7 to initialise the board being used. 
Set-up Complete!

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/ProjectSummary.png?raw=true">
### **Template Code**

VGA is an analog video interface that transmits Red, Green, and Blue (RGB) color signals, along with horizontal and vertical sync signals, to a display. It uses a 15-pin connector for signal transmission and supports various resolutions and refresh rates. The analog nature of VGA can cause image quality degradation over long cables or high resolutions.


The Verilog code templates that were provided were of great use in getting us set up. 
VGA.Top.v was used to initialize the colours, columns, rows and clock counters needed for design output. The template code for colour cycle and colour stripe was then called in to VGA.Top.v as a function, including the attributes needed to work within the function such as colours, clock, columns and rows, all to allow the selected design output to work efficiently.

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/VGATop.png?raw=true">

**Colour Cycle:**

The Colour Cycle template code was used to demonstrate the capabilities of interchanging colour images through the use of a state loop that interchanges through each clock cycle, a binary colour is set within each state enabling the change. This should perform a clear distinct colour change through each clock pulse.

**Colour Stripes:**

The Colour Stripes template code was used to demonstrate the ability of using different colours within a singular static image. The use of columns and rows and be interchanged to the desired colour output by using if else statements to select the pixel range of each column and what colour they will produce.


### **Simulation**

The simulation process for the FPGA VGA Driver project involves creating a testbench in Verilog to model the behavior of the VGA driver before actual hardware implementation. In this phase, you write a simulation file that mimics the signals and timing that the VGA output will generate, such as horizontal and vertical sync pulses, pixel data, and control signals. Tools like Vivado Simulator are used to run the simulation, allowing you to verify functionality, debug, and refine the design.

Key details to consider during simulation include ensuring proper timing of the VGA signals, accurate pixel generation, and the correct mapping of color data to the VGA format. The simulation must match the timing constraints required for the Basys3 FPGA and VGA display, and any errors identified during simulation can be corrected before synthesis, saving time and resources in the hardware implementation phase.

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/counter_n-tick-waveform.webp?raw=true">

### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.

The synthesis process in the FPGA VGA Driver project involves translating the Verilog code into a netlist of logic gates that can be mapped onto the FPGA hardware. This step checks for syntax errors, optimizes the design, and ensures that the logic will fit within the available resources on the Basys3 board. After synthesis, the implementation phase takes place, where the netlist is physically mapped to the FPGA’s architecture, including the placement and routing of the logic elements.

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/ZoomedOutSynthSchematic.png?raw=true">
 

During implementation, the FPGA toolchain ensures that all timing constraints are met, and the design will operate correctly at the intended clock speed. The implementation process also generates a bitstream file, which is used to configure the FPGA to perform the VGA driver functionality. If any issues arise (e.g. timing violations), adjustments are made before finalizing the design.

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/ColourCycleSynthesisDesign.png?raw=true">

### **Demonstration**

The demo of both the Colour Cycle and Colour Stripes template demonstrates both the use of clock cycles and different colour grading techniques that can 
be achieved using the Basys3 board. As seen below.

**Colour Cycle**

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/ColourCycle.gif?raw=true">

**Colour Stripes**

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/ColourStripes.jpeg?raw=true">

## **My VGA Design Edit**

During the Design Edit phase, I decided to go for a more complex approach, instead of choosing a static image design I began to brainstorm an idea that involved moving parts.
I was aware that this specific design was tasking to do but  I aimed to test my capabilities in understanding and writing VGA code,
utilizing the template code that was given from both the colour cycle and colour stripe designs, then incorperating the two design choices to create a rotating colour stripe 
image that would rotate each colour in sequential order.

### **Code Adaptation**

To adapt the code I used the colour stripe template given by our lecturer which contained the correct sizing and binary of each colour stripe,
this was a good starting point as I could work on adapting the code into multiple different static images, rotating between eachother,

I then used the CLK counter state loop from the Colour Cycle template code and incorperated it with the binary if else statements of the Colour Stripe code to allow the interchanging static images of the binary colour columns. 
Following this, I then changed the binary colours, moving each colour column by 1 in each state to create a moving track design through the use of the clock counter cycle.

### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.

Through viewing the Behavoural Clock Simulation, it is validating to see that the Clock Cycle [clk] and the Column Counter [col 10:0] are in sync with eachother, showing that the design is functioning as promised.

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/BehaviouralSim-CLK.png?raw=true">

### **Synthesis**

The Synthesis output shows the optimized logic gates and resources required to implement the VGA driver, while the implementation output includes placement and routing information, ensuring that all signals meet timing constraints. The bitstream file generated can then be used to program the FPGA.
 
The Synthesis and Implementation outputs for my design showed a massive increase in the number of statements and counters,
the original design had to be updated to optimize resource allocation. These adjustments ensure the design works correctly within the available FPGA resources. this can be seen in the Synthesis schematic produced for my design, this increase is due to the transition of my colour stripe image which requires more resources to produce the VGA design.

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/SynthesisSchematic.png?raw=true">

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/ZoomedInSynthesisSchematic.png?raw=true">

### **Demonstration**

This video demonstrates the sequential Colour Stripes video, through the use of the Basys3 Clock counter, moving each colour to the next column through each clock cycle, the design was successful.

<img src="https://github.com/AidanM324/FPGAVAProject/blob/main/docs/assets/images/ColourStripeRotation.gif?raw=true">


**References**

FPGA Coding : [https://fpgacoding.com/].

System-on-Chip Design and Verification (module slides) "Michelle Lynch".

Driving a VGA Monitor : [https://embeddedthoughts.com/].

Github : [GitHub Help](https://help.github.com/).

