---
layout: page
title: "Base Templates"
permalink: templates/
---

{% include menu2.md %}

## Basic header
```
<?xml version="1.0" encoding="utf-8"?>
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:epub="http://www.idpf.org/2007/ops" lang="en-US" xml:lang="en-US">
	<head>
		<title>Title</title>
		<link href="css/styles.css" rel="stylesheet" type="text/css"/>
	</head>
		<body epub:type="bodymatter">
		<section aria-labelledby="ch01" role="doc-chapter" epub:type="chapter">
			<h1 class="chapter-name" id="ch01" epub:type="title">CHAPTER NUMBER</h1>
		
		</section>
	</body>
</html>
```

```
<?xml version="1.0" encoding="utf-8"?>
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:epub="http://www.idpf.org/2007/ops" epub:prefix="z3998: http://www.daisy.org/z3998/2012/vocab/structure/" xml:lang="en-GB">
	<head>
		<title>Chapter IV: Al-Kantara, or “The Bridge”</title>
		<link href="../css/core.css" rel="stylesheet" type="text/css"/>
		<link href="../css/local.css" rel="stylesheet" type="text/css"/>
	</head>
	<body epub:type="bodymatter z3998:fiction">
		<section id="chapter-4" epub:type="chapter">
			<header>
				<p xml:lang="ar">القنطرة</p>
				<hgroup>
					<h2>
						<span epub:type="label">Chapter</span>
						<span epub:type="ordinal z3998:roman">IV</span>
					</h2>
					<h3 epub:type="title"><i xml:lang="ar-Latn">Al-Kantara</i>, or “The Bridge”</h3>
				</hgroup>
			</header>
			<p>When the hour of public executions had arrived and the boys were assembled once more at their uncle’s feet to hear the story of his fortunes, (their minds full of his last success), the old man, still occupied with that pleasing memory, began at once the continuation of his life.</p>
```

## Content OPF
```

    <dc:identifier>urn:isbn:9781459827585</dc:identifier>
```

### Spine
To hide spine items:
`<itemref idref="nav.xhtml" linear="no"/>`



### Accessibility Metadata
```
	<meta property="schema:accessibilitySummary">This publication conforms to WCAG 2.1 Level AA.</meta>
	<link href="http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aa" rel="dcterms:conformsTo"/>
	<meta property="schema:accessMode">textual</meta>
	<meta property="schema:accessMode">visual</meta>
	<meta property="schema:accessModeSufficient">textual, visual</meta>
	<meta property="schema:accessibilityFeature">structuralNavigation</meta>
	<meta property="schema:accessibilityFeature">tableOfContents</meta>
	<meta property="schema:accessibilityFeature">readingOrder</meta>
	<meta property="schema:accessibilityFeature">unlocked</meta>
	<meta property="schema:accessibilityHazard">none</meta>
```
**Extra bits**

- `<dc:source>print_source_ISBN</dc:source>`
- `<meta property="schema:accessibilityFeature">printPageNumbers</meta>`

- `<meta property="schema:accessibilityFeature">alternativeText</meta>`
- `<meta property="schema:accessibilityAPI">ARIA</meta>`
- `<meta property="schema:accessibilityFeature">displayTransformability</meta>`

- `<meta property="schema:accessibilityFeature">noFlashingHazard</meta>`
- `<meta property="schema:accessibilityFeature">noSoundHazard</meta>`
- `<meta property="schema:accessibilityFeature">noMotionSimulationHazard</meta>`

- `<meta property="schema:accessibilitySummary">This publication conforms to WCAG 2.1 Level AA.</meta>`

**Remember page source if using printPageNumbers**

### Page list
```
<nav epub:type="page-list" id="pagelist" role="doc-pagelist">
<h1>Print Page List</h1>
  <ol>
    <li><a href="cover.xhtml#page_i">page i</a></li>
    <li><a href="page212.xhtml#page_210">210</a></li>
  </ol>
</nav>
```


### Certifiers
- `<meta property="a11y:certifiedBy">Benetech</meta>`
- `<meta property="a11y:certifierCredential">https://bornaccessible.org/certification/gca-credential/</meta>`

The following example shows an EPUB 3 Publication that has been self-certified by the publisher (the values of the dc:publisher and a11y:certifiedBy property are the same).
```
<metadata>
  …
  <dc:publisher>Acme Publishing Inc.</dc:publisher>
  <meta property="a11y:certifiedBy">Acme Publishing Inc.</meta>
  <link rel="dcterms:conformsTo" href="http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aa"/>
  …
</metadata>
```
The following example shows a credential.

`<meta property="a11y:certifierCredential">A+ Accessibility Rating</meta>`

### Summary
- GCA partners will no longer be required to include an `accessibilitySummary` and will be discouraged to add one unless the summary is including additional information not already provided in the metadata

## Poetry/verse
see [https://kb.daisy.org/publishing/docs/html/poetry.html](https://kb.daisy.org/publishing/docs/html/poetry.html)

and [https://standardebooks.org/manual/1.7.0/7-high-level-structural-patterns#7.5](https://standardebooks.org/manual/1.7.0/7-high-level-structural-patterns#7.5)

## ToC
> Reference all text sections, even front and back matter, directly from the navigation file. If an HTML document is referenced in the spine, it should be referenced in the navigation file as well. Comprehensive navigation points to all parts of the book’s content ensure that all readers will be able to access the desired information efficiently.

## Accessibility?
`<time datetime="1895">1895</time>`