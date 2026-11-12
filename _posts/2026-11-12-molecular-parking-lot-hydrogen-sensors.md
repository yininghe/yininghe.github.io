---
layout: post
title: "A Molecular Parking Lot on Platinum: How Simulations Help Build Better Hydrogen Leak Sensors"
date: 2026-11-12 11:00:00-0500
description: "Atom-by-atom simulations, checked against my collaborators' experiments, explain why one ionic liquid makes a more sensitive hydrogen leak sensor."
tags: hydrogen-energy hydrogen-sensors ionic-liquids molecular-dynamics
categories: research
giscus_comments: false # set to true once giscus repo_id/category_id are filled in _config.yml
related_posts: false
---

Hydrogen is one of the most promising clean fuels around. Pound for pound it packs a huge amount of energy. There's one catch: it is very easy to ignite, and a leak that reaches just 4% hydrogen in air can explode. Safety is one of the main things holding back large-scale hydrogen energy, so we need sensitive, reliable leak detectors.

I'm a Materials Science PhD candidate at Michigan State University, working with Prof. Wei Lai. I simulate, atom by atom, what happens inside electrochemical hydrogen sensors. In two studies with experimental collaborators in Prof. Xiangqun Zeng's group (University of Missouri), I did the simulation work.

## Liquid salts and a sensor puzzle

In these sensors, leaking hydrogen gas (H<sub>2</sub>) dissolves into the sensor's liquid electrolyte and must reach a **platinum (Pt) electrode**. Platinum is a **catalyst** (a material that speeds up a reaction) and splits the hydrogen into protons and electrons, producing a current that grows with the amount of hydrogen.

The liquid is an **ionic liquid**: a salt made of bulky positive ions (**cations**) and negative ions (**anions**) that stays liquid near room temperature and barely evaporates. Two popular choices share the same anion but differ in their cation. **[Bmim]<sup>+</sup>** has a flat ring of atoms; **[Bmpy]<sup>+</sup>** has a ring that isn't flat.

Here was the puzzle. In the bulk liquid, ions move faster and conduct better in [Bmim][NTf<sub>2</sub>]. Yet hydrogen-sensing experiments by Prof. Xiangqun Zeng's group showed that [Bmpy][NTf<sub>2</sub>] sensors are _more_ sensitive. Experiments can't easily watch gas molecules cross from the liquid to the metal, so I built a virtual sensor to do it.

## Zooming in on the electrode's front door

Using **molecular dynamics**, a method that follows how thousands of atoms push, pull and jostle over time, I placed each liquid between two platinum electrodes. First I checked that the virtual liquids behave like real ones: the simulated ion movement and conductivity matched published measurements. As in experiments, the ions moved faster in bulk [Bmim][NTf<sub>2</sub>], and so did dissolved hydrogen. Hydrogen also moved about a hundred times faster than the ions around it. So speed through the bulk liquid couldn't explain why [Bmpy] wins.

The real action happens right next to the charged metal, in the **electric double layer (EDL)**, where ions line up in layers to balance the electrode's charge. The simulations showed a first layer within about 6 Å of the platinum (an ångström is a ten-billionth of a meter), a second layer out to about 16 Å, and then the bulk liquid.

{% include figure.liquid loading="eager" path="assets/img/blog/h2-simulation-cell.webp" class="img-fluid rounded z-depth-1" alt="Schematic of the simulation box with Pt electrodes and double layers" %}

<div class="caption">The simulated sensor: ionic liquid (red cation rings, green anions) between a negative and a positive platinum electrode. The liquid forms a first double layer (0–6 Å from the metal), a second double layer (6–16 Å) and a randomly oriented bulk region in the middle.</div>

In that first layer next to the sensing electrode, the two liquids behaved like two very different parking lots:

- **Flat tiles versus scattered blocks.** The flat [Bmim] rings mostly lay flat on the platinum, like paving tiles that can block hydrogen's way. The [Bmpy] rings were oriented in a more scattered way, leaving more pathways for hydrogen to reach the surface.
- **A little more hydrogen.** [Bmpy][NTf<sub>2</sub>] dissolves slightly more hydrogen, and hydrogen was more likely to be found right inside the first layer of the sensing electrode. Hydrogen dissolves only in tiny amounts, so even a small boost may matter.

So even though [Bmim] is faster in the bulk, these two effects at the electrode help explain why [Bmpy][NTf<sub>2</sub>] makes the more sensitive hydrogen sensor. The study was selected as a 2025 _PCCP_ HOT Article.

## Rethinking the textbook layer cake

In a follow-up collaboration led by Kamal Arora, I simulated [Bmpy][NTf<sub>2</sub>] at voltages like those used in real sensors. The textbook picture next to a positive electrode is a neat layer cake: a row of only negative ions, then a row of only positive ones. Instead, the simulations showed negative and positive ions sitting _together_, mixed in a single **compact layer** on the platinum. Beyond it lies a more disordered **diffuse layer**, about 14 Å thick, that acts as a buffer before the bulk.

## Simulation and experiment, hand in hand

Electrochemists often describe an interface as an **equivalent circuit**, a diagram of resistors and capacitors. Many circuits can fit the same data, so one with physically meaningful parts is more useful. From the simulated atomic picture, the team built a circuit where each element matches a real region: the bulk liquid, the diffuse layer, and the compact layer at the platinum.

My experimental collaborators used that circuit to analyze their measurements, which also showed two distinct layers. The **capacitance** I calculated (how much charge the interface stores per volt) changed little over the voltage range studied, which was qualitatively consistent with their experimental trend.

## Why it matters

These studies show that bulk liquid properties tell only half the story. Whether hydrogen reaches the catalyst depends on how ions park, tilt and mix within a nanometer or so of the platinum. Pairing simulations with experiments turns that hidden world into practical guidance for designing better sensors. The simulation input files are on [GitHub](https://github.com/yininghe/Simulation_Compare_2ILs).

_The PCCP study was supported by the U.S. Department of Energy's Hydrogen and Fuel Cell Technologies Office._

**Read the papers:**

- Y. He, T. Glossmann, X. Zeng, W. Lai, _Phys. Chem. Chem. Phys._ 27 (2025) 10962–10978 (open access), [https://doi.org/10.1039/d5cp00642b](https://doi.org/10.1039/d5cp00642b)
- K. Arora, Y. He, W. Lai, X. Zeng, _Electrochimica Acta_ 560 (2026) 148664, [https://doi.org/10.1016/j.electacta.2026.148664](https://doi.org/10.1016/j.electacta.2026.148664)
