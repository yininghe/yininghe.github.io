---
layout: page
title: "Machine-learning interatomic potentials for Na-ion battery electrodes"
description: "Developing near-DFT-accuracy neural-network interatomic potentials to resolve Na-ion diffusion mechanisms and conductivity in layered P2- and O3-type battery electrodes across nanosecond timescales."
img: assets/img/research/nib-na-density-map.webp
importance: 1
---

## Overview

Sodium-ion batteries (SIBs) offer a cost-effective, resource-abundant alternative to lithium-ion systems for grid-scale renewable energy storage and electric vehicle charging infrastructure. Layered transition-metal oxides of the form Na<sub>2x</sub>[Ni<sub>x</sub>Ti<sub>1−x</sub>]O<sub>2</sub> (SNTL) are particularly attractive because they function as bi-functional electrodes capable of serving as either the positive or negative electrode, simplifying cell design and lowering manufacturing costs. However, optimizing rate performance requires a quantitative understanding of how local crystal stacking—specifically P2-type (two transition-metal octahedral layers with Na in prismatic sites) versus O3-type (three transition-metal octahedral layers with Na in octahedral sites)—governs sodium self-diffusion and ionic conduction.

<div class="row justify-content-center align-items-center">
  <div class="col-12 col-md-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/nib-o3-structure.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Crystal structure of O3-type Na2x[NixTi1-x]O2 (SNTL): three transition-metal octahedral layers, Na in octahedral sites." caption="<b>O3-type</b> SNTL: three transition-metal octahedral layers with Na in octahedral sites." %}
  </div>
  <div class="col-12 col-md-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/nib-p2-structure.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Crystal structure of P2-type Na2x[NixTi1-x]O2 (SNTL): two transition-metal octahedral layers, Na in prismatic sites." caption="<b>P2-type</b> SNTL: two transition-metal octahedral layers with Na in prismatic sites." %}
  </div>
  <div class="col-12 col-md-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/nib-p2-topview.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Top view along the c-axis of the layered SNTL structure showing the in-plane sodium transport network." caption="Top view along the c-axis showing the in-plane Na transport network." %}
  </div>
</div>

## Approach

First-principles density functional theory molecular dynamics (DFT-MD) accurately captures interatomic forces in complex transition-metal oxides but is computationally restricted to small supercells and picosecond trajectories, resulting in poorly converged transport coefficients. Classical empirical potentials scale to larger systems but lack the fidelity needed to describe variable transition-metal environments.

To bridge this gap, we trained deep neural-network machine-learning interatomic potentials (MLIPs) on DFT reference data (energies, atomic forces, and virial tensors computed with VASP). Local atomic environments were encoded into symmetry-preserving descriptors (exploring both Atom-Centered Symmetry Functions via Simple-NN and local-coordinate transformations via DeePMD-kit), and systematic hyperparameter optimization was performed across learning rates, validation split ratios, activation functions (tanh vs. sigmoid), training iterations, and network architectures before deploying the validated potentials in multi-nanosecond LAMMPS molecular dynamics simulations.

{% include figure.liquid path="assets/img/research/nib-mlip-force-parity.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Parity plot comparing MLIP-predicted atomic forces against DFT reference forces, demonstrating substantial error reduction across Na, Ti, Ni, and O species." caption="Parity plot comparing MLIP-predicted atomic forces against DFT reference forces, demonstrating substantial error reduction across Na, Ti, Ni, and O species." %}

## Key results

