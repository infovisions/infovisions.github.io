---
title: Projects
# To add to site nav, uncomment and adjust the block below:
nav:
  order: 2
  icon: fa-solid fa-flask
  tooltip: Research projects
---

# {% include icon.html icon="fa-solid fa-flask" %}Projects
{% capture content %}**Warning** This page is under construction. While we are currently in the process of adding projects we're involved in, the listing below does not fully reflect our group's activity {% endcapture %}
{% include alert.html type="warning" content=content %}

We design tools, systems, and studies to make data more accessible and meaningful across diverse communities.


{% include section.html size="wide" %}

## What are we working on?

{% assign active_projects = site.projects | where: "status", "active" %}
<div class="project-grid">
{% for project in active_projects %}
  {% assign card_desc = project.short_description | default: project.excerpt %}
  {% include project-card.html
    title=project.title
    subtitle=project.subtitle
    description=card_desc
    image=project.image
    link=project.url
    lead=project.lead
    pi=project.pi
  %}
{% endfor %}
</div>

{% include section.html size="wide" %}

<!-- ## Completed Projects -->

{% assign completed_projects = site.projects | where: "status", "completed" %}
<div class="project-grid" data-size="small">
{% for project in completed_projects %}
  {% assign card_desc = project.short_description | default: project.excerpt %}
  {% include project-card.html
    title=project.title
    subtitle=project.subtitle
    description=card_desc
    image=project.image
    link=project.url
    lead=project.lead
    pi=project.pi
  %}
{% endfor %}
</div>
