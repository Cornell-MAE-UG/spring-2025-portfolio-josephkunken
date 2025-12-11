---
layout: project
title: Torque Wrench Design/Analysis
description: MAE 3270 Mechanics of Engineering Materials Final Project
technologies: [Autodesk Fusion360, Ansys FEA]
image: /assets/images/MAE-3270-Torque-Wrench/MAE-3270-Torque-Wrench-Diagram.png
---
Above is the simplified model of the analyzed system.  The model seeks to design a torque wrench handle to survive a torque of 600 in-lbf at the drive with a force applied at the end of the handle.

Design and analysis was conducted to determine what material a torque wrench should be made out of, as well as with what basic dimensions, in order to withstand a variety of stresses and conditions.  These include withstanding yielding, cyclic loading, and fracture from crack formation.  Analysis was first conducted using hand calculation of the system for each case, followed by analysis using Finite Element Analysis.  All analysis used a simplified model of a rectangular wrench handle.

The design requirements included:
- A minimum safety factor against yield or brittle fracture of X<sub>o</sub> = 4
- A minimum safety factor against crack growth of X<sub>k</sub> = 2
- A minimum safety factor against cyclic loading fatigue of X<sub>s</sub> = 1.5 for a rated torque T = &plusmn;600 in-lbf
- a minimum strain gauge output of 1.0 mV/V to allow for sufficient sensitivity for analysis

The chosen design to meet all these requirements used: 
- Material = Titanium alloy Ti-24Al-11Nb. 
- b = 0.7 in
- h = 0.6 in
- L = 14 in

With a strain gauge at c = 1 in from the drive location.

<!-- First additional image: dissassembled wrench with caption -->
<figure style="width:50%; margin:20px 0; display:block;">
  <img src="{{ '/assets/images/MAE-3270-Torque-Wrench/MAE-3270-Torque-Wrench-CAD.png' | relative_url }}" 
       alt="Dissassembled view" 
       style="width:100%; display:block;">
  <figcaption style="text-align:center; font-size:0.9em;">Autodesk Fusion 360 simplified model used for FEA analysis</figcaption>
</figure>


Below are images of the FEA boundary conditions of this model.  The drive is held fixed while a force is applied at the end of the handle.  This results in a reaction force and reaction moment at the drive.

<!-- Side-by-side images -->
<div style="display:flex; gap:20px; flex-wrap:wrap; margin:20px 0;">
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3270-Torque-Wrench/Model Screenshot/MAE-3270-Torque-Wrench-Ansys-Force-Application.png' | relative_url }}" 
         alt="Rotor view" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Force Application</p>
  </div>
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3270-Torque-Wrench/Model Screenshot/MAE-3270-Torque-Wrench-Ansys-Force-Reaction.png' | relative_url }}" 
         alt="Hammer mechanism" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Reaction Force</p>
  </div>
</div>

Below are images of the FEA analysis showing the normal strain contours in the strain gauge direction (along the length of the handle), as well as the maximum principal stress contours.  These indicate the stress concentrations present in the system.

<!-- Side-by-side images -->
<div style="display:flex; gap:20px; flex-wrap:wrap; margin:20px 0;">
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3270-Torque-Wrench/Model Screenshot/MAE-3270-Torque-Wrench-Ansys-Strain.png' | relative_url }}" 
         alt="Rotor view" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Strain Contours</p>
  </div>
  <div style="width:48%;">
    <img src="{{ '/assets/images/MAE-3270-Torque-Wrench/Model Screenshot/MAE-3270-Torque-Wrench-Ansys-Principal-Stress.png' | relative_url }}" 
         alt="Hammer mechanism" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Principal Stress Contours</p>
  </div>
</div>

The Ansys analysis yielded the following key values.  The maximum normal stress was 49.649 ksi, much greater than the theoretically calculated maximum of 14.286 ksi due to the presence of stress concentrations at the drive's connection to the handle.  The maximum deflection of the handle, at the very end where the force is being applied, is 0.30112 in, which is lower than the expected deflection of 0.5723 in.  At the strain gauge, the measured strain was 0.0010127 in/in, almost exactly matching the expected value of 0.0010126 in/in.  The strain gauge sensitivity is thus 1.0126 mV/V using a half-bridge gauge.

Below are images of the analysis for the normal stress, deformation, and strain gauge strain readings.  

<!-- Three images side-by-side -->
<div style="display:flex; gap:10px; flex-wrap:wrap; margin:20px 0;">
  <div style="flex:1 1 0; min-width:0;">
    <img src="{{ '/assets/images/MAE-3270-Torque-Wrench/Model Screenshot/MAE-3270-Torque-Wrench-Ansys-Stress.png' | relative_url }}" 
         alt="Image 1" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Normal Stress</p>
  </div>
  <div style="flex:1 1 0; min-width:0;">
    <img src="{{ '/assets/images/MAE-3270-Torque-Wrench/Model Screenshot/MAE-3270-Torque-Wrench-Ansys-Deformation.png' | relative_url }}" 
         alt="Image 2" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Deformation</p>
  </div>
  <div style="flex:1 1 0; min-width:0;">
    <img src="{{ '/assets/images/MAE-3270-Torque-Wrench/Model Screenshot/MAE-3270-Torque-Wrench-Ansys-Strain-Gauge-Strain.png' | relative_url }}" 
         alt="Image 3" style="width:100%; display:block;">
    <p style="text-align:center; font-size:0.9em;">Strain at Strain Gauge</p>
  </div>
</div>

In order to allow for this analysis given the chosen physical dimensions of the torque wrench handle, the strain gauge Omega SGT Uniaxial Half-Bridge Strain Gauge is chosen.

This project was enlightening as it allowed me to explore designing a physical component while keeping in mind multiple failure modes to design against, physical dimensions for better ergonomics, and relative cost of the material being used.  It also gave me the opportunity to further explore FEA analysis of physical components and analyzing the differences between FEA simulation results, and results from theoretical hand calculations.