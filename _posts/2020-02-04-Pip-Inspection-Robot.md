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

During the course of `Mechatronics 1`, our [lecturer](https://profile.ut.ac.ir/en/~hrhadi/courses) asked us to design and implement a mechanism for a __pip inspection mobile robot__ to make it able to traverse a vertical path inside a pip of certain diameter, between 4.2" and 5". For that purpose I chose [__scissors mechanism__](https://en.wikipedia.org/wiki/Scissors_mechanism), equiped with a wheel, the original _CAD model_ was taken from [grabcad](https://grabcad.com/library). It will be mounted on the top of a four wheel mobile robot (the total structure was designed from the scratch in Solidworks) and actuates (expands) whenever the robot wants to go through a vertical path. The mechanism would generate proper friction for wheels to prevent slipping. The primary purpose of choosing this mechanism is _simplicity_, besides _efficiency_. Robot is equiped with 4 DC (per eahc wheel) and 1 servo (for scissors mechanism) motors, there are also two springs of cylindrical shape in the front and rear of the chasse' as passive DoFs. The bottom of the chasse' consists of two separate plates to make the wheels in both side have complete contact to the curved pip.

<p style="text-align:center;">
   <video width="320" height="240" poster="/img/project_img.png" controls>
      <source src="/videos/DOFs.mp4" type="video/mp4">
      Your browser does not support the video tag.
   </video>
</p>
