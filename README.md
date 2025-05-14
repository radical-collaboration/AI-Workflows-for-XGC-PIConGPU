# AI Workflows for XGC PIConGPU

Enabling AI Workflows for Particle-In-Cell (PIC) simulations presented by 
[XGC](https://xgc.pppl.gov/html/general_info.html) and 
[PIConGPU](https://helmholtz.software/software/picongpu).

## Overview

**XGC** is a gyrokinetic particle-in-cell (PIC) code, which specializes in the 
simulation of the edge region of magnetically confined thermonuclear fusion 
plasma. It has capabilities for both tokamak and stellarator geometries. 
The simulation domain can include the magnetic separatrix, the magnetic axis, 
and the biased material wall. XGC is written in C++ and Fortran90 and features 
efficient, highly optimized numerics. It is designed for heterogeneous HPCs 
use Kokkos for vendor-independent GPU offloading, vectorization, and 
portability. All I/O is performed with ADIOS2. Weak scaling is roughly linear 
to the maximal number of compute nodes of the leading US HPC platforms.

**PIConGPU** is a high performance particle-in-cell (PIC) code for 
the simulation of laser matter interaction and high energy density physics 
with applications in laser particle acceleration, laser fusion and astrophysics. 
It uses a 3D3V relativistic approach where the plasma particles are modeled as 
macroparticles in a lattice, and their dynamics are solved iteratively using 
a variety of algorithms, such as the Boris Pusher and Esirkepov schemes. 
The electromagnetic fields are updated based on the particle motion.
PIConGPU shows excellent weak and strong scaling on large HPC systems, such as 
Frontier@OLCF, using AMD MI250X GPUs. It handles large particle-to-cell 
ratios and is optimized for large-scale simulations, demonstrating excellent 
scalability and achieving up to 65.3 TeraUpdates/s on Frontier@OLCF.
The code is written in C++ and leverages the alpaka library 
(https://helmholtz.software/software/alpaka) for cross-platform performance 
portability, e.g., on NVIDIA, Intel, AMD, and OpenPower systems. 
For high-performance data handling, PIConGPU integrates openPMD 
(https://www.openpmd.org/) for efficient particle data output and uses ADIOS2 
for in-transit streaming to avoid file system bottlenecks. The openPMD data 
standard provides an open and FAIR data standard for particle and mesh data. 
OpenPMD is key for coupling with machine learning (ML) workflows to analyze 
radiation spectra from plasma dynamics. The far-field radiation plugin, which 
uses the Liénard-Wiechert potential, is used to compute radiation emissions 
in-situ, despite its high computational cost. A machine learning model is 
trained to predict particle distributions from these radiation outputs, 
solving the inversion problem and allowing better interpretation of plasma 
behavior based on observable radiation.

**RADICAL** tools are middleware building blocks that provide scalable, modular, 
and interoperable programming systems to execute heterogeneous workloads on 
heterogeneous HPC resources. **RADICAL-Pilot** is a scalable pilot-based 
runtime system that provides flexible application-level resource management 
capabilities; **ROSE (RADICAL Optimal & Smart-Surrogate Explorer)** simplifies 
the ability to implement online AI/ML workflows on HPC.

***

This effort is the result of the collaboration during 
[Spring 2025 AI Focused Frontier Hackathon](https://www.olcf.ornl.gov/calendar/spring-2025-ai-focused-frontier-hackathon/)
