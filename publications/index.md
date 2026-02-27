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
		<li><a href="/writing">notes/talks</a></li>
		<!-- <li><a href="/contact/">contact</a></li> -->
	</ul>
</nav>

<!-- # Publications -->

<div class="publications">

<h2><strong>Publications/ In press</strong></h2>
<ol id="pubList" reversed style="padding-left:1.2em; margin-bottom: 1.2em; margin-top: 1.2em;"></ol>
<br>


<h2><strong>Manuscripts in preparation</strong></h2>
<ol reversed style="list-style-type:none; padding-left:1.2em; margin-bottom: 1.2em; margin-top: 1.2em;">
	<li>
		<p>
			<strong>J Sebastian</strong>, HA Stone, KH Jensen.
			Electrokinetic constaints on intercellular signalling in plants.
		</p>
	</li>
</ol>


<script>
  // Highlight my name
  function boldName(text) {
    return text.replace(/J Sebastian/g, '<strong>J Sebastian</strong>');
  }

  // Replace * with superscript
  function replaceAsterisk(text) {
    return text.replace(/\*/g, '<sup>*</sup>');
  }

  // Apply both transformations
  function process(text) {
    return replaceAsterisk(boldName(text));
  }

  // Choose best URL to link the title to
  function titleHref(p) {
    return p.text || p.arxiv || p.cover || "";
  }

  // Link the title (if we have a URL)
  function renderTitle(p) {
    const t = process(p.title);
    const href = titleHref(p);
    if (!href) return t;
    return `<a href="${href}" target="_blank" rel="noopener">${t}</a>`;
  }

  // Render pills for www / arXiv / cover
  function renderNotes(p) {
    let notesHTML = '';
    if (p.text)  notesHTML += `<a class="note-link" href="${p.text}" target="_blank" rel="noopener">www</a> `;
    if (p.arxiv) notesHTML += `<a class="note-link" href="${p.arxiv}" target="_blank" rel="noopener">arXiv</a> `;
    if (p.cover) notesHTML += `<a class="note-link" href="${p.cover}" target="_blank" rel="noopener">cover</a> `;
    if (p.sci_comm) notesHTML += `<a class="note-link" href="${p.sci_comm}" target="_blank" rel="noopener">post</a> `;
    // keep these optional if you still use them
    if (p.code) notesHTML += `<a class="note-link" href="${p.code}" target="_blank" rel="noopener">code</a> `;
    if (p.thread) notesHTML += `<a class="note-link" href="${p.thread}" target="_blank" rel="noopener">Sci-Comm</a> `;
    if (p.commentary) notesHTML += `<a class="note-link" href="${p.commentary}" target="_blank" rel="noopener">commentary</a> `;
    if (p.news) notesHTML += `<a class="note-link" href="${p.news}" target="_blank" rel="noopener">news</a>`;
    return notesHTML;
  }

  // IMPORTANT: Use a Jekyll-generated URL so this works on GitHub Pages reliably.
  const pubsUrl = "{{ '/publications/publications.json' | relative_url }}";

  fetch(pubsUrl)
    .then(response => response.json())
    .then(pubs => {
      const list = document.getElementById('pubList');

      pubs.forEach(p => {
        let liHTML = `<p>
          ${process(p.authors)}.
          ${renderTitle(p)}.
          ${p.journal}
          ${renderNotes(p)}
        </p>`;


        const li = document.createElement('li');
        li.innerHTML = liHTML;
        list.appendChild(li);
      });
    })
    .catch(err => console.error("Error loading publications.json:", err));
</script>



</div>





<!-- [![Electrical Circuit Modelling of Nanofluidic Systems](/projects/elkin_circuit/cover.png)]([/writing/](https://doi.org/10.1002/apxr.202370020)) -->




<!-- {% assign pubs = site.data.publications | sort: "year" | reverse %}

{% for p in pubs %}
### {{ p.title }}
**{{ p.authors | join: ", " }}** ({{ p.year }}). *{{ p.venue }}*.

{% if p.doi %}DOI: {{ p.doi }}{% endif %}
{% if p.arxiv %} arXiv: {{ p.arxiv }}{% endif %}
{% if p.url %} [Link]({{ p.url }}){% endif %}

{% endfor %} -->