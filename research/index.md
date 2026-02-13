---
layout: default
title: John Sebastian | research
permalink: /research/
---
<nav>
	<ul>
		<li><a href="/">about</a></li>
		<li><a id="research" class="active" href="/research">research</a></li>
		<li><a href="/publications">publications</a></li>
		<li><a href="/writing">notes/talks</a></li>
		<!-- <li><a href="/contact">contact</a></li> -->
	</ul>
</nav>

Below is a gallery of recent projects. A few more at [Notes/Talks](/writing/).

----

<div class="notes-grid">
{% assign items = site.projects | sort: "date" | reverse %}
  {% if n.thumbnail %}
    <img class="note-thumb" src="{{ n.thumbnail | relative_url }}" alt="{{ n.title }}">
  {% endif %}
{% for p in items %}
  <a class="note-card {{ p.card_style }}" href="{{ p.url | relative_url }}">
    <img class="note-thumb" src="{{ p.thumbnail | relative_url }}" alt="{{ p.title }}">
    <div class="note-caption">
      <div class="note-title">{{ p.title }}</div>
      {% if p.caption %}<div class="note-sub">{{ p.caption }}</div>{% endif %}
    </div>
  </a>
{% endfor %}
</div>