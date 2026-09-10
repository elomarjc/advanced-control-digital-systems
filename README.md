# 🛰️ AAUSAT6 CubeSat: Attitude Determination & Control System (ADCS)

<div align="center">

# AAUSAT6 Attitude Determination & Control System (ADCS)
### Master's Project (Semester 8) • Electronic Systems & Advanced Control
**Aalborg University (AAU) • Student Space Programme**

[![Domain](https://img.shields.io/badge/Domain-Aerospace_ADCS-0B3D91?style=for-the-badge)](https://github.com/elomarjc)
[![Controllers](https://img.shields.io/badge/Controllers-B--dot_%7C_Momentum_Wheels_%7C_Robust-darkgreen?style=for-the-badge)](https://github.com/elomarjc)
[![Academic](https://img.shields.io/badge/AAU-AAUSAT6_CubeSat-0C2340?style=for-the-badge)](https://www.aau.dk)

</div>

---

## 🌌 Project Overview

In Low Earth Orbit (LEO), nanosatellites (CubeSats) must reliably orient their solar panels toward the Sun, antennas toward ground stations, and scientific payloads toward target observation zones. Following separation from the launch vehicle, the satellite experiences unknown angular tip-off rates, entering an uncontrolled spin that must be rapidly mitigated.

This project delivers the mathematical modeling, simulation, and closed-loop control architecture for the **Attitude Determination and Control System (ADCS)** of the **AAUSAT6 CubeSat** at Aalborg University.

---

## 🧠 Flight Control Architecture & Modes

The spacecraft ADCS architecture implements multi-mode attitude stabilization tailored for LEO operations:

```
 Launch Vehicle Separation ──► [ Mode 1: Detumbling (B-dot) ] ──► Low Angular Rates
                                                                        │
                                                                        ▼
 Ground Communication / Sun ◄── [ Mode 3: Robust Pointing ] ◄── [ Mode 2: Momentum Wheels ]
```

### 1. Detumbling Mode (B-dot Magnetic Controller)
* **Objective**: Rapidly dissipates kinetic rotational energy after launch deployment using only ambient geomagnetic field interactions.
* **Control Law**: The control dipole moment $\mathbf{m}$ is actuated in direct opposition to the rate of change of the measured geomagnetic field vector $\mathbf{\dot{B}}$:

$$
\mathbf{m} = -k \mathbf{\dot{B}}
$$
* **Actuation**: 3-axis electromagnetic coils (magnetorquers) interacting with the Earth's magnetic flux density $\mathbf{B}$ to generate damping torques $\boldsymbol{\tau} = \mathbf{m} \times \mathbf{B}$.

### 2. Nominal Pointing Mode (Reaction & Momentum Wheels)
* Employs internal high-speed reaction/momentum wheels to transfer angular momentum between the satellite body and wheel rotors, achieving fine 3-axis nadir and solar pointing.

### 3. Robust Attitude Regulation ($H_\infty$ Control)
* Formulates robust control strategies to reject unmodeled orbital disturbances:
  - Atmospheric drag torques in upper thermosphere.
  - Solar radiation pressure (SRP) moments.
  - Residual magnetic dipole interactions.

---

## 📁 Repository Structure

```
advanced-control-digital-systems/
├── B-dot controller/                    # MATLAB simulations and algorithms for magnetic detumbling
├── Momentum_Wheels/                     # Reaction wheel dynamic models and angular momentum exchange
├── Robust_Controller/                  # H-infinity robust control synthesis and disturbance rejection
├── Problem_and_Solution_Calculations/ # Orbital mechanics, moment of inertia tensors, torque derivations
├── space_simulator_wiki_version/      # Space environment simulator models (IGRF magnetic model, gravity gradient)
├── Literature/                         # Reference papers on CubeSat ADCS, magnetorquers, and LEO dynamics
└── Images/                             # Architectural diagrams, simulation plots, and spacecraft schematics
```

---

## 🎓 Academic Context

* **Course**: 8th Semester Master's Project (Systemer af systemer)
* **Title**: *Attitude Determination and Control System for AAUSAT6*
* **Degree**: M.Sc. in Electronic Systems
* **Institution**: Aalborg University, Denmark (AAU)
* **Programme**: AAU Student Space Programme • AAUSAT6 CubeSat Mission
