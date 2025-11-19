---
title: About
permalink: /about/
---

{% assign about = site.data.about %}

{% if about.hero %}
<section class="page-hero about-hero">
  <h1 class="page-title">{{ about.hero.title }}</h1>
  <p class="about-summary">{{ about.hero.summary }}</p>
</section>
{% endif %}

{% if about.experience %}
<section class="about-section">
  <div class="section-head">
    <h2>Experience</h2>
  </div>
  <div class="exp-list">
    {% for exp in about.experience %}
    <article class="exp-card">
      <div class="exp-body">
        <h3>{{ exp.title }}</h3>
        <p class="exp-meta">
          {{ exp.organization }}
          {% if exp.dates %} · {{ exp.dates }}{% endif %}
        </p>
        {{ exp.description | markdownify }}
        {% if exp.highlights %}
        <ul class="exp-highlights">
          {% for item in exp.highlights %}
          <li>{{ item }}</li>
          {% endfor %}
        </ul>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}

{% if about.education %}
<section class="about-section">
  <div class="section-head">
    <h2>Education</h2>
    <p>Formal training that shaped my research approach.</p>
  </div>
  <div class="edu-list">
    {% for edu in about.education %}
    <article class="edu-card">
      <h3>{{ edu.degree }}</h3>
      <p class="edu-meta">{{ edu.institution }}{% if edu.location %}, {{ edu.location }}{% endif %}</p>
      <p>{{ edu.summary }}</p>
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}

{% if about.affiliation %}
<section class="about-section">
  <div class="section-head">
    <h2>Affiliation</h2>
    <p>Current lab home and collaborators.</p>
  </div>
  <div class="affiliation about-affiliation">
    <div class="affil-grid">
      <div class="affil-text">
        <h3>{{ about.affiliation.title }}</h3>
        <p>{{ about.affiliation.description }}</p>
        {% if about.affiliation.meta %}
        <p class="affil-meta">{{ about.affiliation.meta }}</p>
        {% endif %}
      </div>
    </div>
  </div>
</section>
{% endif %}

{% if about.volunteer %}
<section class="about-section">
  <div class="section-head">
    <h2>Volunteer Activities</h2>
    <p>Community-focused work that keeps me grounded beyond the lab.</p>
  </div>
  <ul class="vol-list">
    {% for item in about.volunteer %}
    <li>
      <strong>{{ item.title }}</strong>
      <p>{{ item.summary }}</p>
    </li>
    {% endfor %}
  </ul>
</section>
{% endif %}
