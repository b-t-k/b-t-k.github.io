---
layout: page
title: "CSS Samples"
permalink: ebook/
---

{% include menu2.md %}


## Base CSS
### Core CSS
```
@charset "utf-8";
@namespace epub "http://www.idpf.org/2007/ops";

@page {
	margin: 10px;
	padding: 0;
}
body {
	<!-- font-family: serif; -->
	font-variant-numeric: oldstyle-nums;
	hyphens: auto;
	adobe-hyphenate: auto;
	-webkit-hyphens: auto;
	-moz-hyphens: auto;
	-epub-hyphens: auto;
	orphans: 1;
	widows: 1;
}

/*headings*/

h1, h2, h3, h4, h5, h6 {
	font-family: sans-serif;

	break-after: avoid;	
	page-break-after: avoid;
	break-inside: avoid;	
	page-break-inside: avoid;
	hyphens: none !important;
	adobe-text-layout: optimizeSpeed; /* For Nook */
	-webkit-hyphens: none !important;
	-moz-hyphens: none !important;
	-epub-hyphens: none;
	margin:	0;
	padding:0;
	text-indent: 0;
}

/* Paragraphs */
p, a, blockquote, ul, ol, li, th, tr, td {
	hyphenate-limit-lines: 3;
	hyphenate-limit-chars: 6 3 2;
	hyphenate-limit-last: always;
	-webkit-hyphenate-limit-lines: 3;
	-webkit-hyphenate-limit-chars: 6 3 2;
	-webkit-hyphenate-limit-last: always;
	-ms-hyphenate-limit-lines: 3;
	-ms-hyphenate-limit-chars: 6 3 2;
	-ms-hyphenate-limit-last: always;
	font-size: 1rem;
	line-height: 1.2rem;
	margin: 0;
}

p{
	text-indent: 1.2rem;
}

li {
	margin: 1em;
	text-indent:0;
}


h1 + p,
h2 + p,
h3 + p,
h4 + p,
h5 + p,
h6 + p,
header + p,
hr + p,
p.first-child,
p:first-child{
	text-indent: 0;
}

cite{
	font-style:italic;
}

i > i,
em > i,
i > em,
cite > i{
	font-style: normal;
}

hr{
	border: none;
	width: 0;
	margin: 1em 0;
}
```

## Images
### Decorative Images
Correctly labeled they are skippable by readers
`<img class="dingbat" src="images/asterisks.png" alt="" role="presentation"/>`


**Note:** `max-width` not supported in KF8 (Kindle)
### Cover Images
#### HTML
```
<figure class="cover-img">
	<img src="image/cover.jpg" class="cover-image" epub:type="cover" role="doc-cover" alt="this_is_alt_test."/>
</figure>

```

#### CSS
```
figure.cover-img {
	display: block;
	text-align: center;
}

img.cover-image {
	height: 95%;
	object-fit:contain;
	width: auto;
}

img.cover-image:only-of-type { /*overrides the previous setting, but only in newer systems that support CSS3 */
	height: 95vh;
}

@media amzn-kf8 {
	/* CSS for KF8 devices */
	img.cover-image:only-of-type { /*overrides the previous setting, but only in newer systems that support CSS3 */
	 height: 95%;
	}
}

@media amzn-mobi {
	/* CSS for Mobi devices */
	img.cover-image:only-of-type { /*overrides the previous setting, but only in newer systems that support CSS3 */
	 height: 95%;
	}
}


.titlepage img{
	display: block;
	margin-top: 3em;
	margin-right: auto;
	margin-bottom: auto;
	margin-left: auto;
	width: 100%;

```

#### Laura's (Blitz) CSS
```
img.Cover {
    height:95vh;
    object-fit:contain;
    max-width:100%;
}

img.titlepage {
    height:95vh;
}


hr.dbat {
  height: 1em;
  background: transparent url("../image/dbat.png") no-repeat center;
  background-size: 2.5em 1.25em;
  overflow: hidden;
  page-break-inside: avoid;
  break-inside: avoid;
  border:none;
}

```

**Custom Lists**
```
ul {
  list-style-image: url(star.svg);
}

ul {
  padding-left: 2rem;
  list-style-type: none;
}

ul li {
  padding-left: 2rem;
  background-image: url(star.svg);
  background-position: 0 0;
  background-size: 1.6rem 1.6rem;
  background-repeat: no-repeat;
}
```

