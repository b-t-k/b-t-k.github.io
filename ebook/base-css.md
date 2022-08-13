---
layout: page
title: "CSS Samples"
permalink: ebook/
---

{% include menu2.md %}

## TO DO
Check into `p.first-child` class — it needs to be added as `p:first-child` isn't respected

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

i > i,
em > i,
i > em{
	font-style: normal;
}

```
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


## SVG etc.
Using SVG will scale and be more responsive. SVGs can be created by: copy of material in InDesign and Paste in Place in Adobe Illustrator. Group, then rasterize the content. Right click on rasterized image and choose export as collection. THen choose SVG as the export option */
Standard:
`<img alt="" src="../images/titlepage.svg" epub:type="se:image.color-depth.black-on-transparent"/>` or  
`<img alt="" class="epub-type-se-image-color-depth-black-on-transparent" src="../images/titlepage.png"/>`

```
/* Cover & Title Page */

.cover {
	width:100vw;
	height:100vh;
	object-fit:contain; /* or :cover, which provides a more resposive experience, but will cut off the image if it is bigger than the container */
	object-position: center;
}

.title-page { 
	width:100vw;
	height:100vh;
	object-fit:contain; /* or :cover, which provides a more resposive experience, but will cut off the image if it is bigger than the container */
	object-position: center;
}

/* Standard */
section.epub-type-titlepage img{
	display: block;
	margin-top: 3em;
	margin-right: auto;
	margin-bottom: auto;
	margin-left: auto;
	width: 100%;
```


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

## Special characters
- nonbreaking space:  `&#160;`
- nonbreaking character `&#8239;`
- thin space: `&#8201;`

## notes to sort

`text-align: initial;` is used instead of `text-align: left;` whenever it's necessary to explicitly set left-aligned text. This allows the reading system to opt to use `text-align: justify;` if the user prefers.