---
title: Talks & Posters
permalink: /talks-posters/
wide: true
---

{% assign about = site.data.about %}

<section class="page-hero">
  <h1 class="page-title">Talks & Posters</h1>
</section>

{% if about.scientific_talks and about.scientific_talks.size > 0 %}
<section class="about-section">
  <div class="section-head">
    <h2>Scientific Talks</h2>
  </div>
  <div class="experience-grid">
    {% for item in about.scientific_talks %}
    <article class="experience-card talk-poster-card">
      <div class="experience-logo">
        {% if item.logo %}
        <img src="{{ item.logo | relative_url }}" alt="{{ item.conference }} logo">
        {% elsif item.logo_text %}
        <span>{{ item.logo_text }}</span>
        {% else %}
        <span>{{ item.conference | slice: 0, 2 }}</span>
        {% endif %}
      </div>
      <div class="experience-text">
        <h3>{{ item.title }}</h3>
        {% if item.conference %}
        <p class="experience-dept">{{ item.conference }}</p>
        {% endif %}
        {% if item.place %}
        <p class="experience-org">{{ item.place }}</p>
        {% endif %}
        {% if item.date or item.dates %}
        <p class="experience-dates">{{ item.date | default: item.dates }}</p>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}

{% if about.poster_presentations and about.poster_presentations.size > 0 %}
<section class="about-section">
  <div class="section-head">
    <h2>Poster Presentations</h2>
  </div>
  <div class="experience-grid">
    {% for item in about.poster_presentations %}
    <article class="experience-card talk-poster-card">
      <div class="experience-logo">
        {% if item.logo %}
        <img src="{{ item.logo | relative_url }}" alt="{{ item.conference }} logo">
        {% elsif item.logo_text %}
        <span>{{ item.logo_text }}</span>
        {% else %}
        <span>{{ item.conference | slice: 0, 2 }}</span>
        {% endif %}
      </div>
      <div class="experience-text">
        <h3>{{ item.title }}</h3>
        {% if item.conference %}
        <p class="experience-dept">{{ item.conference }}</p>
        {% endif %}
        {% if item.place %}
        <p class="experience-org">{{ item.place }}</p>
        {% endif %}
        {% if item.date or item.dates %}
        <p class="experience-dates">{{ item.date | default: item.dates }}</p>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}
