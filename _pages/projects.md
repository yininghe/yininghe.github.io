---
layout: page
title: Research
permalink: /research/
description: Machine-learning interatomic potentials for battery electrodes, molecular simulation of ionic-liquid gas sensors, and the methods behind them.
nav: true
nav_order: 2
---

<!-- _pages/projects.md: one vertical card per page in _projects/, ordered by `importance`.
     Cards are written inline (not via the gem's projects include) so the thumbnail can be a fixed-height crop.
     A project without `img` gets a green gradient placeholder of the same height. -->
<div class="projects">
  {% assign sorted_projects = site.projects | sort: "importance" %}
  <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
    <div class="col mb-4">
      <a href="{{ project.url | relative_url }}" style="text-decoration: none;">
        <div class="card h-100 hoverable overflow-hidden">
          {% if project.img %}
          <img src="{{ project.img | relative_url }}" alt="{{ project.title | escape }}" loading="lazy" style="height: 200px; width: 100%; object-fit: cover;">
          {% else %}
          <div style="height: 200px; background: linear-gradient(135deg, #18453b 0%, #4fb38f 100%);" role="img" aria-label="{{ project.title | escape }}"></div>
          {% endif %}
          <div class="card-body">
            <h2 class="card-title" style="font-size: 1.35rem; line-height: 1.3;">{{ project.title }}</h2>
            <p class="card-text">{{ project.description }}</p>
          </div>
        </div>
      </a>
    </div>
    {% endfor %}
  </div>
</div>
