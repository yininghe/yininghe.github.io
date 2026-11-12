---
layout: post
title: "Teaching a Neural Network Quantum Physics to Build Better Sodium-Ion Batteries"
date: 2026-11-12 10:00:00-0500
description: "How I trained a neural network on quantum calculations to watch sodium ions hop and shuffle through battery electrodes for storing wind and solar energy."
tags: machine-learning sodium-ion-batteries molecular-dynamics renewable-energy
categories: research
giscus_comments: false # set to true once giscus repo_id/category_id are filled in _config.yml
related_posts: false
---

The wind doesn't always blow when you flip on a light switch, and the sun clocks out every evening just as neighborhoods start cooking dinner. If wind and solar power are going to run the grid reliably, we need affordable batteries that store renewable energy when it is plentiful and release it when it isn't. Sodium, lithium's chemical cousin, is enormously more abundant and much cheaper. That's why I'm excited about **sodium-ion batteries**.

I'm a Materials Science PhD candidate at Michigan State University, working with Prof. Wei Lai. In a study published in _Solid State Ionics_ (with Qian Chen and Prof. Lai), I used machine learning to watch sodium ions hop, squeeze and shuffle through a promising battery electrode, one atom at a time.

## One material, two jobs

A battery shuttles charged atoms, called **ions**, between a positive and a negative electrode, and the two usually need different materials. I studied layered crystals called **sodium nickel titanates** (Na<sub>2x</sub>[Ni<sub>x</sub>Ti<sub>1-x</sub>]O<sub>2</sub>, "SNTL") that can serve as _either_ electrode. That's because they contain nickel, which works at a high voltage, and titanium, which works at a low one. One material doing both jobs could mean simpler, cheaper batteries.

Inside SNTL, metal–oxygen sheets are stacked like pancakes with sodium sandwiched between them. I compared two stackings: **P2**, where sodium sits in prism-shaped cages, and **O3**, where it sits in eight-faced (octahedral) pockets. The question: which gives sodium the easier commute, and why?

## Teaching a neural network to mimic quantum mechanics

Simulating atoms comes with an **efficiency-versus-accuracy dilemma**. The gold standard, **density-functional theory (DFT)**, is a quantum-mechanical method that is very accurate but very expensive. Its cost grows roughly with the cube of the number of atoms, which limits it to boxes a few nanometers wide for a few hundred trillionths of a second. Simple classical **force fields** are fast but often not accurate enough.

So I built a **machine-learning interatomic potential (MLIP)**: a neural network that learns to predict the forces DFT would calculate. Think of a fast apprentice studying under a slow, careful quantum master. I ran short DFT simulations at a scorching 1100 K, which shook the atoms into many arrangements, and collected 5,900 snapshots as training examples. Compared with the classical force field used in our group's earlier work, the network cut force errors in the P2 crystal by 56–70%, depending on the element.

{% include figure.liquid loading="eager" path="assets/img/blog/nib-mlip-force-parity.webp" class="img-fluid rounded z-depth-1" alt="Parity plots of machine-learning versus DFT forces" %}

<div class="caption">Forces predicted by the machine-learning potential (vertical axis) against quantum-mechanical DFT forces (horizontal axis) for each element in the P2 (top) and O3 (bottom) crystals. Points on the diagonal mean the network got it right.</div>

With the trained network, I simulated boxes four times larger for 4 to 6 nanoseconds, hundreds to a thousand times longer than the 6-picosecond quantum runs.

## Doorways, detours and a traffic map

Those long simulations showed that sodium traffic is two-dimensional: the ions roam within the planes between sheets, and their movement up or down through the sheets is negligible. Maps of where the sodium ions spend their time made their hopping routes visible.

The diffusion, conductivity and energy barriers I calculated agreed well with experimental data, and **P2 beat O3**: sodium wandered faster, charge flowed better, and the energy barrier for diffusion was lower (0.36 eV in P2 versus 0.43 eV in O3). Why? Picture squeezing through a doorway with an armful of groceries:

- **Bigger doorways.** In P2, the window sodium squeezes through is a rectangle of four oxygen atoms. In O3 it's a triangle of three. P2's window is about 112% larger by area.
- **More headroom.** The layers sit farther apart in P2 (about 3.46 Å versus 3.23 Å; an ångström is a ten-billionth of a meter).
- **Shorter waits.** At 800 K, sodium in P2 waits about 9 picoseconds between hops. In O3 it waits about 313.

There was a surprise in O3, too. Most earlier studies described sodium taking only a "curved" detour through a small side pocket. My simulations showed, for the first time in an O3-type structure, that sodium can also take a direct **"straight jump."** Which route it takes depends on the neighbors: with only one empty seat nearby, pushback from surrounding sodium sends the traveler straight across; with two or more, it curves through the side pocket.

Finally, sodium ions rarely travel alone. A measure called the **Haven ratio**, which compares how individual ions wander with how net charge flows, came out well below 1, the fingerprint of **cooperative motion**: several ions shuffle forward together, like a crowd edging through a gate.

## Why it matters

Grid-scale storage of wind and solar energy needs battery materials that are cheap and move ions quickly. By teaching a neural network quantum physics, I could simulate sodium-ion electrodes far longer than quantum methods allow while staying close to quantum accuracy. That explains, atom by atom, why one crystal design beats another. This kind of machine-learning simulation is a fast and accurate "microscope" for designing the next generation of energy-storage materials.

_Supported by the National Science Foundation (CAREER grant DMR-1554315) and computing resources at Michigan State University's HPCC/ICER._

**Read the paper:** Y. He, Q. Chen, W. Lai, _Solid State Ionics_ 399 (2023) 116298, [https://doi.org/10.1016/j.ssi.2023.116298](https://doi.org/10.1016/j.ssi.2023.116298)
