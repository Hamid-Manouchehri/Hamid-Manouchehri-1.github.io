---
title:  "Nonlinear Control of an Inverted Pendulum by Partial Feedback Linearization"
mathjax: true
layout: post
categories: media
---

within the course of __Nonlinear Control__, I was intended to simulate the result of [this paper](https://ieeexplore.ieee.org/document/1435497), __"Velocity and Position Control of a Wheeled Inverted Pendulum by Partial Feedback Linearization"__, via _MATLAB_. Considering the inverted pendulum is an _underactuated system_, it is demanding to control such a _nonlinear_ underactuated system, because there are less controllabe states than total states of the system.

<p style="text-align:center;">
  <img width="341" height="296" src="/img/sim_wheeled_inverted_pendulum/inverted_pendulum.png" alt="inverted pendulum model">
</p>

As we know that __Feedback Linearization__ is a technique for transforming the main system to a simpler form, in this case, first we derive the dynamic equations of the system, next we _partially feedback linearize_ the system, Finally apply the controller.

### Dynamic Model
<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?M&space;(&space;q&space;)&space;\ddot{q}&space;&plus;&space;V&space;(&space;q&space;,&space;q&space;_&space;)&space;=&space;E&space;(&space;q&space;)\tau&space;&space;&plus;&space;A^T&space;(&space;q&space;)&space;\lambda;&space;\mathbf{(1)}" title=" dynamic equation of wheeled inverted pendulum" />  
</p>

Eliminate _Lagrange multipliers_ &lambda; with $$S^T$$:

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

Now let's __feedback linearize__ the system. Considering, it has maximum _relative degree_, the change of coordinates is given by:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?z&space;=&space;T(x)=\begin{pmatrix}&space;x_3\\&space;x_7\\&space;x_4\\&space;x_5\\&space;x_1\\&space;x_2\\&space;&space;-x_5g_1[6]&plus;x_6g_1[5]\\\end{pmatrix};&space;\mathbf{(7)}" title="" />
</p>

Finally the equations of the system become:

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


### Design and Implementation of controllers
#### Velocity Controller

<p>
  In order to control desired parameters of the system, we need two controllers; a __lower level__ controller with fast dynamics to track $$\theta_d$$ and $$\alpha_r$$, and a __higher level__ controller with slow dynamics to make sure $$ \alpha_r \in A_s$$:
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?C_l:&space;\omega_1=-k_{qv}\dot{\theta}-k_q(\theta-\theta_d),&space;\omega_2=-k_{av}\dot{\alpha}-k_a(\alpha-\alpha_r);&space;\mathbf{(9)}" title="" />
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?C_h:&space;\dot{\alpha}_r=k_rf_{ss}-k_v(\alpha^2_m-\alpha^2_r)^2(v_{ss}-v_d)\frac{f_{ss}}{\alpha_r};&space;\mathbf{(10)}" title="" />
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\dot{v}_{ss}=f_{ss}(\alpha_r)=[\frac{1}{g_1[5]}(g_1[5]f^\alpha_{22}-f^\alpha_21g_1[6])]_{\alpha=\alpha_r};\mathbf{(11)}" title="" />
</p>

Simulation of equation (11):

<p style="text-align:center;">
  <img width="788" height="425" src="/img/sim_wheeled_inverted_pendulum/f_ss_alpha_r.png" alt="f_ss">
</p>

Now the outputs for step and stop commands:

<p style="text-align:center;">
  <img width="814" height="456" src="/img/sim_wheeled_inverted_pendulum/stop_command.png" alt="stop command">
</p>

<p style="text-align:center;">
  <img width="780" height="420" src="/img/sim_wheeled_inverted_pendulum/step_command.png" alt="step command">
</p>


#### Position and Stabilization Control
Here we want to design a controller to stabilize the robot in a desired coordination against the world frame. For this, it is better to deploy polar coordination for for configuration space of the robot:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?P=[\rho,\phi,\theta,\alpha&space;]^T;\mathbf{(12)}" title="" />
</p>

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\dot{v}_{ss}=f(\alpha_r,\dot{\theta})=\begin{bmatrix}(f^\alpha_{22}&plus;f^{\dot{\theta}}_{22})-(f^\alpha_{21}&plus;f^{\dot{\theta}}_{21})\frac{g_1[6]}{g_1[5]}\end{bmatrix}_{\alpha=\dot{\alpha}}&space;;\mathbf{(13)}" title="" />
</p>

The simulation:

<p style="text-align:center;">
    <img width="848" height="451" src="/img/sim_wheeled_inverted_pendulum/f_ss_alpha_r_theta_dot.png" alt="f_ss_theta_dot">
</p>

Same as befor we need two types of controller, higher level and lower level controllers, for __higher level__ controller, we consider the following _potential function_:

<p style="text-align:center;">
    <img src="https://latex.codecogs.com/svg.image?V_\Sigma=\frac{1}{2(\alpha^2_m-\alpha^2_r)}&plus;\frac{k_v(v_{ss}-v_d)^2}{2};&space;\mathbf{(14)}" title="" />
</p>

We propose the following control signal:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\omega_1=-\frac{\partial&space;V_\Sigma&space;}{\partial&space;\theta}-k_\omega\dot{\theta};&space;\mathbf{(15)}" title="" />
</p>

Finally, by substituting $$\alpha_r$$ in the following equation, stability would be satisfied.

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?f_{ss}(\alpha_r,&space;\dot{\theta})=-(\frac{\partial&space;V_\Sigma&space;}{\partial&space;\rho}cos(\theta-\phi)&plus;\frac{\partial&space;V_\Sigma&space;}{\partial&space;\phi}\frac{sin(\theta-\phi)}{\rho})-k_vv;\mathbf{(16)}" title="" />  
</p>

And the __lower level__ controller is:

<p style="text-align:center;">
  <img src="https://latex.codecogs.com/svg.image?\omega_2=-k_{av}\dot{\alpha}-k_a(\alpha-\alpha_r);\mathbf{(17)}" title="" />
</p>

To get more details, please refer to the papaer and keep in touch with me. :)
