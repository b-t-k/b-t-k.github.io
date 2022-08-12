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

### Page list
1. pagestaker
2. epubgrify

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