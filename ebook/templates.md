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
	<body>
		<section>
		
		</section>
	</body>
</html>
```

## Content OPF
```

    <dc:identifier>urn:isbn:9781459827585</dc:identifier>
```

hide spine items
`	<itemref idref="nav.xhtml" linear="no"/>`



### Accessibility Metadata
```
	<meta property="schema:accessibilitySummary">This publication conforms to WCAG 2.1 Level AA.</meta>
	<link href="http://www.idpf.org/epub/a11y/accessibility-20170105.html#wcag-aa" rel="dcterms:conformsTo"/>
	<meta property="schema:accessMode">textual</meta>
	<meta property="schema:accessMode">Visual</meta>
	<meta property="schema:accessModeSufficient">textual, visual</meta>
	<meta property="schema:accessibilityFeature">structuralNavigation</meta>
	<meta property="schema:accessibilityFeature">tableOfContents</meta>
	<meta property="schema:accessibilityFeature">readingOrder</meta>
	<meta property="schema:accessibilityFeature">unlocked</meta>
	<meta property="schema:accessibilityHazard">none</meta>
```
**Extra bits**
- `<meta property="a11y:certifiedBy">Benetech</meta>`
- `<meta property="a11y:certifierCredential">https://bornaccessible.org/certification/gca-credential/</meta>`
- `<dc:source>print_source_ISBN</dc:source>`
- `<meta property="schema:accessibilityFeature">printPageNUmbers</meta>`
- `<meta property="schema:accessibilityFeature">alternativeText</meta>`
- `<meta property="schema:accessibilityFeature">tableOfContents</meta>`
- `<meta property="schema:accessibilityAPI">ARIA</meta>`
- `<meta property="schema:accessibilityFeature">displayTransformability</meta>`
- `<meta property="schema:accessibilityFeature">noFlashingHazard</meta>`
- `<meta property="schema:accessibilityFeature">noSoundHazard</meta>`
- `<meta property="schema:accessibilityFeature">noMotionSimulationHazard</meta>`


## T0C
> Reference all text sections, even front and back matter, directly from the navigation file. If an HTML document is referenced in the spine, it should be referenced in the navigation file as well. Comprehensive navigation points to all parts of the book’s content ensure that all readers will be able to access the desired information efficiently.