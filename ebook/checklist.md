---
layout: page
title: "Checklist"
permalink: checklist/
---


{% include menu2.md %}

# epub Checklist
- deploy HTML 5 and clean up html
  - clean up all overrides
- edit the CSS down
- check navigation
  - standardize toc
  - add landmarks
  - add ncx
- add accessibility metadata
- check fonts (encryption and subsets)
- search and delete erroneous language declarations (extra fr or la etc.), move language declarations 
- fix emphasis and italics, bold and strong etc. 
- Add epub:type and ARIA roles
- add external https links and urls
- run though epubchecker and Ace by DAISY
- Flightdeck if available

# Accessibility Checklist
1. Semantics, i, em lang etc.
2. Double check `<li>` structures
1. Proper alt descriptions and decorative images
2. Proper hierarchy
1. Correct sectioning and ARIA roles
1. Page lists
1. Navigation: landmarks 
1. LOI and LOT (list of tables)

## Fix HTML
- change `<div>` --> `<section>`
- add urls (non space followed by dotcom followed by line break etc)

  - `([^\s]+)\.(ca|com|org|uk|au|edu).*?(?=\n|\.| |<)`
- doublecheck `<br/>`s

Check into `p.first-child` class — it needs to be added as `p:first-child` isn't respected

### Specific changes
- context breaks --> `<hr/>`

## Edit CSS
- see [base css](/ebook/)

## Check navigation
### Nav toc
- add in all extras (i.e. bio, about, etc) not in print ToC
- leave toc.xhtml as is


### Landmarks
**Minimum Landmarks**
```
<nav epub:type="landmarks" hidden="">
  <ol>
    <li><a epub:type="cover" href="cover.xhtml">Cover</a></li>
    <li><a epub:type="frontmatter" href="copyright.xhtml#title">Preface</a></li>
    <li><a epub:type="toc" href="toc.xhtml">Table of Contents</a></li>
    <li><a epub:type="bodymatter" href="chapter1.xhtml">Start of Content</a></li>
    <li><a epub:type="backmatter" href="afterword.xhtml#title">Afterword</a></li>
    <li><a epub:type="loi" href="loi.xhtml">List of Illustrations</a></li>
  </ol>
</nav>
```
#### Possible Landmarks
- cover – the book cover(s), jacket information, etc.
- toc – table of contents
- bodymatter – First "real" page of content (e.g. "Chapter 1")
- title-page – page with possibly title, author, publisher, and other metadata
- frontmatter
- backmatter
- loi – list of illustrations
- lot – list of tables
- preface
- bibliography
- index – back-of-book style index
- glossary
- acknowledgments

According to Laura Brady extensive landmarks are not really used. You can limit it to:
COVER  
FRONTMATTER  
BODYMATTER  
BACKMATTER  
LOI etc.  


## Add accessibility metadata
[templates](/templates/)
- check textual or textual *and* visual

## Metadata
<dc:source id="src-id">urn:isbn:9780765331458</dc:source>

?????? <meta property="identifier-type" refines="#uid" scheme="onix:codelist5">15</meta>

## Fonts
### Remove encryption
[] removed
1. \META-INF\encryption.xml
2. Re-add fonts
3. Run Sigil subset plugin


## Language declarations
- clean up extra from indesign
- move lang declaration to header
  - `<html xmlns="http://www.w3.org/1999/xhtml" xmlns:epub="http://www.idpf.org/2007/ops" lang="en-CA" xml:lang="en-CA">`
- add tags `<span xml:lang="fr">xxx</span>`
- check `<em>` vs `<i>` etc.

## Add ARIA roles and double check epub:type
- [Daisy aria roles](https://kb.daisy.org/publishing/docs/html/dpub-aria/)
- check spreadsheet (/Projects/ Ebook Production/Doc-roles.xlsx)
- avoid overuse of ARIA roles

## Run checks
[] run epubcheck  
[] Ace by Daisy  
[] FlightDeck  



# Indesign Checklist
(https://helpx.adobe.com/indesign/using/export-content-epub-cc.html)
Alt text via object export style
Story order via articles or Story

Preserve appearance
image object styles?
sidebar object styles
adjust iamges manually

