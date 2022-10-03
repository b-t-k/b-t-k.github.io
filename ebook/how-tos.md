---
layout: page
title: "Basic How Tos"
permalink: howtos/
---


{% include menu2.md %}


# Indesign
- add Object style: figure -> to images
- export Inline images also as figure


#pdfs
- Use article panel to convey reading order


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

## image size limit: 4 million pixels

## DroptoScript
 - move lang:tag
 - fix titles (only H1)
 - clean classes
  - `"classMatch": "/_idGenCharOverride-\\d*/",`
	`"classMatch": "/_idGenParaOverride-\\d*/",`
	`"classMatch": "/_idGenDropcap-\\d*/",`
	`"classMatch": "/_idGenObjectLayout-\\d*/",`
	`"classMatch": "/_idGenObjectAttribute-\\d*/",`
	
# NOTES to sort
- Object export options 
- EPUB tab 
- relative to text flow
- Grouped image anchored and
- Rasterize container and customize alt text

Add object styles:
Export tag: figure
Alt text can use xmp data
Anchored object options

- Asides: navigated by header

## Indesign export hints

Auto leading for styles!
Copy and paste emages to clean document
Export as 1 chapter and split later

# Thngs to ponder 
 - filename conventions
 - Adobe Bridge (metadata; XMP)

 -  check python libraires