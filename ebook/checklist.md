---
layout: page
title: "Checklist"
permalink: checklist/
---

{% include menu2.md %}

## fonts
### Remove encryption
[] removed
1. \META-INF\encryption.xml
2. Re-add fonts
3. Run Sigil subset plugin

## Run checks
[] run epubcheck  
[] Ace by Daisy  
[] FlightDeck  

## Basic Edits
- add aria roles
- change <div> —> <section>
- add urls (non space followed by dotcom followed by line break etc)
```
([^\s]+)\.(ca|com|org|uk|au|edu).*?(?=\n|\.| |<)
```
- remove pages from toc?
- doublecheck <br/>s

- check landmarks etc

Objectstyle figure->to images
Inline images also as figure

- spine (hidden) `linear="no"`
### Page list
1. pagestaker
2. epubogrify (not currently working)
1. pagestakesearch_droplet

#### fixes
1. DroptoScript
 - move lang:tag
 - fix titles (only H1)
 - clean classes
  - `"classMatch": "/_idGenCharOverride-\\d*/",`
	`"classMatch": "/_idGenParaOverride-\\d*/",`
	`"classMatch": "/_idGenDropcap-\\d*/",`
	`"classMatch": "/_idGenObjectLayout-\\d*/",`
	`"classMatch": "/_idGenObjectAttribute-\\d*/",`

##