**Abbr**
Abbreviation markup: `<abbr title="Laugh Out Loud">LOL</abbr>`


### Sub and Sup

```
sub {
  font-size: 0.675em;
  line-height: 1.2;
  vertical-align: sub;
  vertical-align: -20%;
}

sup {
  font-size: 0.675em;
  line-height: 1.2;
  vertical-align: super;
  vertical-align: 35%;
}
```

### SVG for covers, full pages
A "SVG wrapper" is sometimes applied to an image in order to scale it as large as possible on a page without distortion. This is not possible using just using HTML because screens can have widely differing aspect ratios. Title pages probably should fall back to png.

```
	<section id="cover" epub:type="cover">
		<figure class="cover-img">
			<svg xmlns="http://www.w3.org/2000/svg" height="100%" preserveAspectRatio="xMidYMid meet" version="1.1" viewBox="0 0 1428 2200" width="100%" xmlns:xlink="http://www.w3.org/1999/xlink">
			<image width="1428" height="2200" xlink:href="../images/cover.jpg"/>
			</svg>
		</figure>
	</section>
```

**Note**  
6" x 9" = 1400px x 2100px  

### content.opf
`<item href="page_name.html" id="" media-type="application/xhtml+xml" properties="svg"/>`
`<item href="Images/image_name_.svg" id="" media-type="image/svg+xml" />`

*CSS*
### Suggested
```
/* Cover & full page */

.cover,
.full-page {
	width:100vw;
	height:100vh;
	object-fit:contain;
	object-position: center;
}
```

## Common CSS

### Lists
Set ol li as one style then ol li p as another
```
/*sidebar*/

ul li,
ol li {
font-family: sans-serif;
font-weight: bold;
color: #666;
font-size: 105%;
}

li p {
font-family:serif;
font-weight: normal;
font-size: 1 em;
color: initial;
}

```

### Tables
```
/* Tables */

div.table-responsive {
	overflow-x: auto;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td, tr {
  text-align: left;
  padding: 10px;
}
```


### sidebar, backgrounds
```
blockquote.sidebar{
	margin: 0.5em;
	padding: 1em;
	-webkit-column-break-inside: avoid;
	page-break-inside: avoid;
	break-inside: avoid;
}
```

```
header{
	background: url("../image/sharkbackground_aqua.png") no-repeat;
	background-position: center center;
	background-size: contain;
	margin: 2em 0;
	padding: 1em 0 2em;
}
```
### Copyright and Dedication
```
/*copyright*/
.Copyright{
text-align: left;
font-size: 90%;
}

/*dedication*/
.Dedication {
font-style: italic;
text-align: right;
margin-top: 20%;
}
```
### Praise (Page Two)
#### HTML:
`<p class="Endorsements">“This is an endosement”</p>`
`<p class="EndorsementAttri"><span class="AttriEndorseName">Endorser_Name</span>, Their titles</p>`

#### CSS:
```
/*praise*/
.Endorsements {
margin-top:1em;
margin-bottom:.25em;
}
.EndorsementAttri{
font-family:"Graphik", sans-serif;
font-weight: 500;
font-size: 95%;
}
.AttriEndorseName{
font-weight:bold;
}
```

## Font Faces
Check EULAs
```
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:normal;
	src : url("../font/Graphik-Regular.otf");
}
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:bold;
	src : url("../font/Graphik-Bold.otf");
}
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:500;
	src : url("../font/Graphik-Medium.otf");
}
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:600;
	src : url("../font/Graphik-Semibold.otf");
}
@font-face {
	font-family:"Graphik";
	font-style:normal;
	font-weight:900;
	src : url("../font/Graphik-Black.otf");
}
```
### A potential fix
To remove font-weight and font-styles in css you can….  
Change:
```
	font-family:Graphik;
	font-style:italic;
	font-weight:normal;
	src : url("../font/Graphik-Italic.otf");
}
@font-face {
	font-family:Graphik;
	font-style:normal;
	font-weight:bold;
	src : url("../font/Graphik-Bold.otf");
}
```
to:
```
@font-face {
	font-family:"Graphik Italic";
	font-style:normal;
	font-weight:normal;
	src : url("../font/Graphik-Italic.otf");
}

@font-face {
	font-family:"Graphik Bold";
	font-style:normal;
	font-weight:normal;
	src : url("../font/Graphik-Bold.otf");
}
```

