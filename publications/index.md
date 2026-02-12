---
layout: default
title: John Sebastian | publications
permalink: /publications/
---
<nav>
	<ul>
		<li><a href="/">about</a></li>
		<li><a href="/research">research</a></li>
		<li><a id="publications" class="active" href="/publications">publications</a></li>
		<li><a href="/code">code</a></li>
		<li><a href="/writing">writing</a></li>
		<li><a href="/cv">cv</a></li>
		<li><a href="/contact">contact</a></li>
	</ul>
</nav>


# Publications

{% assign pubs = site.data.publications | sort: "year" | reverse %}

{% for p in pubs %}
### {{ p.title }}
**{{ p.authors | join: ", " }}** ({{ p.year }}). *{{ p.venue }}*.

{% if p.doi %}DOI: {{ p.doi }}{% endif %}
{% if p.arxiv %} arXiv: {{ p.arxiv }}{% endif %}
{% if p.url %} [Link]({{ p.url }}){% endif %}

{% endfor %}