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

i > i,
em > i,
i > em{
	font-style: normal;
}

```
### cover images
```
body.fullpage {
	margin: 0;
	padding: 0;
}
div.cover {
	display: block;
	text-align: center;
	height: 95%;
}
img.coverimage {
	height: 95%;
	width: auto;
}

img.coverimage:only-of-type { /*overrides the previous setting, but only in newer systems that support CSS3 */
	height: 95vh;
}

@media amzn-kf8 {
		/* CSS for KF8 devices */
img.coverimage:only-of-type { /*overrides the previous setting, but only in newer systems that support CSS3 */
	 height: 95%;
}
img.fullim:only-of-type { /*overrides the previous setting, but only in newer systems that support CSS3 */
	height: 85%;
}
}

@media amzn-mobi {
		/* CSS for Mobi devices */
img.coverimage:only-of-type { /*overrides the previous setting, but only in newer systems that support CSS3 */
	 height: 95%;
}
img.fullim:only-of-type { /*overrides the previous setting, but only in newer systems that support CSS3 */
	height: 85%;
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
**HTML:**
`<p class="Endorsements">“This is an endosement”</p>`
`<p class="EndorsementAttri"><span class="AttriEndorseName">Endorser_Name</span>, Their titles</p>`

**CSS:**
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


## SVG etc
```
/* Cover & Title Page */

.cover {
	width:100vw;
	height:100vh;
	object-fit:contain; /* or :cover, which provides a more resposive experience, but will cut off the image if it is bigger than the container */
	object-position: center;
}

.title-page { /* Where posisble, use SVG. This will scale and be more responsive. SVGs can be created by: copy of material in InDesign and Paste in Place in Adobe Illustrator. Group, then rasterize the content. Right click on rasterized image and choose export as collection. THen choose SVG as the export option */
	width:100vw;
	height:100vh;
	object-fit:contain; /* or :cover, which provides a more resposive experience, but will cut off the image if it is bigger than the container */
	object-position: center;
}
```


### sup and sub
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
```