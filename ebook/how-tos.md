---
layout: page
title: "Basic How Tos"
permalink: howtos/
---


{% include menu2.md %}


# Indesign
- add Object style: figure -> to images
- add object style: aside -> sidebars
- export Inline images also as figure


# pdfs
- Use article panel to convey reading order


# xml:lang
Subtags: [https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry)

**Non-linguistic** Use the subtag *zxx* when the text is known to be not in any language.  
`xml:lang="zxx"`
`<p>Here is a list of part numbers: <span xml:lang="zxx">9RUI34 8XOS12 3TYY85</span>.</p>`

**Undetermined**:
`xml:lang="und"`  
*However you should only tag text as undetermined if you can't just leave it as is. In practice, this means you should only use this markup if the undetermined text is embedded in content that has already been labeled for language in some way.*


Athapascan languages ath  
Blackfoot/Siksika bla  
Chinook jargon (Chinuk Wawa) chn  
Chipewyan chp  
Cree cr  
Dakota (Sioux) dak  
Delaware (Munsee) del  
Dogrib (Tli Cho) dgr  
Haida hai  
Inuktitut iu  
Inupiaq ik  
Kutenai (Kootenai) kut  
Micmac; Mi'kmaq mic  
Mohawk moh  
Ojibwa oj  
Salishan languages (salish) sal  
Slave (Athapascan) den  
Tlingit tli  
Tsimshian tsi  
Wakashan languages wak  
[https://www.nationsonline.org/oneworld/language_code.htm](https://www.nationsonline.org/oneworld/language_code.htm)

# epub
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