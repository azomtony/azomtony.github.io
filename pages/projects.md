---
title: Research Projects
permalink: /projects/
wide: true
---

{% assign projects = site.data.projects | where: "type", "Research" %}
{% assign featured_projects = projects | where: "featured", true %}
{% assign category_groups = projects | group_by: "category" %}

<section class="page-hero projects-hero">
  <h1 class="page-title">Research Projects</h1>
</section>

<section class="project-section">
  <div class="section-head split">
    <div>
      <h2>Featured Research Projects</h2>
    </div>
  </div>

  <div class="featured-project-grid">
    {% for project in featured_projects %}
    <article class="feature-tile">
      <div class="feature-media project-visual {{ project.visual }}" aria-hidden="true">
        {% if project.media %}
        {% assign media_count = project.media | size %}
        <div class="project-media-grid media-count-{{ media_count }}">
          {% for item in project.media %}
          <figure>
            <img class="project-image" src="{{ item.src | relative_url }}" alt="">
            {% if item.label %}<figcaption>{{ item.label }}</figcaption>{% endif %}
          </figure>
          {% endfor %}
        </div>
        {% elsif project.image %}
        <img class="project-image" src="{{ project.image | relative_url }}" alt="">
        {% else %}
        <span class="pv-dot a"></span>
        <span class="pv-dot b"></span>
        <span class="pv-dot c"></span>
        <span class="pv-line"></span>
        <span class="pv-pulse"></span>
        {% endif %}
      </div>
      <div class="feature-content">
        {% if project.focus %}
        <p class="project-focus">{{ project.focus }}</p>
        {% endif %}
        <h3>{{ project.title }}</h3>
        <p>{{ project.summary }}</p>
        {% if project.impact %}
        <p class="impact"><strong>Impact:</strong> {{ project.impact }}</p>
        {% endif %}
        <div class="tag-row">
          {% for method in project.methods %}
          <span>{{ method }}</span>
          {% endfor %}
        </div>
        {% if project.publication or project.links %}
        <div class="project-links">
          {% if project.publication %}
          <a href="{{ project.publication.url }}" {% if project.publication.url contains 'http' %}target="_blank" rel="noopener"{% endif %}>{{ project.publication.label | default: "Read the Paper" }}</a>
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

{% for group in category_groups %}
{% assign category_projects = group.items | where_exp: "project", "project.featured != true" %}
{% if category_projects.size > 0 %}
<section class="project-section">
  <div class="section-head split">
    <div>
      <p class="eyebrow">{{ group.name }}</p>
      <h2>{{ group.name }}</h2>
    </div>
  </div>

  <div class="compact-project-grid">
    {% for project in category_projects %}
    <article class="compact-project-card">
      {% if project.focus %}
      <p class="project-focus">{{ project.focus }}</p>
      {% endif %}
      <h3>{{ project.title }}</h3>
      <p>{{ project.summary }}</p>
      <div class="project-facts compact">
        {% if project.problem %}
        <div>
          <strong>Problem</strong>
          <p>{{ project.problem }}</p>
        </div>
        {% endif %}
        {% if project.approach %}
        <div>
          <strong>Approach</strong>
          <p>{{ project.approach }}</p>
        </div>
        {% endif %}
      </div>
      <div class="tag-row">
        {% for method in project.methods %}
        <span>{{ method }}</span>
        {% endfor %}
      </div>
      {% if project.publication or project.links %}
      <div class="project-links">
        {% if project.publication %}
        <a href="{{ project.publication.url }}" {% if project.publication.url contains 'http' %}target="_blank" rel="noopener"{% endif %}>{{ project.publication.label | default: "Read the Paper" }}</a>
        {% endif %}
        {% if project.links %}
        {% for link in project.links %}
        <a href="{{ link.url }}" {% if link.url contains 'http' %}target="_blank" rel="noopener"{% endif %}>{{ link.label }}</a>
        {% endfor %}
        {% endif %}
      </div>
      {% endif %}
    </article>
    {% endfor %}
  </div>
</section>
{% endif %}
{% endfor %}
