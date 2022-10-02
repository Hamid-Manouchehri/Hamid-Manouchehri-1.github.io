---
title:  "Design and Programming of a Control Panel; Embedded System Design"
mathjax: true
layout: post
categories: media
---

### Overview

[Embedded systems](https://en.wikipedia.org/wiki/Embedded_system) are computer systems with different peripherals to automate a task and control a procedure. _Embedded systems_ are mostly based on [microcontrollers (MCU)](https://en.wikipedia.org/wiki/Microcontroller), programmable electronic devices. In this project, a pre-designed PCB based on [PIC](https://en.wikipedia.org/wiki/PIC_microcontrollers) MCU is provided. The [PCB](https://en.wikipedia.org/wiki/Printed_circuit_board) is a control panel for manipulating a _coffee grinder_ machine.

### Project Definition

There are different [steps](https://resources.pcb.cadence.com/blog/2020-the-steps-for-embedded-systems-design) to design embedded systems:
1. __Analysis of Requirements__: First we evaluated the available _coffee grinder_ machines in the market, and then made a comparison to what exists and what we require. Next we provided the components for our controller panel ([BOM](https://en.wikipedia.org/wiki/Bill_of_materials)). It is also necessary to say we have to direct our design to what we have in the warehouse.
2. __Schematics__: In this stage we have to design the arrangement of pieces of hardware of the system, including input/output preipherals, power supply, indicators, selection of a suitable MCU, and etc. Each electrical component must be drived based on its [datasheet](https://en.wikipedia.org/wiki/Datasheet). For our case the following is the schematic of control panel:

<p style="text-align:center;">
    <img width="981" height="682" src="/img/embedded_design/coffee_grinder_schematic.png" alt="schematic">
</p>

3. __PCB (Printed Circuit Board)__ and __Prototype__: According to the former step, component-level view of the electronic system, now we have to design a circuit board and test it to be free of error.

<p style="text-align:center;">
    <img width="1140" height="498" src="/img/embedded_design/controller_panel.png" alt="panel">
</p>

4. __Firmware Development__: This was my main task to develop a programm for two _PIC16F1829_ MCU. The MCUs are in connection via [USART](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter). In this case, _PIC16F1829_ MCU did not have sufficient pins for our task and we were out of other models of PIC MCUs, so it was decided to deploy two of them. One of them were used for driving 7-segments and buzzer, the other one for touch and mechanical keys. <br>
The controller panel consists of 9 touchpads, a buzzer, a mechanical key, a 3 digit 7-segment LED display, and a LED indicator.

5. __Testing and Acceptance__: After the _firmware development_ different tests must be done to validate both functionality of the _firmware_ and the _circuit_. Also some scenarios must be defined for unexpected situations which makes embedded design challenging.

In the following I will show you the functionality of the controller panel:

<!-- <p style="text-align:center;">
   <video width="523" height="302" poster="/img/pip_inspection_robot/simulation_poster.png" controls>
      <source src="/videos/embedded_design/controller_panel.mp4" type="video/mp4">
      Your browser does not support the video tag.
      <p style="text-align:center;">
        <b> <i> Video. 1, Test control panel </i> </b>
      </p>
   </video>
</p> -->


### Code

The source code (_Firmware_) is on my [GitHub](https://github.com/Hamid-Manouchehri/embedded_control_panel).


