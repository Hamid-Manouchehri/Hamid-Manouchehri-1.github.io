---
title:  "Development and Simulation of Bimanual Object Manipulation, Using UR5 Manipulators; M.Sc. Dissertation"
mathjax: true
layout: post
categories: media
---

### Abstract

Manipulating an object or in more general terms, the ability of the robot to interact with its environment, for modification and enhancing that, is
called "__manipulation__". This has usually been done by an [articulated](https://en.wikipedia.org/wiki/Articulated_robot) robot equipped with a gripper. Within this research, the manipulation will be done by occupation of two articulated robotic arms, while after holding the object, the set of two robotic arms and the object make a closed dynamic chain. The most significant aspect of optimal bi-manual manipulation against manipulation with only one articulated robotic arm is, __having a better and more efficient control on manipulation__. In this method, bi-manual manipulation of the object acquires dynamic models of both arms and the object. Also, in typical methods of object manipulation, it is common to measure or estimate contact forces by sensors. Due to the intrinsic complexity of the whole system dynamics, measurement of the constraint generalized forces in the contacts of object and arms needs high precision sensors and periodic calibration, also force-torque sensors have limited range, steady state error and include noise. So it is desirable to __calculate__ them in the __absence of force-torque sensors__. Analytical calculation of the inverse dynamics for a closed-chain robotic system in the absence of force-torque sensors in wrist is not easy to implement, because of the constraint term in the equation of the motion. Thanks to a method called “__Orthogonal Decomposition__”, the aforementioned problem is handled, though. In addition, by designing the null-space of the task, we would be able to control the squeeze and motion terms of forces for manipulation. What we want to develop in this research is according to the previous researches, but in a physics-based simulation environment, Gazebo, via two [UR5](https://www.universal-robots.com/products/ur5-robot/) robot manipulators under some __oiptimizations__ for constraints and trajectory planning in [quaternion](https://en.wikipedia.org/wiki/Quaternion) space.

<p style="text-align:center;">
    <img width="728" height="512" src="/img/12dof_bimanual_manipulation/bimanual_ur5.png" alt="bimanual setup">
</p>

### Introduction, Problem Statement

We have simulated manipulation (translational and orientational displacement) of an object by a dual arm robot, in this case; two UR5 manipulators. Simulation is done via __Gazebo__ (v9) and __ROS__ (Robot Operating System, Melodic); and for dynamic and kinematic calculations we leveraged [RBDL](https://rbdl.github.io/index.html). There are two controllers used in this research for manipulation, 1. inverse dynamics, 2. constrained QP (Quadratic Programming). According to the proposed inverse dynamics method, it is feasible to calculate contact (end-effector to object) force and torque in the absence of force-torque sensors, and for validation of the results, we compared it with the data measured by sensors placed in the wrist of manipulators. In addition, to avoid singularity and other limitations of Euler's rules for orientation planning of the object, we used quaternion math for this purpose.

### Architecture of Algorithm

In this section, a brief description of different parts of the algorithm is shown through diagrams.

<p style="text-align:center;">
    <img width="1196" height="560" src="/img/12dof_bimanual_manipulation/architecture.png" alt="algorithm architecture">
</p>



