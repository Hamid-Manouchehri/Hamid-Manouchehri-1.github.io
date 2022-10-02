---
title:  "Design and Programming of a Control Panel; Embedded System Design"
mathjax: true
layout: post
categories: media
---

### Overview

[Embedded systems](https://en.wikipedia.org/wiki/Embedded_system) are computer systems with different peripherals to automate a task and control a procedure. _Embedded systems_ are mostly based on [microcontrollers (MCU)](https://en.wikipedia.org/wiki/Microcontroller), programmable electronic devices. In this project, a pre-designed PCB based on [PIC](https://en.wikipedia.org/wiki/PIC_microcontrollers) MCU is provided. The [PCB](https://en.wikipedia.org/wiki/Printed_circuit_board) is a control panel for controlling a _coffee grinder_ machine. There are two approached in embedded system design, this [link](https://www.researchgate.net/figure/Critical-levels-of-abstraction-in-the-Embedded-System-Design-Process-6_fig2_319164367).

<p style="text-align:center;">
    <img width="709" height="588" src="/img/embedded_design/levels_of_abstraction.png" alt="levels of abstraction">
</p>

### Project Definition

There are different [steps](https://resources.pcb.cadence.com/blog/2020-the-steps-for-embedded-systems-design) to design embedded systems:
1. __Analysis of Requirements__: First we evaluated the available _coffee grinder_ machines in the market, and then made a comparison to what exists and what we require. Next we provided the components for our controller panel ([BOM](https://en.wikipedia.org/wiki/Bill_of_materials)). It is also necessary to say we have to direct our design to what we have in the warehouse.
2. __Schematics__: In this stage we have to design the arrangement of pieces of hardware of the system, including input/output preipherals, power supply, indicators, selection of a suitable MCU, and etc. Each electrical component must be drived based on its [datasheet](https://en.wikipedia.org/wiki/Datasheet). For our case the following is the schematic of control panel:

<p style="text-align:center;">
    <img width="987" height="766" src="/img/embedded_design/coffee_grinder_schematic.png" alt="schematic">
</p>

3. __PCB (Printed Circuit Board)__ and __Prototype__: According to the former step, component-level view of the electronic system, now we have to design a circuit board and test it to be free of error.

<p style="text-align:center;">
    <img width="1200" height="576" src="/img/embedded_design/controller_panel.png" alt="panel">
</p>

4. __Firmware Development__: This was my main task to develop a programm for two _PIC16F1829_ MCU. The MCUs are in connection via [USART](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter). In this case, _PIC16F1829_ MCU did not have sufficient pins for our task and we were out of other models of PIC MCUs, so it was decided to deploy two of them. One of them were used for driving 3 digit 7 segments and buzzer, the other one for touch, mechanical keys, and the [timers](https://www.microchip.com/en-us/products/microcontrollers-and-microprocessors/8-bit-mcus/core-independent-and-analog-peripherals/timer-peripheral). <br>
The controller panel consists of 9 touchpads, a buzzer, a mechanical key, a 3 digit 7-segment LED display, and a LED indicator. It has one touchpad for turn on/off the machine (_Power_), one touchpad for starting/stopping the process (_Stop/Start_), a touchpad for changing the digits (_Next_), a touchpad for changing value of selected digit (_Up_), a touchpad for changing the mode of control, _Automatic, Manual, Timer_, (_Mode_), and four of the touchpads (_1-4_) are dedicated to [EEPROM](https://en.wikipedia.org/wiki/EEPROM) to store differet settings/configurations. <br>
The challenging part of developing the firmware was distribution of tasks between the two _MCUs_, and having a continuouse reliable transmission. In addition to that, callibration of sensitivity of touchpad sensors was arduous. <br>
In the following there are some of my [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language)-like diagrams before starting the development of the firmware for this project that could help me to have a better [top-down](https://en.wikipedia.org/wiki/Top-down_and_bottom-up_design) view for designing.

<p style="text-align:center;">
    <img width="1294" height="673" src="/img/embedded_design/UML_images.png" alt="UML">
</p>

5. __Testing and Acceptance__: After the _firmware development_ different tests must be done to validate both functionality of the _firmware_ and the _circuit_. Also some scenarios must be defined for unexpected situations which makes embedded design challenging.

### Video

In the following I will show you the functionality of the controller panel:

<p style="text-align:center;">
   <video width="733" height="294" poster="/img/embedded_design/control_panel_poster.png" controls>
      <source src="/videos/embedded_design/controller_panel.mp4" type="video/mp4">
      Your browser does not support the video tag.
      <p style="text-align:center;">
        <b> <i> Video. 1, Test control panel </i> </b>
      </p>
   </video>
</p>


### Code

The source code (_Firmware_) is on my [GitHub](https://github.com/Hamid-Manouchehri/embedded_control_panel).


