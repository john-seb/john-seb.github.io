---
layout: default
title: John Sebastian | publications
permalink: /publications/
---

<nav>
	<ul>
		<li><a href="/about">about</a></li>
		<li><a href="/research">research</a></li>
		<li><a id="publications" class="active" href="/publications">publications</a></li>
		<li><a href="/code">code</a></li>
		<li><a href="/writing">writing</a></li>
		<li><a href="/cv">cv</a></li>
		<li><a href="/contact">contact</a></li>
	</ul>
</nav>

# Publications

<div class="pub-table">
  <div class="pub-header">
    <div>Paper</div>
    <div>Details</div>
    <div>Links</div>
  </div>

  {% assign pubs = site.data.publications | sort: "year" | reverse %}
  {% for p in pubs %}
  <div class="pub-row">
    <div class="pub-paper">
      <img class="pub-thumb" src="{{ p.thumbnail }}" alt="Thumbnail for {{ p.title }}">
      <div class="pub-title">{{ p.title }}</div>
    </div>

    <div class="pub-details">
      <div class="pub-authors">{{ p.authors }}</div>
      <div class="pub-venue">{{ p.venue }} · {{ p.year }}</div>

      {% if p.tags %}
      <div class="pub-tags">
        {% for t in p.tags %}
          <span class="pub-tag">{{ t }}</span>
        {% endfor %}
      </div>
      {% endif %}
    </div>

    <div class="pub-links">
      {% if p.links.paper %}<a href="{{ p.links.paper }}" target="_blank" rel="noopener">paper</a>{% endif %}
      {% if p.links.pdf %}<a href="{{ p.links.pdf }}" target="_blank" rel="noopener">pdf</a>{% endif %}
      {% if p.links.doi %}<a href="{{ p.links.doi }}" target="_blank" rel="noopener">doi</a>{% endif %}
      {% if p.links.arxiv %}<a href="{{ p.links.arxiv }}" target="_blank" rel="noopener">arXiv</a>{% endif %}
      {% if p.links.code %}<a href="{{ p.links.code }}" target="_blank" rel="noopener">code</a>{% endif %}
      {% if p.links.project %}<a href="{{ p.links.project }}" target="_blank" rel="noopener">project</a>{% endif %}
    </div>
  </div>
  {% endfor %}
</div>
