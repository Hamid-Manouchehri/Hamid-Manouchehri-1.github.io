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
1. _Analysis of Requirements_
2. _Schematics_
3. _PCB_ (Printed Circuit Board)
4. _Prototype_
5. _Firmware Development_
6. _Testing and Acceptance_

1. First we evaluated the available _coffee grinder_ machines in the market, and then made a comparison to what exists and what we require. Next we provided the components for our controller panel ([BOM](https://en.wikipedia.org/wiki/Bill_of_materials)). It is also necessary to say we have to direct our design to what we have in the warehouse.
2. In this stage we have to design the arrangement of pieces of hardware of the system, including input/output preipherals, power supply, indicators, selection of a suitable MCU, and etc. Each electrical component must be drived based on its [datasheet](https://en.wikipedia.org/wiki/Datasheet). For our case the following is the schematic of control panel:

<p style="text-align:center;">
    <img width="608" height="478" src="/img/embedded_design/coffee_grinder_schematics.png" alt="schematic">
</p>
