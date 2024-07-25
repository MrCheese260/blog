---
layout: post
title: Building a Video Card on FPGA!
tags: 
- Electronics
- FPGA
- Verilog
- Video_Card
description: Harnessing the power of FPGA to create a video card from scratch.
---
## Mentees:
-- [Sarvesh Ganu](https://github.com/MrCheese260)
-- [Suchit Garad](https://github.com/IamLegend509)

### What is this project about?
This project focuses on building a Video Card relaying analog messages (such as for a CRT display) on a Field programmable gate array (FPGA).The project requires fundamental knowledge of FPGA boards, CRT monitors’ working and electronic logic gates.
### Starting with FPGA programming
For the starting of FPGA programming the first task was to select the programming languages which were VHDL and Verilog. VHDL is the older language and follows a more complex structure. Whereas Verilog is comparatively newer and concise like C-like languages. 
So, for getting started with Verilog we started learning it by solving Verilog problem from HdLbits website. These problems started easy with programming simple logic gates, modules and getting to know the basis of Verilog programming language. This was followed by intermediate problems based on multiplexers and Sequential circuits such as D-flip-flops and Finite state machines (FSMs).
By completing the course, we had learned the Verilog Syntax and Finite state machines working. The previous problem solving developed due to having prior knowledge of other programming languages like C/C++, Java and Python helped in learning the language faster. 
### How VGA works
VGA stands for Visual Graphics Array and it is a way to send visual information from a computer's video card to a monitor. VGA connectors are typically blue and have 15 pins arranged in three rows.  This connector transmits the video signals from the computer to the monitor. Most of the pins used in the VGA are ground pins, but the pins we are most concerned with are the RGB pins(3 separate pins for Red green and blue colours)as well the horizontal and vertical sync pins.Thes RGB pins carry analog signals that provide information for the intensity of red, green, and blue components of the image. By varying the voltage of each signal, different colors can be produced.The H_sync and V_sync signals synchronize the timing of the image data. H_sync signals the end of a line and the start of a new one, while V_sync signals the end of a frame and the beginning of a new one.

![Diagram_of_VGA_connector](/assets/posts/Video_card_on_FPGA/1678689924-2249-BhAkyv.png)

                               
### Learning working of CRT displays
The CRT displays works on a simple yet very fast procedure of displaying images using an electron gun pointed at a phosphorescent screen which goes on printing horizontal as well as vertical lines by using different voltages for different colours. The electron gun works on the principle of thermionic emission.Electrons are emitted from the heated cathode within the electron gun. These electrons are then accelerated by an accelerating anode.he deflection system, controlled by the display's circuitry, steers the electron beam. The beam moves from left to right and top to bottom, line by line, refreshing the entire screen many times per second. This movement of the electron gun will be controlled by the H_sync and V_sync signals coming from the VGA.
H sync and V_sync 
In the third week of our project, we started working on the H_sync and V_sync signals. Both these signals can be divided into 4 specific interval timings :the Visible area, Front porch, sync pulse and back porch. The Visible Area is the period during which the actual image data is displayed on the screen. It is the active portion where pixels are lit up to form the picture. Front Porch is a short interval after the visible area and before the sync pulse. It provides time for the electron beam (in CRTs) or the scanning process (in LCDs) to prepare for the sync pulse. Sync pulse is the part of the signal that resets the position of the beam or scans to the start of the next line (horizontal sync) or frame (vertical sync). It is essential for keeping the display in sync with the input signal.Last but not the least is the Back porch which follows the sync pulse and precedes the next visible area. It allows time for the display system to stabilize before drawing the next line or frame.We have decided to use a 800 * 600 VGA signals in our project and we have been able to output the above interval timings correctly on a Digital Signal Oscilloscope using the Arty A7 35 FPGA.

![CRT_monitor](assets/posts/Video_card_on_FPGA/CRT-2.png)
                 
### What we are working on now
We have completed writing H_sync and V_sync signals script as well as tested the timings and waveforms on a Oscilloscope.
We are currently working on adjusting the intensity of RGB signals using resistors and writing the code for the same.

### Problems we faced
The initial problems involved the understanding of finite state machines and how their working varied from simple logical statements. Since the hardware implications can sometimes vary from the software results or our thinking process.Testing the timings of the Sync pulses also was a significant problem due to improper readings appearing on the Oscilloscope due to presence of jumper wires which are unreliable sometimes

