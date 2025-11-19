---
title: Skills
permalink: /skills/
---

{% assign skills = site.data.skills %}

{% if skills.hero %}
<section class="page-hero skills-hero">
  <h1 class="page-title">{{ skills.hero.title }}</h1>
  <p class="skills-intro">{{ skills.hero.intro }}</p>
</section>
{% endif %}

{% if skills.cloud_sections %}
  {% for section in skills.cloud_sections %}
  <section class="skills-section">
    <div class="section-head">
      <h2>{{ section.title }}</h2>
      {% if section.subtitle %}
      <p>{{ section.subtitle }}</p>
      {% endif %}
    </div>
    <div class="skill-cloud" aria-label="{{ section.title }} emphasis cloud">
      {% for tag in section.tags %}
      <span class="skill-pill weight-{{ tag.weight | default: 2 }}">{{ tag.label }}</span>
      {% endfor %}
    </div>
  </section>
  {% endfor %}
{% endif %}
