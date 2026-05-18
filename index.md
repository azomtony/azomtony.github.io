---
title: Home
wide: true
---

<section class="home-hero">
  {% assign current = site.data.about.current_position %}
  <div class="home-heading">
    <h1>Golam Azom, Ph.D.</h1>
  </div>

  <div class="home-intro-row">
    <div class="home-copy">
      <div class="current-card">
        <div class="current-logo" aria-hidden="true">
          {% if current.logo %}
          <img src="{{ current.logo | relative_url }}" alt="">
          {% else %}
          <span>{{ current.logo_text }}</span>
          {% endif %}
        </div>
        <div class="current-details">
          <h2>{{ current.position }}</h2>
          <p class="current-group">{{ current.lab_group }}</p>
          <p class="current-org">{{ current.organization }}</p>
          <a class="current-email" href="mailto:{{ current.email | default: site.data.about.contact.email }}">{{ current.email | default: site.data.about.contact.email }}</a>
        </div>
      </div>
    </div>

    <div class="home-portrait">
      <img src="{{ '/assets/images/profile.jpg' | relative_url }}" alt="Golam Azom">
    </div>
  </div>

  <div class="home-divider"></div>

  <div class="home-intro-text">
    {% for paragraph in current.intro %}
    <p class="home-summary">{{ paragraph }}</p>
    {% endfor %}
  </div>
</section>

<div class="home-section-separator" aria-hidden="true"></div>

<section class="expertise-band" aria-label="Expertise areas">
  {% for domain in site.data.domains %}
  <span class="expertise-term">
    <span class="expertise-name">{{ domain.title }}</span>
  </span>
  {% endfor %}
</section>

{% if site.data.news %}
<section class="news-section" aria-label="News">
  <div class="section-head">
    <h2>News</h2>
  </div>
  <div class="news-list">
    {% for item in site.data.news limit: 5 %}
    <article class="news-item">
      <time>{{ item.date }}</time>
      {% if item.url %}
      <a href="{{ item.url | relative_url }}">{{ item.text }}</a>
      {% else %}
      <p>{{ item.text }}</p>
      {% endif %}
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}
