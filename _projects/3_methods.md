---
layout: page
title: "Methods & technical skills"
description: "End-to-end technical toolkit spanning first-principles DFT, neural-network interatomic potential development, classical MD/MC simulations, HPC workflows, and experimental materials characterization."
img: assets/img/research/mlip-training-study.webp
importance: 3
---

My research combines multi-scale atomistic simulation, machine-learning model development, and experimental characterization to solve transport and interfacial problems in electrochemical materials.

## Atomistic & multiscale simulation

- **Density Functional Theory (DFT):** Ab initio molecular dynamics (AIMD), structural relaxation, energy/force/virial dataset generation, and electronic structure calculations using **VASP**.
- **Molecular Dynamics (MD):** Large-scale classical and machine-learning potential MD simulations in **LAMMPS** for bulk crystalline ion conductors and solid/liquid electrode interfaces; trajectories analyzed for self-diffusivity, collective Nernst-Einstein conductivity, Haven ratio, nuclear density maps, and intermediate scattering functions.
- **Monte Carlo (MC):** Gas solvation and thermodynamic partitioning simulations in **GROMACS** to quantify solute solubility and spatial probability distributions across bulk and interfacial electrolyte regions.

## Machine-learning interatomic potentials (MLIPs)

- **Descriptor engineering:** Encoding local chemical environments into invariant representations using Atom-Centered Symmetry Functions (**ACSF** via **Simple-NN**, radial and angular symmetry functions) and local-coordinate frame transformations (**DeePMD-kit**).
- **Neural-network training & hyperparameter optimization:** Designing feed-forward neural network architectures and conducting systematic parametric studies across learning rates (e.g., 0.001 vs. 0.0005), validation split ratios (<i>v</i><sub>r</sub> = 0.2–0.5), activation functions (tanh vs. sigmoid, where sigmoid accelerates energy and force RMSE convergence), hidden-layer dimensions, and training iterations (30,000–40,000 steps).
- **Rigorous physical validation:** Benchmarking trained potentials against held-out DFT energies and atomic forces, experimental lattice parameters, and multi-nanosecond transport convergence criteria before production deployment.

{% include figure.liquid path="assets/img/research/mlip-training-study.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Parametric study of MLIP neural-network training showing energy and force RMSE convergence across activation functions (tanh vs. sigmoid), validation ratios, and learning rates." caption="Parametric study of MLIP neural-network training showing energy and force RMSE convergence across activation functions (tanh vs. sigmoid), validation ratios, and learning rates." %}

## Programming, data analysis & HPC

- **Scientific computing & scripting:** **Python** and **MATLAB** for trajectory post-processing, statistical mechanics, correlation function fitting, orientation/density heatmaps, and automated data pipelines.
- **High-performance computing:** Managing parallelized DFT, MLIP training, and MD/MC production workflows on **Linux** High-Performance Computing Clusters (**HPCC**).
- **Quantitative & statistical modeling:** Time-series correlation analysis, nonlinear regression, neural-network validation, and foundational training in stochastic processes, Brownian motion, and Monte Carlo methods.

## Experimental & laboratory characterization

- **Electrochemical testing:** Chronoamperometry (CA), Chronopotentiometry (CP), Cyclic Voltammetry (CV), and Potentiostatic Electrochemical Impedance Spectroscopy (PEIS).
- **Structural, thermal & mechanical analysis:** Scanning Electron Microscopy (SEM), X-Ray Diffraction (XRD), Differential Scanning Calorimetry (DSC), Thermogravimetric Analysis (TGA), and mechanical testing (tensile, hardness, fracture).
- **Materials processing:** Fused Deposition Modeling (FDM) 3D printing, polymer nanocomposite ink formulation, microwave plasma surface treatment, and wet-chemistry sample preparation (rotary evaporation, GC-MS residue analysis).
