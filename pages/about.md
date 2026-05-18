---
title: About
permalink: /about/
wide: true
---

{% assign about = site.data.about %}

{% if about.hero %}
<section class="page-hero about-hero">
  <h1 class="page-title">{{ about.hero.title }}</h1>
  <p class="about-summary">{{ about.hero.summary }}</p>
</section>
{% endif %}

{% if about.contact %}
<div class="contact-bar">
  {% if about.contact.linkedin %}
  <a class="contact-chip" href="{{ about.contact.linkedin }}" target="_blank" rel="noopener" aria-label="LinkedIn">
    <span class="icon">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M4.98 3.5A2.5 2.5 0 0 1 7.5 6a2.5 2.5 0 1 1-2.52-2.5H5zM4 8h3v13H4V8zm6.5 0h2.9v1.8h.04c.4-.76 1.36-1.55 2.8-1.55C19.6 8.25 21 9.7 21 12.3V21h-3v-7.4c0-1.77-.63-2.98-2.2-2.98-1.2 0-1.92.82-2.23 1.6-.12.3-.15.72-.15 1.14V21h-3V8z" fill="currentColor"/></svg>
    </span>
    <span>LinkedIn</span>
  </a>
  {% endif %}
  {% if about.contact.email %}
  <a class="contact-chip" href="mailto:{{ about.contact.email | uri_escape }}" aria-label="Email">
    <span class="icon">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M4 5h16a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V7a2 2 0 0 1 2-2zm0 2v.01L12 13l8-5.99V7H4zm0 2.25V17h16V9.25l-7.4 5.54a1.5 1.5 0 0 1-1.8 0L4 9.25z" fill="currentColor"/></svg>
    </span>
    <span>Email</span>
  </a>
  {% endif %}
  {% if about.contact.github %}
  <a class="contact-chip" href="{{ about.contact.github }}" target="_blank" rel="noopener" aria-label="GitHub">
    <span class="icon">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M12 .5C5.65.5.5 5.64.5 12c0 5.08 3.29 9.39 7.86 10.91.58.1.79-.25.79-.56v-2c-3.2.7-3.88-1.54-3.88-1.54-.52-1.3-1.27-1.65-1.27-1.65-1.04-.7.08-.68.08-.68 1.15.08 1.76 1.18 1.76 1.18 1.02 1.75 2.68 1.24 3.33.95.1-.74.4-1.24.72-1.53-2.55-.29-5.23-1.27-5.23-5.64 0-1.25.45-2.27 1.18-3.07-.12-.29-.51-1.46.11-3.05 0 0 .96-.31 3.15 1.17a10.9 10.9 0 0 1 5.74 0c2.2-1.48 3.15-1.17 3.15-1.17.62 1.59.23 2.76.12 3.05.73.8 1.17 1.82 1.17 3.07 0 4.38-2.69 5.34-5.25 5.63.41.35.77 1.04.77 2.11v3.12c0 .31.21.67.8.56A10.53 10.53 0 0 0 23.5 12C23.5 5.64 18.35.5 12 .5z" fill="currentColor"/></svg>
    </span>
    <span>GitHub</span>
  </a>
{% endif %}
{% if about.downloads and about.downloads.size > 0 %}
  {% for item in about.downloads %}
  <a class="contact-chip" href="{{ item.file | relative_url }}" {% if item.file contains 'http' %}target="_blank" rel="noopener"{% endif %} aria-label="{{ item.label }}">
    <span class="icon">
      <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M6 2h8l5 5v15H6V2zm7 1.8V8h4.2L13 3.8zM8 11v2h8v-2H8zm0 4v2h8v-2H8z" fill="currentColor"/></svg>
    </span>
    <span>{{ item.short_label | default: item.label }}</span>
  </a>
  {% endfor %}
{% endif %}
</div>
{% endif %}

{% if about.education %}
<section class="about-section">
  <div class="section-head">
    <h2>Education</h2>
  </div>
  <div class="edu-list">
    {% for edu in about.education %}
    <article class="edu-card">
      <div class="edu-logo">
        {% if edu.logo %}
        <img src="{{ edu.logo | relative_url }}" alt="{{ edu.institution }} logo">
        {% elsif edu.logo_text %}
        <span>{{ edu.logo_text }}</span>
        {% else %}
        <span>{{ edu.institution | slice: 0, 2 }}</span>
        {% endif %}
      </div>
      <div class="edu-body">
        <h3>{{ edu.degree }}</h3>
        <p class="edu-meta">{{ edu.institution }}{% if edu.location %}, {{ edu.location }}{% endif %}</p>
        {% if edu.year or edu.dates %}
        <p class="edu-year">{{ edu.year | default: edu.dates }}</p>
        {% endif %}
        {% if edu.summary %}
        <p>{{ edu.summary }}</p>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}

