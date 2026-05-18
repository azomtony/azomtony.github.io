---
title: Software/Workflow
permalink: /software-workflow/
wide: true
---

{% assign projects = site.data.projects | where: "type", "Software / Workflow" %}

<section class="page-hero">
  <h1 class="page-title">Software/Workflow</h1>
</section>

<section class="project-section">
  <div class="software-grid">
    {% for project in projects %}
    <article class="software-card">
      {% if project.thumbnail %}
      <div class="software-thumb">
        <img src="{{ project.thumbnail | relative_url }}" alt="Thumbnail for {{ project.name | default: project.title }}">
      </div>
      {% endif %}
      <div class="software-body">
        <h3>{{ project.name | default: project.title }}</h3>
        <p>{{ project.description | default: project.summary }}</p>
        {% assign keywords = project.keywords | default: project.methods %}
        {% if keywords %}
        <div class="tag-row">
          {% for keyword in keywords %}
          <span>{{ keyword }}</span>
          {% endfor %}
        </div>
        {% endif %}
        {% if project.github or project.links %}
        <div class="project-links">
          {% if project.github %}
          <a href="{{ project.github }}" target="_blank" rel="noopener">GitHub</a>
          {% endif %}
          {% if project.links %}
          {% for link in project.links %}
          <a href="{{ link.url }}" {% if link.url contains 'http' %}target="_blank" rel="noopener"{% endif %}>{{ link.label }}</a>
          {% endfor %}
          {% endif %}
        </div>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
