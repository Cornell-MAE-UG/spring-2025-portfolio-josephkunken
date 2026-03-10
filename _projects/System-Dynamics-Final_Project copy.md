---
layout: project
title: Hand Mixer Control System Analysis
description: MAE 3260 System Dynamics Final Project
technologies: [AutoDesk Fusion360, Ansys]
image: /assets/images/MAE-3260-Final-Project/MAE-3260-Hand-Mixer.png
---


In a group of 4 members, we physically dissassembled an electric hand mixer using a variety of hand tools to expose each mechanical component of the system.  Then we analyzed the control systems of the system, studying how the hand mixer attained certain speeds.

First, we dissassembled the hand mixer.  This process was especially difficult due to the inconvenient placing of certain screws, making them more difficult or impossible to remove.  The outer casing was secured with a triangle screw bit.  Lacking a triangle bit screwdriver, we were forced to saw and leverage the plastic in order to break it open.

The hand mixer contains 5 different speeds, which are controlled by a switch that connects the power to a transformer coil.  Each speed setting determines how many number of turns are connected in the circuit, and how much voltage is applied.



<!-- First additional image: dissassembled wrench with caption -->
<figure style="width:50%; margin:20px 0; display:block;">
  <img src="{{ '/assets/images/MAE-3260-Final-Project/MAE-3260-Hand-Mixer-Switch-2.png' | relative_url }}" 
       alt="Dissassembled view" 
       style="width:100%; display:block;">
  <figcaption style="text-align:center; font-size:0.9em;">Speed Control Switch Mechanism</figcaption>
</figure>

This transformer formed a magnetic circuit with a 12 pole motor.

<!-- First additional image: dissassembled wrench with caption -->
<figure style="width:50%; margin:20px 0; display:block;">
  <img src="{{ '/assets/images/MAE-3260-Final-Project/MAE-3260-Hand-Mixer-Mechanism.png' | relative_url }}" 
       alt="Dissassembled view" 
       style="width:100%; display:block;">
  <figcaption style="text-align:center; font-size:0.9em;">Hand Mixer Transformer Coil</figcaption>
</figure>

 The motor then led to a worm gear drive to spin the whisk.  The worm gear to helical gear ratio was 1:20, leading to the whisk speed being 1/20th the motor speed.  The motor also controlled a fan which provided cooling to the circuitry, which would quickly heat up with use.

<!-- First additional image: dissassembled wrench with caption -->
<figure style="width:50%; margin:20px 0; display:block;">
  <img src="{{ '/assets/images/MAE-3260-Final-Project/MAE-3260-Hand-Mixer-Gear.png' | relative_url }}" 
       alt="Dissassembled view" 
       style="width:100%; display:block;">
  <figcaption style="text-align:center; font-size:0.9em;">Gear Mechanism</figcaption>
</figure>

We created a model using first order ODE's based on the system.  From these ODE's I formed the state space model.  
<!-- Side-by-side images -->
<div style="display:flex; gap:20px; flex-wrap:wrap; margin:20px 0;">
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3260-Final-Project/MAE-3260-ODE-Model.png' | relative_url }}" 
         alt="Rotor view" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">ODE's</p>
  </div>
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3260-Final-Project/MAE-3260-State-Space-Model.png' | relative_url }}" 
         alt="Hammer mechanism" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">State Space Model</p>
  </div>
</div>

I then generated a Matlab script in order to analyze the system using the state space model to observe the angular velocity response of the motor/whisk.  With this script, I was able to extract the settling time of the system as it approached a steady state angular velocity, calculated the steady state angular velocity, calculated the settling time, and plotted graphs to observe this response.  A minimum and maximum steady state velocity was graphed, based on the range of constants while maintaining a constant voltage.  In reality this voltage would be lower for lower speed settings.

<!-- Side-by-side images -->
<div style="display:flex; gap:20px; flex-wrap:wrap; margin:20px 0;">
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3260-Final-Project/MAE-3260-Hand-Mixer-Whisk-Minimum-Speed.png' | relative_url }}" 
         alt="Rotor view" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Whisk Minimum Speed Model Response</p>
  </div>
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3260-Final-Project/MAE-3260-Hand-Mixer-Whisk-Maximum-Speed.png' | relative_url }}" 
         alt="Hammer mechanism" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Whisk Maximum Speed Model Response</p>
  </div>
</div>

This was compared to experimental results observing the angular velocity ramp up when the hand mixer was turned on, measured using a high speed camera.  Significant differences emerged between the settling times with the model's settling time being much greater.  This indicates that some of the constants used could have been different, notably the inductance of the transformer coil.  However, the steady state angular velocity of the highest speed setting did fall in between the minimum and maximum steady state angular velocities calculated from the model.

In future analysis, the model will have to be refined further using more exact values for the constants and including disturbances such as friction between the gears and from other sources.

This project showed me how to analyze a physical controls system and the various contrasts that appear between an idealized model and experimental data.

[Access the full report]({{ "/assets/MAE3260-Hand-Mixer-Project-Report.pdf" | relative_url }}) in PDF format.