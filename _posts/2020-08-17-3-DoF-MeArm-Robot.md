---
title:  "3 DoF MeArm Robot"
mathjax: true
layout: post
categories: media
---

<p style="text-align:center;">
    <img width="608" height="478" src="/img/MeArm/MeArm_robot.png" alt="MeArm robot">
</p>

### Overview

[MeArm](https://mearm.com) is a 3 Dof _open source_ robot arm which has various versions. It is considered as a hobby to learn basic concepts of a robotic arm such as, _kinematics_, _embedded hardware_, _programming_ specially C, _control_, _structure and assembly_, and etc. This robot is similar to [Motoman MPK50](https://www.robots.com/robots/motoman-mpk50) which is particularly used for _pick and place_, _packaging_ and _palletizing_ applications, its special structure and morphology make it able to be more _agile_ and _dexterous_ in comparison to typical RRR robots. This case is designed via CAD softwares like __SOLIDWORKS__ and then cut by laser on wooden sheets. Is includes 3 [plastic gear SG90 servo motors](https://www.tinkermart.in/shop/small-servo-plastic-gear-sg90/), a [Pro Mini 328P Arduino](https://docs.arduino.cc/retired/boards/arduino-pro-mini?queryID=07baba49160a79c79ac8a60ec2d1300c&gl=1*nf7yzt*_ga*MTAzMTY0OTQ0MC4xNjY0MzcxNjg5*_ga_NEXN8H46L5*MTY2NDM3MTY4OS4xLjEuMTY2NDM3MTcxOC4wLjAuMA..)
, a [USB to TTL UART Module](https://www.robofactory.co.za/arduino-modules/158-6pin-cp2102-usb-20-to-ttl-uart-module-6pin-serial-converter.html), a [Breadboard](https://en.wikipedia.org/wiki/Breadboard) and breadboard wires, 5 volt AC DC power supply, and some electornic components. [Joystick Module](https://www.bol.com/nl/nl/p/ps2-joystick-breakout-module-game-controller-voor-arduino-en-raspberry-pi/9300000008325595/?Referrer=ADVNLGOO002013-G-135735704382-S-1678314345586-9300000008325595&gclid=CjwKCAjw4c-ZBhAEEiwAZ105RUMwHQnQxgklasez-0TLup4k1AlCo6KyziLVGZO-M3sZITQ_McglahoC1j0QAvD_BwE) is optional for easier control.

### Project Definition

During `Advanced Robotics` course, as a personal desire, I proposed my [lecturer](https://profile.ut.ac.ir/en/~mudehghani) to implement __Inverse Kinematics__ via _MeArm_. 
1. At first, I had to derive __Forward Kinematics__ of the robot, for this, it is necessary to know (/measure) geometry parameters of _links_, _joints_ and frames, __Denavit-Hartenberg parameters__ ([DH](https://en.wikipedia.org/wiki/Denavit%E2%80%93Hartenberg_parameters)). 
2. 

### Source Code

The source code is uploaded to [MeArm_robot](https://github.com/Hamid-Manouchehri/MeArm_robot) repository on GitHub. Email me if you have question.
