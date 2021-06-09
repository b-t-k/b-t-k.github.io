---
layout: page
title: "A Step by Step for the Step by Step
permalink: /step-by-step/
---

{% include menu.md %}

# DRAFT NOTES ONLY!!!

# <a id="step_by_step"></a>Intro [↺](#toc)
This is just a brief look at the [step by step guide](https://standardebooks.org/contribute/producing-an-ebook-step-by-step) with a few additional hints/suggestions/explanations that might make it easier to understand as you go along.

## <a id="the_steps"></a>The Steps [↺](#toc)



### 1. The Tools
*Coming soon*



### 2. Select an ebook

You will be ***strongly*** encouraged to pick a book off the [First Production list](https://standardebooks.org/contribute/wanted-ebooks) as your first project. Many people come to the list because they have a project in mind and balk at this restriction. After what is often a lot of argument, some reluctantly agree to do it the Standard Ebooks way and some depart unhappily. 

The reason for this restriction is two-fold. As a producer you will discover in some cases it is harder than it looks to balance the editorial and structural demands of a text (even little things like letters or posters pose some semantic and coding problems). And length is a big factor in being able to balance the many dimensions of producing a quality project—many projects are abandoned each year because the producer just couldn’t sustain the effort. The other main reason is it is highly likely you will make errors on your first attempt and the reviewer assigned to you is left having to scrutinize not only the basics, but all that extra length and/or complexities involved in a longer, more complicated book.

So stick to some thing say for the first book—and if you are new to coding, maybe the fist couple of books—before you strike out in an attempt to bring your favourite piece of literature to the world. The good new is that a first production was categorized as 40,000 words when I started and is now, thanks to improvements in the toolset, set at < 100,000 words.

Remember though, even given the restrictions you are free to use the methodology and toolset to produce you own book—it just won’t be eligible for inclusion in the Standard Ebook corpus.



### 3. Locate Page Scans

As a Canadian, finding texts (especially for cover searches) can often be problematic. Because of geo-blocking due to territorial rights and differing copyright periods often books that are freely available in the U.S. are not available to Canadian producers—I find Google Books especially frustrating on the score and rarely use it. 

There are often multiple sources for finding original texts and sorting through them to find the best, copyright free version is just another challenge.

- [Internet Archive](https://archive.org/) — The go-to. Start here when looking for page scans of pre-1925 books.
- [HathiTrust](https://www.hathitrust.org/) — Not quite as user-friendly as the Internet Archive, but a good source for scanned books if you strike out there.
- [Google books](https://books.google.com/) — As mentioned above, not as accessible to non-American locations.
- [Distributed Proofreaders](https://www.pgdp.org/ols/index.php) — The online home of the proofreaders who are supplying the main Gutenberg projects. Page scans are available as individual files so it makes it more cumbersome to work with.



### 4. Create a skeleton
*Coming soon*



### 5. Rough Cleanup
- how rough can it get?



### 6. Split the text
- gotchas



### 7. Clean the text
-but sometimes it's broke


### 8. Typogrify
*Coming soon*



### 9. Endnotes & Illustrations
- not for beginners


### 10. Convert British to America
-single quotes? WTF mate?


### 11. Add Semantics
*Coming soon*


### 12. Modernize Spelling
- how far to go. And when?


### 13. Diacritics
*Coming soon*


### 14. TItle Elements
- but I already did this?


### 15. Build Manifest and Spine
*Coming soon*


### 16. Build ToC
*Coming soon*


### 17. Clean and Lint
- what, you havent done this yet?


### 18. Build and proofread
*Coming soon*


### 19. Create the Cover
- yes, he's serious; no, you can't do that; yes it's **hard**
Preview can:
- Adjust the size with Tools/Adjust Size. I use this more often for downrezing than up; e.g. if a picture is 3000h x 4500w, depending on what crop I want, I might resize it to 2200h x <whatever that would turn out to be>w. Preview will scale proportionally as long as the checkbox is checked, which it is by default, so you only have to specify one dimension.
- Identify a crop just by clicking and dragging the cursor (it shows you the dimensions as you drag, so you can see when you get to 2100x1400), then typing Cmd-C to copy it, and Cmd-N to open a new Preview window with that crop displayed full size in it, where it can then be saved, etc. The default file is PNG, so you have to change the file type before saving.
- It can also do rudimentary visual adjustments via Tools/Adjust Color, e.g. exposure, contrast, temperature, etc. The usual major things you see in a photo editor.
- It can also flip and rotate if needed.

#### Gigapixel
- ask and you shall recieve

### 20. Complete content.opf

#### Escaped HTML
You need to use escaped html text for the long description in the content.opf file. But you also need to ensure that each paragraph is indented by 3 tabs. This might be corrected by the latest version of lint.
- [Escaped text page](https://www.freeformatter.com/xml-escape.html) — You will be asked to use escaped text for the long description and this site can help do that automatically.
- finding errors: (coming


### 21. Imprint & Colophon

*Coming soon*

### 22. Final Checks
*Coming soon*


### 23. Initial Publication
- ignore this, its a red herring!




