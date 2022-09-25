---
title:  "6 DoF Bi-manual Manipulation"
mathjax: true
layout: post
categories: media
---

As a part of my master's thesis, for implementing the inverse dynamics algorithm to an upper-body bi-manual robot base on my supervisor [paper](https://www.researchgate.net/publication/320330613_Inverse_Dynamics_Control_of_Bimanual_Object_Manipulation_Using_Orthogonal_Decomposition_An_Analytic_Approach) in a 3D simulator, I had to work with __Gazebo__. First the [URDF](http://wiki.ros.org/urdf) model of the robot was prepared by the help of my teammate, Ms [Nooshin Kohli](https://github.com/nooshin-kohli), then other dependencies like torque controllers of joints, launch file, and etc attached, finally of courese the script of algorithm was written by a great deal of work. Actually the fundaments of algorithm for a 2D simulation was obtained beforehand by my supervisor and I developed it to 3D simulation in Gazebo.

<p style="text-align:center;">
  <img style="text-align:center;" width="755" height="199" src="/img/6dof_bimanual_manipulation/fig_123.png" alt="Logo">
</p>

Although the control approach is dynamic cancellation, It was cumbersome to adjust joints' `damping` and `friction` in URDF model.

<p style="text-align:center;">
  <img style="text-align:center;" width="651" height="269" src="/img/6dof_bimanual_manipulation/control_system_caption.png" alt="Logo">  
</p>

First the desired trajectory of the object (green box) is calculated, a triangular path in this case. After that, regrading dynamic equations of robot and object are derived in joint space, it is necessary to determine desired joint position, velocity and acceleration.
What is notable in this method is that, the effect of force and torque of object in hands' contacts (end-effectors) of robot, removes by a projector, obtained from __orthogonal decomposition__ of a specially defined jacobian. Therefore the total dynamics equation becomes free from the effect of the object, so it is possible to specify inverse dynamics of arms analytically.

<img src="https://latex.codecogs.com/svg.image?\hat{M}\ddot{q}&plus;\hat{h}=S^{T}\tau=S^{T}\tau&space;&plus;&space;J_{g}^{T}\lambda_{a};\mathbf{(1)}&space;" title="no title" /> <br>
<img src="https://latex.codecogs.com/svg.image?P(\hat{M}\ddot{q}&plus;\hat{h})=PS^{T}\tau;&space;\mathbf{(2)}" title="no title" />





