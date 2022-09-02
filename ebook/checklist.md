---
layout: page
title: "Checklist"
permalink: checklist/
---


{% include menu2.md %}


- deploy HTML 5 and clean up html
  - clean up all overrides
  - add href to urls
- edit the CSS down
- check navigation
  - standardize toc
  - add landmarks
  - add ncx
- add accessibility metadata
- check fonts (encryption and subsets)
- search and delete erroneous language declarations (extra fr or la etc.), move language declarations and fix emphasis and italics
- Add epub:type and ARIA roles
- run though epubchecker and Ace by DAISY

## Fix HTML
- change `<div>` --> `<section>`
- add urls (non space followed by dotcom followed by line break etc)

  - `([^\s]+)\.(ca|com|org|uk|au|edu).*?(?=\n|\.| |<)`
- doublecheck `<br/>`s

Check into `p.first-child` class — it needs to be added as `p:first-child` isn't respected

## Edit CSS
- see [base css](/ebook/)

## Check navigation
### toc
Check to see if it includes...
- remove pages from toc?


### Landmarks
**Minimum Landmarks**
```
<nav epub:type="landmarks" hidden="">
  <ol>
    <li><a epub:type="cover" href="cover.xhtml">Cover</a></li>
    <li><a epub:type="titlepage" href="copyright.xhtml#title">Title Page</a></li>
    <li><a epub:type="toc" href="toc.xhtml#TOC">Table of Contents</a></li>
    <li><a epub:type="bodymatter" href="chapter1.xhtml">Start of Content</a></li>
  </ol>
</nav>
```
**Possible Landmarks**
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

## Add accessibility metadata
[templates](/templates/)
- check textual or textual *and* visual

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

## Run checks
[] run epubcheck  
[] Ace by Daisy  
[] FlightDeck  







