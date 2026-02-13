---
layout: default
title: "Markdown Resources"
date: 2021-01-10
thumbnail: 
caption: ""
card_style: wide
---

<nav>
	<ul>
		<li><a href="/">about</a></li>
		<li><a href="/research">research</a></li>
		<li><a href="/publications">publications</a></li>
		<li><a id="writing" class="active" href="/writing">notes/talks</a></li>
		<!-- <li><a href="/contact">contact</a></li> -->
	</ul>
</nav>

Some of the handy Markdown tricks I've come across and found useful, and collected for reference.
<hr>

<div class=text-justify> 

To paraphrase Prof Alex Slocum[^1][^2], if you are a serious researcher in this century, you should have a website; and if you don’t, don’t expect to talk.   
I believe that he's absolutely right! 

I often use markdown to write everything from emails to technical documents and manuscripts.

These are *shortcuts/ tricks/ resources* that I’ve looked up over time. Just posting it here for future reference- yours and mine.
</div>   

***   

{{< table_of_contents >}}  
 

***   

## 1 To change fonts inline in Markdown


```
<p class=text-center style="font-family: Georgia, serif; font-size:11pt; font-weight:bold">
 This is how you do it!
</p>
```

Check the [full HTML output](./ref.html) to see how it works. Themes can override the intended output.


General styling tweaks are discussed in Section: [Text formatting and
Styles](#4-text-formatting-and-styles)

### 1.1 Useful list of Fonts

-   Arial (sans-serif)
-   Verdana (sans-serif)
-   Helvetica (sans-serif)
-   Tahoma (sans-serif)
-   Trebuchet MS (sans-serif)
-   Times New Roman (serif)
-   Georgia (serif)
-   Garamond (serif)
-   Courier New (monospace)
-   Brush Script MT (cursive)

As you can see, this is not the most elegant solution for inline changes
in text formatting. If it were so, I would have converted each of the
above list entries to the fonts they represent.

## 2 Toc - Table of Contents

-   the toggle word for `toc` is `yes` and not `true` in RMarkdown

### 2.1 Indentation

-   the following script will take care of indentation in the toc list:

<!-- -->

    <script>
    $(document).ready(function() {
      $items = $('div#TOC li');
      $items.each(function(idx) {
        num_ul = $(this).parentsUntil('#TOC').length;
        $(this).css({'text-indent': num_ul * 10, 'padding-left': 0});
      });

    });
    </script>

-   Use `number_sections: true` in the header for numbering. Levels are
    intuitively expressed using *decimal dots* and are equivalent to the
    number of `#` signs prefixing the heading. But to display more
    levels than the default 3 (H3) levels, use `toc_depth: 5` in the
    header.
  
### 2.2 TOC anywhere on the page
-	This can be done (as I have chosen to do for this article) by making use of [Shortcodes](https://gohugo.io/templates/shortcode-templates/).
  Checkout the details and implementation in [Ref. 4](#8-Reference)

## 3 Text alignment

-   While its possible to use css to do this, I often use the following
    html snip for flexibility

<!-- -->

    <div class=text-justify>
    body
    </div>

## 4 Text formatting and Styles

-   the following snippet of code can be placed in the markdown body as
    a work around to text styling.

<!-- -->


    <style type="text/css">

    body{ /* Normal  */
          font-size: 12px;
      }
    td {  /* Table  */
      font-size: 8px;
    }
    h1.title {
      font-size: 38px;
      color: DarkRed;
    }
    h1 { /* Header 1 */
      font-size: 28px;
      color: DarkBlue;
    }
    h2 { /* Header 2 */
        font-size: 22px;
      color: DarkBlue;
    }
    h3 { /* Header 3 */
      font-size: 18px;
      font-family: "Times New Roman", Times, serif;
      color: DarkBlue;
    }

    </style>

### 4.1 Themes

The list of themes available to call from the header via `theme` is
available at [Bootswatch](https://bootswatch.com/3/)[^3]

## 5 Internal Links

I have used an implicit link in section [To change fonts inline in
Markdown](#1-to-change-fonts-inline-in-markdown).

The syntax is to use the correct heading you want to link to within
square brackets:

    I have used an implicit link in section [To change fonts inline in Markdown].

## 6 Footnotes

The syntax is as follows. Scroll down to see how they appear.

    Footnote 1 link[^first].

    Footnote 2 link[^second].

    Inline footnote^[Text of inline footnote] definition.

    Duplicated footnote reference[^second].

    [^first]: Footnote **can have markup**

        and multiple paragraphs.

    [^second]: Footnote text.


## 7 Converting to GFM

The front matter specifics:

    output:
      md_document:
        variant: gfm
        toc: yes
        toc_depth: 5
        number_sections: true
    preserve_yaml: true

## 8 Reference

1.  [markdown-it](https://markdown-it.github.io/)
2.  [R Markdown: The Definitive
    Guide](https://bookdown.org/yihui/rmarkdown/)
3.  [Reproducible Templates for Analysis and Dissemination Course by
    Emory University](https://www.coursera.org/lecture/reproducible-templates-analysis/customizing-an-html-document-3Bfz3)
4.  [Table of Contents Shortcode](https://ruddra.com/hugo-add-toc-anywhere/)



   

[^1]: [Tea with Alexander Slocum: an
interview](https://www.youtube.com/watch?v=NkbY2RHviPU&ab_channel=TeawithTeachers)\

[^2]: [Alex Slocum’s website](http://pergatory.mit.edu/)

[^3]: [Rmarkdown
Catalogue](https://bookdown.org/yihui/rmarkdown/html-document.html#appearance-and-style)
