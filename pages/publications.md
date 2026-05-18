---
title: Publications
permalink: /publications/
wide: true
---

{% assign pubs = site.data.publications %}

<section class="page-hero">
  <h1 class="page-title">Publications</h1>
  <div class="publication-profiles" aria-label="Publication profiles">
    {% for profile in site.data.publication_profiles %}
    <a class="profile-link {{ profile.key }}" href="{{ profile.url }}" target="_blank" rel="noopener">
      {% if profile.icon %}
      <img class="profile-logo" src="{{ profile.icon | relative_url }}" alt="" aria-hidden="true">
      {% endif %}
      <span>{{ profile.label }}</span>
    </a>
    {% endfor %}
  </div>
</section>

{% assign groups = pubs | group_by: "year" | sort: "name" | reverse %}
{% for g in groups %}
  <div class="pub-year-row">
    <h2 class="pub-year">{{ g.name }}</h2>
    <span>{{ g.items | size }} publication{% if g.items.size != 1 %}s{% endif %}</span>
  </div>
  <div class="pub-list">
    {% for p in g.items %}
      <article id="{% if p.id %}{{ p.id }}{% else %}{{ p.title | slugify }}{% endif %}" class="pub-card{% if p.toc %} has-toc{% else %} no-toc{% endif %}">
        {% if p.toc %}
        <div class="pub-thumb">
          <img src="{{ p.toc | relative_url }}" alt="TOC figure for {{ p.title }}">
        </div>
        {% endif %}
        <div class="pub-body">
          <div class="pub-meta">
            {% if p.venue %}<span class="venue">{{ p.venue }}</span>{% endif %}
            {% if p.type %}<span class="tag">{{ p.type }}</span>{% endif %}
            {% if p.status %}<span class="tag status">{{ p.status }}</span>{% endif %}
          </div>
          <h3 class="title">{{ p.title }}</h3>
          <div class="authors">{{ p.authors | markdownify }}</div>

          {% if p.abstract %}
          <details class="abs">
            <summary>Abstract</summary>
            <p>{{ p.abstract }}</p>
          </details>
          {% endif %}

          {% if p.doi %}
          <div class="links">
            <a href="https://doi.org/{{ p.doi }}">DOI</a>
          </div>
          {% endif %}
        </div>
      </article>
    {% endfor %}
  </div>
{% endfor %}
