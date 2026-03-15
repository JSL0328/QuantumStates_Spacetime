# QuantumProbe-CV: Spacetime Metrology in Realistic Channels

A comprehensive framework and simulation suite for estimating spacetime parameters using Continuous Variable (CV) quantum states under realistic space mission constraints.

## Executive Summary
This project aims to bridge the gap between theoretical quantum metrology and practical satellite-based quantum communications. We investigate the measurement of spacetime parameters, such as the Schwarzschild radius, using CV quantum states over Inter-Satellite Links (ISL) and Ground-to-Geostationary (GEO) links. By rigorously classifying physical hardware and environmental noises, we uncover the "Anti-Squeezing Dilemma"—proving that in realistic space missions, maximum quantum squeezing is not optimal and can catastrophically degrade measurement precision.

## Problem Statement
- **The "Ideal Vacuum" Fallacy**: Previous theoretical frameworks assumed idealized, noiseless vacuum channels. Under these assumptions, the consensus was that allocating 100% of the probe energy to the squeezed vacuum always yields the highest precision.
- **The Reality Gap**: Real space missions suffer from extreme path loss, atmospheric turbulence, and fixed hardware noises. Unbounded squeezing in such environments leads to fatal signal degradation, rendering previous models impractical for actual satellite missions.

## Proposed Solution and Core Objectives

### 1. Rigorous Noise Classification
We categorize intrinsic physical noises into two fundamentally different types:
- **Channel-Induced Noise ($V_{nc}$)**: Noise that propagates and accumulates with the signal. Includes Laser Phase Noise and Atmospheric Noise.
- **Fixed Detector Noise ($V_{nd}$)**: Hardware noise that persists independently of channel attenuation. Includes Accelerometer Noise and Satellite Platform Vibrations.
- *(Note: Fundamental shot noise is explicitly excluded from these summations to prevent double-counting within the Quantum Fisher Information formulation).*

### 2. ITU-T Standard Compatibility
Unlike previous studies relying on 700 THz (430 nm) to avoid thermal noise, our numerical evaluations are performed at **193.5 THz (1550 nm)** to align with actual satellite communication standards (ITU-T) and the practical capabilities of state-of-the-art laser hardware.

## Key Discovery: The Anti-Squeezing Dilemma
Through our simulation model, we discovered critical behavior in realistic space quantum metrology:
- **Ideal Conditions**: Estimation error decreases monotonically as the squeezing fraction $y$ approaches 1.
- **Realistic ISL (600 km)**: A distinct optimal threshold emerges at approximately $y \approx 0.2$. Exceeding this threshold causes the estimation error to diverge.
- **Realistic GEO (35,630 km)**: Due to immense distance and atmospheric noise, the optimal strategy shifts overwhelmingly towards coherent states ($y \to 0$).

**The Physical Cause**: Excessive squeezing amplifies the fixed hardware noise floor ($V_{nd}$) via the anti-squeezing effect in the conjugate quadrature. Thus, a careful balance between coherent amplitude and the squeezing fraction is essential.

## System Architecture (The Quantum Channel Model)
The simulation pipeline follows this physical timeline:
1. **Probe Generation**: Generation of the initial CV probe state with an adjustable squeezing fraction.
2. **Channel Propagation**: Attenuation via transmissivity ($t$) and addition of distance-dependent Channel Noise ($V_{nc}$).
3. **Phase Encoding**: Imprinting the gravitationally induced phase shift.
4. **Detection**: Addition of the Fixed Detector Noise ($V_{nd}$) at the receiver.
5. **Estimation**: Calculation of the Quantum Fisher Information (QFI) and Cramér-Rao bound for the relative error.

## Simulation Environments Evaluated
1. **ISL (LEO-to-LEO)**:
   - Distance: ~600 km
   - Characteristics: Vacuum environment with negligible atmospheric noise. Evaluates the impact of fixed detector hardware noise.
2. **GEO (Ground-to-GEO)**:
   - Distance: ~35,630 km
   - Characteristics: Extreme free-space diffraction and severe atmospheric turbulence. Evaluates the theoretical limits of quantum advantage.

## Discussion
The results of this study suggest that the practical implementation of quantum-enhanced spacetime probing requires a fundamental shift in state preparation strategies. 

First, the **Anti-Squeezing Dilemma** highlights that hardware limitations ($V_{nd}$) impose a "soft ceiling" on the utility of squeezed states. In high-loss scenarios like GEO links, the amplification of anti-squeezed noise can quickly overwhelm the benefits of reduced uncertainty in the signal quadrature. 

Second, the adoption of the **193.5 THz (1550 nm)** standard demonstrates that quantum advantage is still attainable within the constraints of current telecommunication infrastructure, provided that the squeezing fraction is dynamically optimized. 

Future mission designs must prioritize the minimization of receiver-side platform vibrations and accelerometer noise to push the boundaries of quantum-enhanced geodetic measurements. This framework can be further extended to evaluate precision limits for other cosmological parameters, such as the Hubble constant or gravitational wave amplitudes, under non-stationary satellite trajectories.
