---
title:  "Simulation; Nonlinear Control of an Inverted Pendulum by Partial Feedback Linearization"
mathjax: true
layout: post
categories: media
---

within the course of __Nonlinear Control__, I was intended to simulate the result of [this paper](https://ieeexplore.ieee.org/document/1435497), __"Velocity and Position Control of a Wheeled Inverted Pendulum by Partial Feedback Linearization"__, via _MATLAB_. Considering the inverted pendulum is an _underactuated system_, it is demanding to control such a _nonlinear_ underactuated system, because there are less controllabe states than total states of the system.

<p style="text-align:center;">
  <img style="text-align:center;" width="341" height="296" src="/img/sim_wheeled_inverted_pendulum/inverted_pendulum.png" alt="inverted pendulum model">
</p>

As we know that __Feedback Linearization__ is a technique for transforming the main system to a simpler form, in this case, first we derive the dynamic equations of the system, next we _partially feedback linearize_ the system, Finally apply the controller.

### Dynamic Model
<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?M&space;(&space;q&space;)&space;\ddot{q}&space;&plus;&space;V&space;(&space;q&space;,&space;q&space;_&space;)&space;=&space;E&space;(&space;q&space;)\tau&space;&space;&plus;&space;A^T&space;(&space;q&space;)&space;\lambda;&space;\mathbf{(1)}" title=" dynamic equation of wheeled inverted pendulum" />  
</p>

Eliminate _Lagrange multipliers_ $\lambda$ with $S^{T}$:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?(&space;S^T&space;MS&space;)\dot{\nu}&space;&plus;&space;S^T&space;(&space;M&space;\dot{S}\nu&space;&plus;&space;V&space;(&space;q&space;,&space;\dot{q}))&space;=&space;S^{T}&space;E&space;(&space;q&space;)\tau&space;;&space;\mathbf{(2)}" title="Lagrange multipliers eliminated" />
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\nu&space;=&space;[\dot{\alpha},v,\dot{\theta}]^T" title="https://latex.codecogs.com/svg.image?\nu = [\dot{\alpha},v,\dot{\theta}]^T" />
</p>

Then the _input-affine_ form of equations:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\dot{x}&space;=&space;f&space;(&space;x&space;)&space;&plus;&space;g&space;(&space;x&space;)&space;u;&space;x=\begin{pmatrix}&space;q_r&space;\\&space;\nu\end{pmatrix};\mathbf{(3)}" title="input-affine form" />
</p>

<p style="text-align:center;">
  
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?g&space;(&space;x&space;)&space;=&space;\begin{pmatrix}&space;0_{4*2}&space;\\&space;(S^T&space;M&space;S)^{-1}&space;S^T&space;E\end{pmatrix}_{7*2}&space;;&space;u=\begin{pmatrix}&space;\tau_r&space;\\&space;\tau_l\end{pmatrix};&space;\mathbf{(4)}" title="" />
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?f&space;(&space;x&space;)&space;=\begin{pmatrix}&space;f_1(x)&space;\\&space;f_2(x)\end{pmatrix}=\begin{pmatrix}&space;S_r&space;\nu&space;\\&space;-(S^T&space;M&space;S)^{-1}&space;S^T&space;(M\dot{S}\nu&space;&plus;&space;V(q_r,&space;\dot{q_r}))\end{pmatrix}_{7*1}&space;;&space;q_r=[x_o,y_o,\theta,\alpha]^T;\mathbf{(5)}" title="" />
</p>

Now let's feedback linearize the system, considering that it has maximum _relative degree_:





