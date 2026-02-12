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
		<li><a href="/contact">contact</a></li>
	</ul>
</nav>

<div class="publications">

<h2><strong>Published manuscripts</strong></h2>
<ol id="pubList" reversed style="padding-left:1.2em; margin-bottom: 1.2em; margin-top: 1.2em;"></ol>
<br>

<!-- <h2><strong>Manuscripts under review</strong></h2>
<ol reversed style="list-style-type:none; padding-left:1.2em; margin-bottom: 1.2em; margin-top: 1.2em;">
	<li>
		<p>
			Konczal M, <strong>Lyulina AS</strong>, Zapata L, Camara F, Camara F, ...
			Population growth facilitated the retention of deleterious variance in the critically endangered spoon-billed sandpiper.
			<a class="note-link" href="https://github.com/alyulina/spoon-billed-sandpiper" target="_blank" rel="noopener">code</a>
		</p>
	</li>
</ol>
<br> -->

<h2><strong>Manuscripts in preparation</strong></h2>
<ol reversed style="list-style-type:none; padding-left:1.2em; margin-bottom: 1.2em; margin-top: 1.2em;">
	<li><p><strong>Lyulina AS</strong>, Good BH. Genetic diversity under nonequilibrium demography.</p></li>
	<li>
		<p>
			<strong>Sebastian J*</strong>, Stone HA, Jensen KH.
			Electrokinetic constaints on intercellular signalling in plants.
			<a class="note-link" href="https://github.com/alyulina/metastatic-phenotypes" target="_blank" rel="noopener">url</a>
		</p>
	</li>
</ol>



<script>
  // Highlight my name
  function boldName(text) {
    return text.replace(/Lyulina AS/g, '<strong>Lyulina AS</strong>');
  }

  // Replace * with superscript
  function replaceAsterisk(text) {
    return text.replace(/\*/g, '<sup>*</sup>');
  }

  // Apply both transformations
  function process(text) {
    return replaceAsterisk(boldName(text));
  }

  // Italicize everything before first number in journal string
  function italicizeJournal(journal) {
    return journal.replace(/^(.+?)\s+(?=\d)/, '<em>$1</em> ');
  }

  // Render code/text/thread/cover/commentary/news links inline
  function renderNotes(p) {
    let notesHTML = '';
    if (p.text) notesHTML += `<a class="note-link" href="${p.text}" target="_blank" rel="noopener">text</a> `;
    if (p.code) notesHTML += `<a class="note-link" href="${p.code}" target="_blank" rel="noopener">code</a> `;
    if (p.thread) notesHTML += `<a class="note-link" href="${p.thread}" target="_blank" rel="noopener">thread</a> `;
    if (p.cover) notesHTML += `<a class="note-link" href="${p.cover}" target="_blank" rel="noopener">cover</a> `;
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
          ${process(p.authors)}
          ${process(p.title)}
          ${italicizeJournal(p.journal)}
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





# Publications

{% assign pubs = site.data.publications | sort: "year" | reverse %}

{% for p in pubs %}
### {{ p.title }}
**{{ p.authors | join: ", " }}** ({{ p.year }}). *{{ p.venue }}*.

{% if p.doi %}DOI: {{ p.doi }}{% endif %}
{% if p.arxiv %} arXiv: {{ p.arxiv }}{% endif %}
{% if p.url %} [Link]({{ p.url }}){% endif %}

{% endfor %}