### To subset fonts
```
@font-face {
	font-family:JapaneseWithGentium;	src : url(font/Gentium.ttf);
	unicode-range:U+0-2FF;
}
```
### iBooks (from 2014)
**NOT SURE IF THIS IS RELEVANT**
Create file named `com.apple.ibooks.display-options.xml` in META-INF folder
```
<?xml version="1.0" encoding="UTF-8"?>
<display_options>
	<platform name="*">
		<option name-"specified-fonts">true</option>
	</platform>
</display_options>
```
And then in content.opf change:
```
<package version="3.0" unique-identifier="bookid" prefix="ibooks: http://vocabulary.itunes.apple.com/rdf/ibooks/vocabulary-extensions-1.0/" xmlns="http://www.idpf.org/2007/opf">
```
To:
```
<package xmlns="http://www.idpf.org/2007/opf" unique-identifier="bookid" version="3.0"  prefix="rendition:http://idpfg.org/vocab/rendition/#ibooks:http://vocabulary.itunes.apple.com/rdf/ibooks/vocabulary-extensions-1.0/" >
```

```
<package  xmlns=“http://www.idpf.org/2007/opf” version=“3.0” unique-identifier=“bookid” prefix=“ibooks: http://vocabulary.itunes.apple.com/rdf/ibooks/vocabulary-extensions-1.0/”>
```
Be sure to add `<meta property="iBooks:specified-fonts">true</meta>` to metadata in content.opf




### `sup` and `sub` Suggestions
```
PREVENT SUB- AND SUPER- SCRIPT FROM AFFECTING LINE-HEIGHT - Sub- and super- script will affect line-height if you just use their dedicated keyword for vertical-align. By decreasing line-height to the minimum value Kindle supports (i.e. 1.2) and using % for vertical-align, we solve this problem and can vertically-align sub- and superscript more accurately.
*/

sub {
 font-size: 0.675em;
 line-height: 1.2;
 vertical-align: sub;
 vertical-align: -20%;
}

sup {
 font-size: 0.675em;
 line-height: 1.2;
 vertical-align: super;
 vertical-align: 35%;
}

a[epub|type~="noteref"]{
	font-size: .75em;
	font-style: normal !important;
	vertical-align: super;
```

### Verse etc.
Borrowed from [Standard ebooks](https://standardebooks.org/manual/1.7.0/7-high-level-structural-patterns#7.5)

#### HTML
```
<p>
	<span>A line in a stanza</span>
	<br/>
	<span>Another line in a stanza</span>
</p>
<p>
	<span>First line</span>
	<br/>
	<span class="i1">indented line.</span>
</p>
```

#### CSS

```
.poem p > span{
	display: block;
	padding-left: 1em;
	text-indent: -1em;
}
.poem p > span + br{
	display: none;
}

p span.i1{
	padding-left: 2em;
	text-indent: -1em;
}
```

# MISC

## Special characters
- nonbreaking space:  `&#160;`
- nonbreaking character `&#8239;`
- thin space: `&#8201;`

## Page breaks
`page-break-inside:avoid;`
- * rigidly applied

## notes to sort
- look at Circular Flow for fixed layout
`text-align: initial;` is used instead of `text-align: left;` whenever it's necessary to explicitly set left-aligned text. This allows the reading system to opt to use `text-align: justify;` if the user prefers.

## Accessibility

(https://kb.daisy.org/publishing/docs/metadata/schema.org/index.html#prop)
  
See [templates](/templates/)
```
<metadata>
  <meta property="schema:accessibilitySummary">
     This publication conforms to WCAG 2.0 Level AA.
  </meta>
  <meta property="schema:accessMode">textual</meta>
  <meta property="schema:accessMode">visual</meta>
  <meta property="schema:accessModeSufficient">textual</meta>
  <meta property="schema:accessibilityFeature">structuralNavigation</meta>
  <meta property="schema:accessibilityFeature">MathML</meta>
  <meta property="schema:accessibilityFeature">alternativeText</meta>
  <meta property="schema:accessibilityFeature">longDescription</meta>
  <meta property="schema:accessibilityHazard">noFlashingHazard</meta>
  <meta property="schema:accessibilityHazard">noSoundHazard</meta>
  <meta property="schema:accessibilityHazard">noMotionSimulationHazard</meta>
  …
</metadata>
```