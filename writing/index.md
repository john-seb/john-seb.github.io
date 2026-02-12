---
layout: default
title: John Sebastian| notes
permalink: /writing/
---
<nav>
	<ul>
		<li><a href="/">about</a></li>
		<li><a href="/research">research</a></li>
		<li><a href="/publications">publications</a></li>
		<li><a id="writing" class="active" href="/writing">notes/talks</a></li>
		<!-- <li><a href="/contact/">contact</a></li> -->
	</ul>
</nav>

### Talks

<div class="notes-grid">
{% assign items = site.notes | sort: "date" | reverse %}
{% for n in items %}
  <a class="note-card" href="{{ n.url | relative_url }}">
    <img class="note-thumb" src="{{ n.thumbnail | relative_url }}" alt="{{ n.title }}">
    <div class="note-caption">
      <div class="note-title">{{ n.title }}</div>
      {% if n.caption %}<div class="note-sub">{{ n.caption }}</div>{% endif %}
      {% if n.date %}<div class="note-meta">{{ n.date | date: "%Y-%m-%d" }}</div>{% endif %}
    </div>
  </a>
{% endfor %}
</div>