---
layout: project
title: Mechatronics Robot Competition
description: MAE 3780 Robot Competition Project
technologies: [Arduino C Programming, Autodesk Fusion360, Laser Cutting, 3D Printing, Electronics]
image: /assets/images/MAE-3780-Robot-Competition/MAE-3780-Robot-Competition.png
---

In a robot competition sponsored by ASML, in a team of 3 members, we won 3rd place out of 62 teams.  The aim of this competition was to use a constrained budget and physical dimensions to collect as many randomly scattered cubes on a 4'x4' board within one minute, while another opponent's robot was also on the board.  In my team, I handled all of the code required to operate the robot, as well as managing all of the wiring between electrical components.

The robot was constrained to using an Arduino Uno however without using any build-in Arduino libraries, coding the entire robot in C.  In addition, the robot had to begin any given round within an 8"x8" square, before being able to continue the round in a 12" diameter circle.  Additional constraints included the use of specific electrical components and the prohibition of potential damage being inflicted on an enemy robot.  There was also a budget constraint of $40 to be spent on laser cutting, 3D printing, and the purchasing of additional components.  


<!-- Side-by-side images -->
<div style="display:flex; gap:20px; flex-wrap:wrap; margin:20px 0;">
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3780-Robot-Competition/MAE-3780-Robot-Competition-CAD-Pre-Deployed.png' | relative_url }}" 
         alt="Rotor view" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">CAD Model In Pre-Deployed State</p>
  </div>
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3780-Robot-Competition/MAE-3780-Robot-Competition-CAD-Deployed.png' | relative_url }}" 
         alt="Hammer mechanism" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">CAD Model In Deployed State</p>
  </div>
</div>

Our final design included acrylic laser cut arms on either side to collect cubes.  A triangular shaped acrylic piece at the front served to push cubes into the arms as the robot moved forward, as well as serving as the mount for a color sensor and two QTI sensors.  Two servos connected to arms began the competition upright, but when started, would lower their arms to further extend the robot's reach.  Finally, a T-shaped "attack arm" would serve to potentially snag and disconnect an opponent's wires, as well as push other robots away.



<!-- First additional image: dissassembled wrench with caption -->
<figure style="width:50%; margin:20px 0; display:block;">
  <img src="{{ '/assets/images/MAE-3780-Robot-Competition/MAE-3780-Robot-Competition-Circuit-Diagram.png' | relative_url }}" 
       alt="Dissassembled view" 
       style="width:100%; display:block;">
  <figcaption style="text-align:center; font-size:0.9em;">Circuit Diagram</figcaption>
</figure>

This is the circuit diagram governing the wiring of our robot.  The electronics revolve around an Arduino Uno which controls:

- two H-Bridges to control the directions of the motors
- two motors for our driving wheels
- two servos for our extended arms
- a color sensor to detect which side of the board (yellow or blue), the robot is on
- two QTI sensors to detect the black outside border
- a 9V battery to power the Arduino
- a 6V battery pack to power the rest of the electronics

Coding and wiring the robot provided many challenges, but allowed for an amazing chance to control all of the functionality of the robot, integrating the mechanical components such as the servos and motors, with electrical sensors such as the color sensor and QTI's to create a system that can independently search and move across the board.  

I consistently had to rewire parts of the robot as the mechanical components such as the extended arms and triangular front section were improved upon, while maintaining compatibility with the code controlling it all.  By the time of the competition I also had to ensure that the wires would remain secure throughout each round, as a loose wire could instantly lead to immobility.  This was done through a combination of tape and looping wires through/around the chassis and mechanical connections to prevent them from straying too far outside our robot's perimeter.  I also minimized and color coded the wires to improve testing and maintenance capabilities.  

The competition's constraint against the use of built-in Arduino libraries also proved to be a significant hurdle.  It meant that certain advanced electronics could not be practically used due to their complexity such as a more advanced Distance Sensor that would have helped to detect other robots.  It also required me to code the entire system from its foundation, controlling every Arduino pin myself to dictate wheel direction, data collection from sensors, and servo movement.  This gave me a lot of experience in creating foundational functions that were then built upon to create more complex algorithms.  Additionally, I had to calibrate each sensor and motor to accurately reflect real conditions.  This meant simplifying the physics of the model to create formulas for driving certain distances and turning certain angles, as well as accounting for different lighting conditions for the color sensor and QTI sensors.

<!-- Side-by-side images -->
<div style="display:flex; gap:20px; flex-wrap:wrap; margin:20px 0;">
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3780-Robot-Competition/MAE-3780-Robot-Competition-Start.png' | relative_url }}" 
         alt="Rotor view" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Robot At Start of Competition Round</p>
  </div>
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3780-Robot-Competition/MAE-3780-Robot-Competition-First-Turn.png' | relative_url }}" 
         alt="Hammer mechanism" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Robot Making Initial Turn in Competition</p>
  </div>
</div>

The main strategy of our robot was to deploy our arms, then begin moving to the center at a 45 degree angle.  This served to minimize initial collisions with other robots.  When first hitting the opposite color (in this case blue), the robot would turn 135 degrees to then drive along the center of the board, collecting the most cubes.  For the rest of the competition the robot would simply drive around the board in straight lines, turning back towards the center when hitting the black border.  

Our method for border detection used two QTI sensors on the left and right sides of the front of our robot.  If the left QTI detected the black border, then the robot would turn to the right, and vice versa.  If both QTI sensors detected the border, then that meant we were pointed directly at the border, and so would make a much larger turn to point back at the board center.

As pictured, many robots failed to accurately detect the black border and simply drove off the board, becoming stuck.  This never was an issue for us.  

<!-- Side-by-side images -->
<div style="display:flex; gap:20px; flex-wrap:wrap; margin:20px 0;">
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3780-Robot-Competition/MAE-3780-Robot-Competition-Pre-Deployed.png' | relative_url }}" 
         alt="Rotor view" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Robot In Pre-Deployed State</p>
  </div>
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3780-Robot-Competition/MAE-3780-Robot-Competition-Deployed.png' | relative_url }}" 
         alt="Hammer mechanism" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Robot in Deployed State</p>
  </div>
</div>

This competition gave me valuable experience in creating a system from scratch that integrated mechanical, electrical, and computational components.  I learned how to build up programs to accomplish advanced tasks and techniques for conducting testing and prototyping of different designs and implementations.  I also worked with capable teammates to brainstorm ideas, split up tasks, and assist each other in combining them into a working robot.


[Access the full report]({{ "/assets/MAE-3780-Robot-Competition-Final-Report.pdf" | relative_url }}) in PDF format.