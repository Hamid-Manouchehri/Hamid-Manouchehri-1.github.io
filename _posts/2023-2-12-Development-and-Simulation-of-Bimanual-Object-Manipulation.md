---
title:  "Development and Simulation of Bimanual Object Manipulation, Using UR5 Manipulators; M.Sc. Dissertation"
mathjax: true
layout: post
categories: media
---

### Abstract

Manipulating an object or in more general terms, the ability of the robot to interact with its environment, for modification and enhancing that, is
called "__manipulation__". This has usually been done by an [articulated](https://en.wikipedia.org/wiki/Articulated_robot) robot equipped with a gripper. Within this research, the manipulation will be done by occupation of two articulated robotic arms, while after holding the object, the set of two robotic arms and the object make a closed dynamic chain. <br>
The most significant aspect of optimal bi-manual manipulation against manipulation with only one articulated robotic arm is, __having a better and more efficient control on manipulation__. In this method, bi-manual manipulation of the object acquires dynamic models of both arms and the object. Also, in typical methods of object manipulation, it is common to measure or estimate contact forces by sensors. Due to the intrinsic complexity of the whole system dynamics, measurement of the constraint generalized forces in the contacts of object and arms needs high precision sensors and periodic calibration, also force-torque sensors have limited range, steady state error and include noise. So it is desirable to __calculate__ them in the __absence of force-torque sensors__. <br>
Analytical calculation of the inverse dynamics for a closed-chain robotic system in the absence of force-torque sensors in wrist is not easy to implement, because of the constraint term in the equation of the motion. Thanks to a method called “__Orthogonal Decomposition__”, the aforementioned problem is handled, though. In addition, by designing the null-space of the task, we would be able to control the squeeze and motion terms of forces for manipulation. What we want to develop in this research is according to the previous researches, but in a physics-based simulation environment, Gazebo, via two [UR5](https://www.universal-robots.com/products/ur5-robot/) robot manipulators under some __oiptimizations__ for constraints and trajectory planning in [quaternion](https://en.wikipedia.org/wiki/Quaternion) space.

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

As you see in Fig.2; first, we have prepared a [URDF](http://wiki.ros.org/urdf) model of UR5 manipulator. Here, it was just some modifications on the predefined validated model of the UR5. Second, the control algorithm is implemented as a ROS node. Third, the desired trajectory for the object in 3D would be interpolated for certain initial and final states of object. Forth, the algorithm receives states of the robot (joint position and velocity) from Gazebo and then calculates the desired torque for tracking desired trajectory of the manipulated object in Cartesian space iteratively. Also, the control loop of the algorithms is shown in the blue block.

### Theory

In the following the fundamental formulations related to the modeling, control and calculation of torque would be presented.

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?M(q)\ddot{q}&space;&plus;&space;h(q,&space;\dot{q})&space;=&space;S^T\tau&space;&plus;&space;J^T(q)\lambda;&space;(1)" title="bimanual robot dynamic equation" />
</p>


<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?M_o(q)\dot{v_o}&space;&plus;&space;h_o(z_o,&space;v_o)&space;=&space;-G_o^T(z_o)\lambda;&space;(2)" title="object dynamic equation" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?G_{oi}(z_o)&space;=&space;\begin{bmatrix}&space;I&space;&&space;p_{o/i}\times&space;\\&space;0&space;&&space;I&space;\\\end{bmatrix},&space;G_{oi}(z_o)&space;\in&space;\mathbb{R}^{k&space;\times&space;k},&space;i&space;=&space;\{a,b\}&space;;&space;(3)" title="grasp matrix" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?v_o&space;=&space;G_{oa}^{-1}J_a\dot{q}&space;=&space;G_{ob}^{-1}J_b\dot{q};&space;(4)" title="kinematic constraint equation" />
</p>


<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?(J_a&space;-&space;G_{oa}G_{ob}^{-1}J_b)\dot{q}&space;=&space;0;&space;(5)" title="kinematic constraint equation" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?J_g\dot{q}&space;=&space;0,&space;J_g&space;\in&space;\mathbb{R}^{k&space;\times&space;n};&space;(6)" title="kinematic constraint equation" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?\hat{M}\ddot{q}&space;&plus;&space;\hat{h}&space;=&space;S^T\tau&space;&plus;&space;J_g^T\lambda_a;&space;(7)&space;" title="bimanual robot and object dynamic equation" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?\hat{M}&space;=&space;M&space;&plus;&space;J_b^TG_{ob}^{-T}M_oG_{ob}^{-1}J_b;&space;(8)&space;" title="inertial matrix of whole system" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?\hat{h}&space;=&space;h&space;&plus;&space;J_b^TG_{ob}^{-T}(h_o&space;&plus;&space;M_oG_{ob}^{-1}(\dot{J_b}&space;-&space;\dot{G}_{ob}G_{ob}^{-1}J_b)\dot{q});&space;(9)&space;" title="centrifugal and coriolis forces" />
</p>

As you see, we could derive the whole dynamics equation of bimanual robot and object in (7) by merging bimanual robot dynamic (1) and object dynamic (2) equations via the defined __Grasp Matrix__ (3). 'k' is the number of constraints per each end-effector and 'n' is bimanual robot degrees of freedom. The jacobian matirix in (6) is called __Grasp Jacobian__. <br>
Now, lets calculate the inverse dynamics solution by "QR" decomposition of transposed grasp jacobian:

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?J_g^T&space;=&space;\hat{Q}[\hat{R}^T&space;0]^T;&space;(10)" title="QR decomposition of grasp jacobian" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?P_{QR}&space;=&space;\hat{S}_u&space;\hat{Q}^T,&space;\hat{S}_u&space;=&space;[0_{(n-k)&space;\times&space;k}&space;I_{n-k}];&space;(11)" title="kinematic projector" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?P(\hat{M}\ddot{q}&space;&plus;&space;\hat{h})&space;=&space;PS^T\tau;&space;(12)" title="unconstrained dynamic" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?\tau(W,&space;\tau_0)&space;=&space;(PS^T)^{\sharp}P(\hat{M}\ddot{q}_{des}&space;&plus;&space;\hat{h})&space;&plus;&space;(I&space;-&space;(PS^T)^{\sharp}PS^T)W^{-1}\tau_0;&space;(13)" title="inverse dynamics equation of bimanual robot" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?(PS^T)^{\sharp}&space;\overset{\underset{\mathrm{def}}{}}{=}&space;W^{-\frac{1}{2}}(PS^TW^{-\frac{1}{2}})^&plus;;&space;(14)" title="W-weighted generalized inverse" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?\lambda_a&space;=&space;\hat{R}^{-1}\hat{S}_c\hat{Q}^T(\hat{M}\ddot{q}_{des}&space;&plus;&space;\hat{h}&space;-&space;S^T\tau),&space;\hat{S}_c&space;=&space;[I_k&space;0_{k&space;\times&space;(n-k)}];&space;(15)" title="constrained (external) froce-torque" />
</p>

By pre-multiplying (11) by (7), we are able to break the dynamic equation (7) into a constrained and unconstrained (12) equations; now, the inverse dynamics would be calculated by (13), and by substituting the calculated torque into (7), we can compute the constrained force-torque analytically (15). <br>

To compute the required torque, it is necessary to feed the desired joint acceleration:

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?\ddot{q}_{des}&space;=&space;\begin{bmatrix}&space;J_g&space;\\&space;G_{ob}^{-1}J_b\end{bmatrix}^&plus;(\begin{bmatrix}&space;0&space;\\&space;a\end{bmatrix}&space;-&space;\begin{bmatrix}&space;\dot{J}_g&space;\\&space;G_{ob}^{-1}(\dot{J}_b&space;-&space;\dot{G}_{ob}G_{ob}^{-1}J_b)\end{bmatrix}\dot{q});&space;(16)" title="desired joint acceleration" />
</p>

<p style="text-align:left;">
  <img src="https://latex.codecogs.com/svg.image?a&space;=&space;\dot{v}_{o,des}&space;&plus;&space;k_{da}(v_{o,des}&space;-&space;v_o)&space;&plus;&space;k_{pa}(z_{o,des}&space;-&space;z_o);&space;(17)" title="generalized acceleration of object in cartesian space" />
</p>

### Trajectory Planning

To plan the desired translational and orientational trajectory for the object, we used __quintic__ polynomial interpolation. For translational trajectory, it is straight forward to calculate, and for orientational trajectory in quaternion space, it is the same method presented in [this]() paper. <br>

In the following, manipulation is done for different trajectory scenarios:

<p style="text-align:center;">
<!--    <video width="523" height="302" poster="/img/pip_inspection_robot/simulation_poster.png" controls> -->
      <source src="/videos/MSc_dissertation/whole_scenario_*4.mp4" type="video/3gp">
      Your browser does not support the video tag.
      <p style="text-align:center;">
        <b> <i> Video. 1, Bimanual manipulation, Gazebo </i> </b>
      </p>
   </video>
</p>


<!-- <p style="text-align:left;">
  <img src="" title="" />
</p> -->







