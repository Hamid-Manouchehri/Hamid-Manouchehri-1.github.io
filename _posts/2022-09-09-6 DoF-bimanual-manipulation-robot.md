As a part of my master's thesis, for implementing the inverse dynamics algorithm to an upper-body bi-manual robot base on my supervisor [paper](https://www.researchgate.net/publication/320330613_Inverse_Dynamics_Control_of_Bimanual_Object_Manipulation_Using_Orthogonal_Decomposition_An_Analytic_Approach) in a 3D simulator, I had to work with __Gazebo__. First the [URDF](http://wiki.ros.org/urdf) model of the robot was prepared by the help of my teammate, Ms [Nooshin Kohli](https://github.com/nooshin-kohli), then other dependencies like torque controllers of joints, launch file, and etc attached, finally of courese the script of algorithm was written by a great deal of work. Actually the fundaments of algorithm for a 2D simulation was obtained beforehand by my supervisor and I developed it to 3D simulation in Gazebo.

<p>
  <img style="text-align:left;" width="275" height="265" src="/img/6dof_bimanual_manipulation/bimanual_1.png" alt="Logo">
  <img style="text-align:center;" width="275" height="265" src="/img/6dof_bimanual_manipulation/bimanual_2.png" alt="Logo">
  <img style="text-align:right;" width="275" height="265" src="/img/6dof_bimanual_manipulation/bimanual_3.png" alt="Logo">
  <figcaption>
    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Fig.1
    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Fig.2
    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Fig.3 
  </figcaption>
</p>

Although the control approach is dynamic cancellation, It was cumbersome to adjust joints' `damping` and `friction` in URDF model.

<p>
  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;
  <img style="text-align:center;" width="651" height="269" src="/img/6dof_bimanual_manipulation/control_system.png" alt="Logo">  
  <figcaption>
    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 
    Fig.4, <i> Introduction to Robotics, Craig </i>
  </figcaption>
</p>