- **Near-DFT force accuracy and structural fidelity:** Compared with the classical interatomic potential used in prior studies, the trained MLIP reduced force root-mean-square error (F-RMSE) by **69.8% for Na**, **66.4% for Ti**, **56.1% for Ni**, and **59.0% for O**, while reproducing experimental lattice parameters.
- **Converged transport statistics:** Convergence testing with the Einstein-Helfand formalism established that **3 ns** of MLIP-MD simulation is sufficient to obtain well-converged sodium self-diffusivity (<i>D</i>) and ionic conductivity (σ).
- **Diffusivity and activation barriers:** Arrhenius analyses of MLIP-MD trajectories yielded Na diffusion activation energies of **<i>E</i><sub>a</sub> = 0.36 eV for P2-SNTL** and **<i>E</i><sub>a</sub> = 0.43 eV for O3-SNTL**, quantitatively accounting for the higher Na self-diffusivity observed in the P2 phase (<i>D</i>(P2) &gt; <i>D</i>(O3)).
- **Ionic conductivity and correlation effects:** From the computed Nernst-Einstein and collective conductivities, the **Haven ratio (<i>H</i><sub>R</sub>)** was determined to be **~0.42–0.47 in P2-SNTL** and **~0.22–0.31 in O3-SNTL**, quantifying the stronger correlated ion motion in the O3 lattice.
- **Atomistic jump-diffusion mechanisms:** Three-dimensional nuclear density maps and (001)-plane slices resolved the microscopic Na migration pathways. Fitting analytical jump-diffusion models to the incoherent intermediate scattering function demonstrated that sodium transport follows the **Singwi-Sjölander (SS) model in P2-SNTL** and the **Chudley-Elliott (CE) model in O3-SNTL**.

<div class="row justify-content-center align-items-center">
  <div class="col-12 col-md-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/nib-diffusivity-arrhenius.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Arrhenius plots of Na self-diffusivity in P2- and O3-SNTL (Ea = 0.36 eV for P2, 0.43 eV for O3)." caption="Arrhenius plots of Na self-diffusivity: <i>E</i><sub>a</sub> = 0.36 eV (P2) and 0.43 eV (O3)." %}
  </div>
  <div class="col-12 col-md-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/nib-ionic-conductivity.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Temperature-dependent Na ionic conductivity in P2- and O3-SNTL." caption="Temperature-dependent Na ionic conductivity." %}
  </div>
  <div class="col-12 col-md-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/nib-haven-ratio.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Haven ratio versus temperature for P2- and O3-SNTL, quantifying correlated ion motion." caption="Haven ratio <i>H</i><sub>R</sub>, quantifying correlated Na motion." %}
  </div>
</div>

<div class="row justify-content-center">
  <div class="col-12 col-md-8">
    {% include figure.liquid path="assets/img/research/nib-na-density-map.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Nuclear density maps in 3D space and 2D (001) slices revealing continuous in-plane Na jump diffusion pathways." caption="Nuclear density maps in 3D space and 2D (001) slices revealing continuous in-plane Na jump diffusion pathways." %}
  </div>
</div>

{% include figure.liquid path="assets/img/research/nib-jump-diffusion-fits.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Jump-diffusion model fits to the incoherent intermediate scattering function for P2-SNTL (SS model) and O3-SNTL (CE model)." caption="Jump-diffusion model fits to the incoherent intermediate scattering function for P2-SNTL (SS model) and O3-SNTL (CE model)." %}

## Impact

This work establishes a transferable workflow for training and validating MLIPs in disordered multi-component battery oxides and provides direct mechanistic explanations for why P2-structured Na<sub>2x</sub>[Ni<sub>x</sub>Ti<sub>1−x</sub>]O<sub>2</sub> exhibits superior sodium mobility over its O3 counterpart. The resulting structure-transport relationships serve as quantitative design rules to guide experimental phase selection and composition tuning in next-generation sodium-ion batteries.

## Methods & tools

- **First-principles calculations:** DFT and ab initio MD via VASP
- **Machine-learning potentials:** DeePMD-kit, Simple-NN (ACSF descriptors), neural-network hyperparameter tuning and cross-validation
- **Atomistic simulation:** Large-scale MD via LAMMPS on high-performance computing clusters (HPCC)
- **Transport & statistical analysis:** Einstein-Helfand diffusivity/conductivity, Nernst-Einstein relation, Haven ratio, nuclear density mapping, incoherent intermediate scattering function fitting (Python, MATLAB)

## Publication

- **He, Y.**, Chen, Q., & Lai, W. (2023). Computational study of Na diffusion and conduction in P2- and O3-Na<sub>2x</sub>[Ni<sub>x</sub>Ti<sub>1−x</sub>]O<sub>2</sub> materials with machine-learning interatomic potentials. *Solid State Ionics*, 399, 116298. [DOI: 10.1016/j.ssi.2023.116298](https://doi.org/10.1016/j.ssi.2023.116298)
