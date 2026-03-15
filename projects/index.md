---
title: Projects
# To add to site nav, uncomment and adjust the block below:
# nav:
#   order: 2
#   tooltip: Research projects
---

# {% include icon.html icon="fa-solid fa-flask" %}Projects

We design tools, systems, and studies to make data more accessible and meaningful across diverse communities.

{% include section.html %}

## Active Projects

<div class="project-grid">
{% include list.html component="project-card" data="projects" filter="status == 'active'" %}
</div>

{% include section.html %}

## Completed Projects

<div class="project-grid" data-size="small">
{% include list.html component="project-card" data="projects" filter="status == 'completed'" %}
</div>
