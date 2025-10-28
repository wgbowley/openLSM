<p align="center">
  <img src="media\images\bluefin.png" alt="BlueFin Logo" style="max-width:600px;">
  <br>
  <em> High Performance Low Cost Linear Motors – built with love by <a href="https://github.com/wgbowley">William Bowley</a> & <a href="https://github.com/LawsonDG">Lawson Gallup</a> </em>
</p>

---
![Work in Progress](https://img.shields.io/badge/status-wip-orange)
![License](https://img.shields.io/badge/license-MIT-green)

Part of the `blue` series projects, with the goal of making linear motors viable for 3D printing and other applications at the hobbyist level.

## Overview
**BlueFin** is the umbrella name for a series of low-cost, high-performance linear synchronous motors (LSMs) for 3D printing. The objective of **BlueFin** is to design and validate an LSM for hobbyists to make with limited resources and tooling. 

### Objectives
- Basic design must be 3D-printable using standard materials  
- Target force output: **15–25 N** with ripple force of ±5%  
- Options for passive or active cooling  
- Custom driver board using field-oriented control (FOC)  
  - Option for step/dir input  

## Prototype 0: Flat LSM (FLSM)

<div align="center">
  <img src="media/images/flat_linear_motor.png" alt="Prototype 0: Flat LSM" style="max-width: 600px; width: 100%; height: auto;">
</div>

Prototype 0 had a force output of ~0.5 N with ~20 W input power. This first prototype showed poor force output and efficiency but did prove that a 3D-printed linear motor can be made. Here are the main insights:

1. **Architecture mismatch**  
   FLSMs can achieve high force (commercially proven), but they rely on laminated silicon steel armatures. This is not ideal for a hobbyist as they’re quite complex to manufacture. It also breaks the project’s objectives, so a new architecture must be explored.  
   > This path may still be revisited; documentation can be found in [/flat_lsm](/motors/flat_lsm/).

2. **Thermal mismanagement**  
   Thermal analysis of the motor during operation was not performed, and as a result, the coil forms melted in testing. This led to increased friction between the armature and track. Future work must integrate thermal analysis directly into the optimization process. 

3. **High phase resistance**  
   `0.21mm` copper wire was chosen as it was on hand, but it proved to have much too high resistance after winding the coils. Hence, future iterations should perform a parametric sweep of wire sizes during optimization while biasing toward lower phase resistance.

Even with speculative improvements (e.g., increasing force-per-watt to **0.05 N/W**), it would take ~400 W to reach the force target. For an XY-coordinate 3D printer, it would require two motors at 800 W, which makes this architecture rather impractical for hobbyists.

---

## Current Development: Tubular LSM (TLSM)
![Prototype 1: Tubular LSM](media/images/tubular_linear_motor.png)

>This design is directly based on work done by cmore839 in [DIY Linear Motor](https://github.com/cmore839/DIY-Linear-Motor)
