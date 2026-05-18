---
title: Experience
permalink: /experience/
wide: true
---

{% assign about = site.data.about %}

<section class="page-hero">
  <h1 class="page-title">Experience</h1>
</section>

{% if about.experience %}
<section class="about-section">
  <div class="section-head">
    <h2>Professional Experience</h2>
  </div>
  <div class="experience-grid">
    {% for exp in about.experience %}
    <article class="experience-card">
      <div class="experience-logo">
        {% if exp.logo %}
        <img src="{{ exp.logo | relative_url }}" alt="{{ exp.organization }} logo">
        {% elsif exp.logo_text %}
        <span>{{ exp.logo_text }}</span>
        {% else %}
        <span>{{ exp.organization | slice: 0, 2 }}</span>
        {% endif %}
      </div>
      <div class="experience-text">
        <h3>{{ exp.title }}</h3>
        {% if exp.department %}
        <p class="experience-dept">{{ exp.department }}</p>
        {% endif %}
        <p class="experience-org">{{ exp.organization }}</p>
        {% if exp.mentor %}
        <p class="experience-mentor">Mentor: {{ exp.mentor }}</p>
        {% endif %}
        {% if exp.dates %}
        <p class="experience-dates">{{ exp.dates }}</p>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}

{% if about.workshops %}
<section class="about-section">
  <div class="section-head">
    <h2>Workshops</h2>
  </div>
  <div class="experience-grid">
    {% for item in about.workshops %}
    <article class="experience-card">
      <div class="experience-logo">
        {% if item.logo %}
        <img src="{{ item.logo | relative_url }}" alt="{{ item.organization | default: item.event }} logo">
        {% elsif item.logo_text %}
        <span>{{ item.logo_text }}</span>
        {% else %}
        <span>{{ item.organization | default: item.event | slice: 0, 2 }}</span>
        {% endif %}
      </div>
      <div class="experience-text">
        <h3>{{ item.role | default: item.title }}</h3>
        {% if item.title and item.role %}
        <p class="experience-dept">{{ item.title }}</p>
        {% elsif item.department %}
        <p class="experience-dept">{{ item.department }}</p>
        {% endif %}
        {% if item.organization or item.event %}
        <p class="experience-org">{{ item.organization | default: item.event }}</p>
        {% endif %}
        {% if item.mentor %}
        <p class="experience-mentor">Mentor: {{ item.mentor }}</p>
        {% endif %}
        {% if item.dates or item.date %}
        <p class="experience-dates">{{ item.dates | default: item.date }}</p>
        {% endif %}
        {% if item.github %}
        <a class="experience-link" href="{{ item.github }}" target="_blank" rel="noopener">GitHub</a>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}
