---
title: Publications
permalink: /publications/
---

<section class="page-hero">
  <h1 class="page-title">Publications</h1>
  <p class="page-links">
    <a class="badge" href="https://scholar.google.com/citations?user=rLltVjIAAAAJ&hl=en" target="_blank">Google Scholar</a>
    <a class="badge" href="https://www.researchgate.net/profile/Golam-Azom?ev=hdr_xprf" target="_blank">ResearchGate</a>
  </p>
</section>

{% assign groups = site.data.publications | group_by: "year" | sort: "name" | reverse %}
{% for g in groups %}
  <h2 class="pub-year">{{ g.name }}</h2>
  <div class="pub-list">
    {% for p in g.items %}
      <article class="pub-card">
        <div class="pub-thumb">
          {% if p.toc %}<img src="{{ p.toc | relative_url }}" alt="TOC figure for {{ p.title }}">{% endif %}
        </div>
        <div class="pub-body">
          <div class="pub-meta">
            {% if p.venue %}<span class="venue">{{ p.venue }}</span>{% endif %}
            {% if p.type %}<span class="tag">{{ p.type }}</span>{% endif %}
          </div>
          <h3 class="title">{{ p.title }}</h3>
          <p class="authors">{{ p.authors | markdownify }}</p>

          {% if p.abstract %}
          <details class="abs">
            <summary>Abstract</summary>
            <p>{{ p.abstract }}</p>
          </details>
          {% endif %}

          <div class="links">
            {% if p.doi %}<a href="https://doi.org/{{ p.doi }}">DOI</a>{% endif %}
            {% if p.link %}<a href="{{ p.link }}">Publisher</a>{% endif %}
            {% if p.preprint %}<a href="{{ p.preprint }}">Preprint</a>{% endif %}
            {% if p.pdf %}<a href="{{ p.pdf }}">PDF</a>{% endif %}
            {% if p.code %}<a href="{{ p.code }}">Code</a>{% endif %}
            {% if p.bibtex %}<a href="{{ p.bibtex }}">BibTeX</a>{% endif %}
          </div>
        </div>
      </article>
    {% endfor %}
  </div>
{% endfor %}
