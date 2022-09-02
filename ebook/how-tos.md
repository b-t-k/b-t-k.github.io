---
layout: page
title: "Basic How Tos"
permalink: howtos/
---


{% include menu2.md %}


# Indesign
- add Object style: figure -> to images
- export Inline images also as figure


#epub
## Fonts
### Remove encryption
[] removed
1. \META-INF\encryption.xml
2. Re-add fonts
3. Run Sigil subset plugin

## Page list
1. pagestaker
2. epubogrify (not currently working)
1. pagestakesearch_droplet

## Hide pages
- spine (hidden) `linear="no"`

## DroptoScript
 - move lang:tag
 - fix titles (only H1)
 - clean classes
  - `"classMatch": "/_idGenCharOverride-\\d*/",`
	`"classMatch": "/_idGenParaOverride-\\d*/",`
	`"classMatch": "/_idGenDropcap-\\d*/",`
	`"classMatch": "/_idGenObjectLayout-\\d*/",`
	`"classMatch": "/_idGenObjectAttribute-\\d*/",`