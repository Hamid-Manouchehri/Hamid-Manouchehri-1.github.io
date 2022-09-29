---
title:  "Pip Inspection Robot; Design and Simulation in Solidworks"
mathjax: true
layout: post
categories: media
---

<p style="text-align:center;">
    <img width="442" height="359" src="/img/pip_inspection_robot/pip_inspection_robot.png" alt="Pip-Inspection robot">
</p>

### Overview

During the course of `Mechatronics 1`, our [lecturer](https://profile.ut.ac.ir/en/~hrhadi/courses) asked us to design and implement a mechanism for a __pip inspection mobile robot__ to make it able to traverse a vertical path inside a pip of certain diameter, between 4.2" and 5". For that purpose I chose [__scissors mechanism__](https://en.wikipedia.org/wiki/Scissors_mechanism), equiped with a [caster](https://en.wikipedia.org/wiki/Caster) wheel. The original _CAD model_ of the _scissors mechanism_ was taken from [grabcad](https://grabcad.com/library). It will be mounted on the top of a four wheel mobile robot (the total structure was designed from the scratch in Solidworks) and actuates (expands) whenever the robot wants to go through a vertical path. The mechanism would generate proper friction for wheels to prevent slipping. The primary purpose of choosing this mechanism is _simplicity_, besides _efficiency_. Robot is equiped with 4 DC (per each wheel) and 1 servo (for scissors mechanism) motors, there are also two springs of cylindrical shape in the front and rear of the chassé as passive DoFs. The bottom of the chassé consists of two separate plates to make the wheels in both side have complete contact to the curved pip.

<p style="text-align:center;">
    <img width="1310" height="383" src="/img/pip_inspection_robot/detailed_views.png" alt="detailed view">
</p>

To calculate desired normal force for travesing the vertical pip without slipping, I used the static friction force equation. Assuming the whole robot weighs 5 kg:

### Project Definition

As I mentioned above, firstly I designed the CAD model of the chassé with all details, then mount the modified _scissors mechanism_ on it. The power of the servo motor is transmited via a verical _shaft_ to the _lead screw_ of the _scissors mechanism_.

<p style="text-align:center;">
    <img width="708" height="460" src="/img/pip_inspection_robot/power_transmission.png" alt="power transmission">
</p>

To calculate the required normal force for the tyres to traverse the vertical pip without slipping, I used static [friction](https://en.wikipedia.org/wiki/Friction) equation. Assume the whoel robot weighs 5 $$kg$$:

<p style="text-align:center;">
    <img width="424" height="357" src="/img/pip_inspection_robot/normal_forces.png" alt="normal forces">
</p>

<p style="text-align:center;">
    <img src="https://latex.codecogs.com/svg.image?F_{max}=\mu&space;N;&space;\mathbf{(1)}" title="maximum static friction" />
</p>

<p style="text-align:center;">
    <img src="https://latex.codecogs.com/svg.image?N_{caster}=166.7&space;(N)" title="" />
</p>
    
<!-- <p style="text-align:center;">
   <video width="320" height="240" poster="/img/project_img.png" controls>
      <source src="/videos/DOFs.mp4" type="video/mp4">
      Your browser does not support the video tag.
   </video>
</p> -->