{% if about.awards and about.awards.size > 0 %}
<section class="about-section">
  <div class="section-head">
    <h2>Honors & Awards</h2>
  </div>
  <div class="award-list">
    {% for item in about.awards %}
    <article class="award-card">
      <div class="award-logo">
        {% if item.logo %}
        <img src="{{ item.logo | relative_url }}" alt="{{ item.organization | default: item.title }} logo">
        {% elsif item.logo_text %}
        <span>{{ item.logo_text }}</span>
        {% else %}
        <span>{{ item.organization | default: item.title | slice: 0, 2 }}</span>
        {% endif %}
      </div>
      <div class="award-body">
        <h3>{{ item.title }}</h3>
        {% if item.organization %}
        <p class="award-org">{{ item.organization }}</p>
        {% endif %}
        {% if item.date %}
        <p class="award-date">{{ item.date }}</p>
        {% endif %}
        {% if item.summary and item.summary != "" %}
        <p>{{ item.summary }}</p>
        {% endif %}
        {% if item.url %}
        <a class="award-preview{% unless item.preview_image %} no-image{% endunless %}" href="{{ item.url }}" {% if item.url contains 'http' %}target="_blank" rel="noopener"{% endif %}>
          {% if item.preview_image %}
          <span class="award-preview-image">
            <img src="{{ item.preview_image | relative_url }}" alt="">
          </span>
          {% endif %}
          <span class="award-preview-text">
            <strong>{{ item.preview_title | default: "Read the article" }}</strong>
            {% if item.preview_text %}
            <em>{{ item.preview_text }}</em>
            {% endif %}
          </span>
        </a>
        {% endif %}
      </div>
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

{% if about.certifications and about.certifications.size > 0 %}
<section class="about-section">
  <div class="section-head">
    <h2>Certifications</h2>
  </div>
  <div class="award-list">
    {% for item in about.certifications %}
    <article class="award-card">
      <div class="award-logo">
        {% if item.logo %}
        <img src="{{ item.logo | relative_url }}" alt="{{ item.issuer | default: item.title }} logo">
        {% elsif item.logo_text %}
        <span>{{ item.logo_text }}</span>
        {% else %}
        <span>{{ item.issuer | default: item.title | slice: 0, 2 }}</span>
        {% endif %}
      </div>
      <div class="award-body">
        <h3>{{ item.title }}</h3>
        {% if item.issuer %}
        <p class="award-org">{{ item.issuer }}</p>
        {% endif %}
        {% if item.date %}
        <p class="award-date">{{ item.date }}</p>
        {% endif %}
        {% if item.summary and item.summary != "" %}
        <p>{{ item.summary }}</p>
        {% endif %}
        {% if item.url %}
        <a class="text-link certification-link" href="{{ item.url }}" {% if item.url contains 'http' %}target="_blank" rel="noopener"{% endif %}>View credential</a>
        {% endif %}
      </div>
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}

{% if about.volunteer %}
<section class="about-section">
  <div class="section-head">
    <h2>Volunteer Activities</h2>
  </div>
  <ul class="vol-list">
    {% for item in about.volunteer %}
    <li class="vol-card{% if item.images or item.image %} has-image{% endif %}">
      <div class="vol-main{% unless item.logo or item.logo_text %} no-logo{% endunless %}">
        {% if item.logo or item.logo_text %}
        <div class="vol-media">
          {% if item.logo %}
          <img src="{{ item.logo | relative_url }}" alt="{{ item.organization | default: item.title }} logo">
          {% elsif item.logo_text %}
          <span>{{ item.logo_text }}</span>
          {% endif %}
        </div>
        {% endif %}
        <div class="vol-body">
          {% if item.role %}
          <p class="vol-role">{{ item.role }}</p>
          {% endif %}
          <h3>{{ item.title }}</h3>
          {% if item.organization or item.location or item.date %}
          <p class="vol-meta">
          {% if item.organization %}{{ item.organization }}{% endif %}
            {% if item.location %}{% if item.organization %}, {% endif %}{{ item.location }}{% endif %}
            {% if item.date %}{% if item.organization or item.location %}, {% endif %}{{ item.date }}{% endif %}
          </p>
          {% endif %}
          {% if item.summary %}
          <p>{{ item.summary }}</p>
          {% endif %}
          {% if item.url %}
          <a class="text-link volunteer-link" href="{{ item.url }}" {% if item.url contains 'http' %}target="_blank" rel="noopener"{% endif %}>View activity</a>
          {% endif %}
        </div>
      </div>

      {% if item.images %}
      <div class="vol-gallery count-{{ item.images.size }}">
        {% for image in item.images limit: 3 %}
        <div class="vol-media vol-photo">
          <img src="{{ image | relative_url }}" alt="{{ item.title }} event photo {{ forloop.index }}">
        </div>
        {% endfor %}
      </div>
      {% elsif item.image %}
      <div class="vol-gallery count-1">
        <div class="vol-media vol-photo">
          <img src="{{ item.image | relative_url }}" alt="{{ item.title }} event photo">
        </div>
      </div>
      {% endif %}
    </li>
    {% endfor %}
  </ul>
</section>
{% endif %}
