# Simulation of a Transfemoral Prosthetic Leg

> **Author:** Hari Prasad Gajurel  
> **Date:**  2025 
> **Topic:** Robotics / Biomechanics / Control Systems  

---

## Overview

Briefly describe the purpose of your project. For example:
This project simulates the knee joint dynamics of an active transfemoral prosthetic leg during the stance and swing phases of human gait.

---

## 1. System Dynamics & Equations of Motion

Explain the physics or math involved. GitHub supports LaTeX formatting using single `$` for inline math and `$$` for block math equations.

$$M(\theta)\ddot{\theta} + C(\theta, \dot{\theta})\dot{\theta} + G(\theta) = \tau_{\text{actuator}}$$

Where:
- $M(\theta)$: Inertia matrix of the shank segment.
- $C(\theta, \dot{\theta})$: Coriolis and centrifugal forces.
- $G(\theta)$: Gravitational forces.
- $\tau_{\text{actuator}}$: Torque provided by the motor at the knee joint.

---

## 2. Simulation Setup

Describe the tools, CAD models, or physics engine used (e.g., PyBullet, Gazebo, Simscape, OpenSim).

* **Physics Engine:** PyBullet / MuJoCo
* **Control Strategy:** Proportional-Integral-Derivative (PID) + Impedance Control
* **Integration Step:** 0.001s

---

## 3. Code Implementation

Include code snippets using syntax highlighting:

```python
import numpy as np

def compute_impedance_torque(theta, theta_d, dtheta, dtheta_d, K, D):
    """
    Computes virtual spring-damper torque for joint impedance control.
    """
    error_pos = theta_d - theta
    error_vel = dtheta_d - dtheta
    return K * error_pos + D * error_vel
