---
title:  "Design and Manufacturing of a Pneumatic Procedure; Bachelor Project"
mathjax: true
layout: post
categories: media
---

<p style="text-align:center;">
    <img width="839" height="741" src="/img/pneumatic_table/pneumatic_table_whole_setup.png" alt="laboratory prenumatic table">
</p>

### Overview

My _B.Sc._ thesis was design and manufacturing of a [__pneumatic__](https://en.wikipedia.org/wiki/Pneumatics) table for illustrating some concepts of pneumatic applications for __instrumentation laboratory__ with my teammate, _Eng. Yadollah Alinaghi Naini_ under supervision of Dr. [Mohsen Shafieirad](https://faculty.kashanu.ac.ir/mshafieirad/en). _Pneumatic_ systems are widely used in industry due to its `safty and cleanliness`, `simplicity of design and control`, and `reliability` over hydraulic and electrical systems. On the other hand, these systems sometimes do not have enough `accuracy`, and due to _compressibility of air_, it is harder to control, besides _pneumatic systems_ are the _loudest_ type of designs. <br>
This project was defined in a way to illustrate different structures and sensors for measurement of air pressure and how pneumatic (/electro-pneumatic) actuators work through different _test scenarios_. Firstly, we _desinged and simulated_ the scanarios by [FluidSIM](https://www.festo.com/in/en/e/technical-education/digital-learning/virtual-simulation-and-modelling-id_31275/) software. Then draw a _schematic_ (/map) for placement of pneumatic facilities. After that, we did _actuator sizing_ to provide suitable pneumatic equipments for the scenarios.

<p style="text-align:center;">
    <img width="888" height="766" src="/img/pneumatic_table/pneumatic_schematic.png" alt="laboratory prenumatic table">
</p>

### Familiarity with Equipments

According to _Fig. 1_:
1. Panel for activation of the _test scenarios_
2. _2 Position 5 Way Soleniod Valve_, directional control valve
3. _Two Finger Double Action Pneumatic Gripper_, parallel gripping type, actuates via _#5_
4. _Magnetic Linear Slide (Actuator)_
5. _3 Position 5 Way Flow Control Valve_, hand lever operated
6. _Pneumatic Cylinder_
7. _Air Filter and Pressure Regulator Gauge_
8. _Pneumatic Cylinder_, equipped with magnetic proximity sensor
9. Main _Air Distribution Valve_, connects to the compressor
10. _T Shape Hose Tube Connector_
11. _Pneumatic Shut-off Valve_
12. _Differential Pressure Transmitter_ (DPL/DP-cell)

In addition to the _Differential Pressure Transmitter_, we had [mercury pressure gauge (manometer)](https://en.wikipedia.org/wiki/Mercury_pressure_gauge) and _piezoresistive transducer_ ([MPX5100DP](https://www.nxp.com/part/MPX5100DP#/)) to measure different types of pressures, including _absolute pressure_ (relative to a perfect reference _vacuum_), _gauge pressure_ (relative to _ambient atmospheric_ pressure), and _differential pressure_. For _MXP5100DP_, we designed our _PCB_ based on its datasheet in the laboratory. The _DPL_ is used for measurement of _differential pressure_, MXP5100DP for measurement of _differential pressure_ and _absolute pressure_, and _mercurry gauge_ for measurement of _gauge pressure _ and _absolute pressure_ if one side of tube is sealed.

<p style="text-align:center;">
    <img width="827" height="725" src="/img/pneumatic_table/pressure_gauge.png" alt="MPX5100DP and mercurry pressure gauge">
</p>

### Project Definition

The table is devided into two parts; the below part of the table is for _pneumatic actuators_ and the upper part of it is for _pneumatic pressure measurement_ equipments. 6 scenarios are defined for _pneumatic pressure measurement_:
1. __gauge pressure__ of _regulator gauge #1_ (_R1_) via _DP-cell_
2. __gauge pressure__ of _R1_ via _manometer_
3. __gauge pressure__ of _R1_ via _DP-cell_ and _manometer_
4. __differential pressure__ of _R1_ and _R2_ via _DP-cell_
5. __differential pressure__ of _R1_ and _R2_ via _manometer_
6. __differential pressure__ of _R1_ and _R2_ via _DP-cell_ and _manometer_

<p style="text-align:center;">
    <img width="731" height="321" src="/img/pneumatic_table/activation_table.png" alt="activation table">
</p>

To avoid the _mercury_, splashed out of the tube, in abrupt mistakes, we designed a volume along the tube of _manometer_ that is capable of collecting the _mercury_ when it overflows.

### Video

My teammate would illustrate how to activate actuators and how to measure the _gauge pressure_ via _DP-cell_:

<iframe src="https://vimeo.com/755876282" width="500" height="375" frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen=""></iframe>


