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
  <img src="https://latex.codecogs.com/svg.image?g&space;(&space;x&space;)&space;=[g_1(x),&space;g_2(x)]=&space;\begin{pmatrix}&space;0_{4*2}&space;\\&space;(S^T&space;M&space;S)^{-1}&space;S^T&space;E\end{pmatrix}_{7*2}&space;;&space;u=\begin{pmatrix}&space;\tau_r&space;\\&space;\tau_l\end{pmatrix};&space;\mathbf{(4)}" title="" />
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?f&space;(&space;x&space;)&space;=\begin{pmatrix}&space;f_1(x)&space;\\&space;f_2(x)\end{pmatrix}=\begin{pmatrix}&space;S_r&space;\nu&space;\\&space;-(S^T&space;M&space;S)^{-1}&space;S^T&space;(M\dot{S}\nu&space;&plus;&space;V(q_r,&space;\dot{q_r}))\end{pmatrix}_{7*1}&space;;&space;q_r=[x_o,y_o,\theta,\alpha]^T;\mathbf{(5)}" title="" />
</p>

And the new feedback law is:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\omega_1=f_2[3]&plus;v_2&space;" title="" />
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\omega_2=f_2[1]&plus;g_1[5]v_1;&space;\mathbf{(6)}&space;" title="" />
</p>

Now let's feedback linearize the system. Considering, it has maximum _relative degree_, the change of coordinates is given by:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?z&space;=&space;T(x)=\begin{pmatrix}&space;x_3\\&space;x_7\\&space;x_4\\&space;x_5\\&space;x_1\\&space;x_2\\&space;&space;-x_5g_1[6]&plus;x_6g_1[5]\\\end{pmatrix};&space;\mathbf{(7)}" title="" />
</p>

Finally the equations of system become:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\dot{z}_1=z_2,&space;\dot{z}_2=\omega_1,\dot{z}_3=z_4,\dot{z}_4=\omega_2" title="" />
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\dot{z}_5=(\frac{z_7&plus;g_1[6]z_4}{g_1[5]})cos(z_1)" title="" />
<p/>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\dot{z}_6=(\frac{z_7&plus;g_1[6]z_4}{g_1[5]})sin(z_1)" title="" />
<p/>


<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\dot{z}_7=z_4(-z_4\frac{\partial&space;g_1[6]}{\partial&space;z_3}&plus;\frac{\partial&space;g_1[5]}{\partial&space;z_3}\frac{z_7&plus;g_1[6]z_4}{g_1[5]})&plus;g_1[5](f_2[2]-f_2[1]\frac{g_1[6]}{g_1[5]});&space;\mathbf{(8)}&space;" title="" />
<p/>







