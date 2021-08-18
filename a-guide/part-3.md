---
layout: page
title: "A Step by Step for the Step by Step"
permalink: step-by-step/
---

{% include menu.md %}

# DRAFT NOTES ONLY!!!

## <a id="step_by_step"></a>Intro [↺](#toc)
This is just a brief look at the [step by step guide](https://standardebooks.org/contribute/producing-an-ebook-step-by-step) with a few additional hints/suggestions/explanations that might make it easier to understand if you are still struggling with the basics.

## About the Manual
- Bookmark the single page version: [https://standardebooks.org/manual/latest/single-page](https://standardebooks.org/manual/latest/single-page). You can now use the browsers search function (cmd-F on a Mac) to search the entire manual.
    - **Note:** the link will change to whatever the current version is e.g. *https://standardebooks.org/manual/**1.6.1**/single-page*, so be sure your bookmark is for *https://standardebooks.org/manual/**latest**/single-page*

## Definitions
- lint: "Lint, or a linter, is a static code analysis tool used to flag programming errors, bugs, stylistic errors and suspicious constructs." —[Wikipedia](https://en.wikipedia.org/wiki/Lint_(software)). The lint command is used to check for errors in your files.
 


## <a id="the_steps"></a>The Steps [↺](#toc)

### 1. The Tools
[Standard Ebook tools github](https://github.com/standardebooks/tools)
- check the GitHub site and scroll down to [Tool Descriptions](https://github.com/standardebooks/tools#tool-descriptions) to get an explanation of the available tools.
-**Note** that there are some extra tools there not mentioned in the various guides
- you can also always add the `-h` flag after a command to get a description of how to use it e.g. `se create-draft -h`
- if you use bbedit you can make scripts out of some of them and assign keyboard shortcuts. For example I have `se roman2dec` and `se titlecase` mapped to keyboard shortcuts.
Open the script editor (you might have to adjust the location of the tools):
```
tell application "BBEdit"
	tell window 1
		copy selection		
		set theString to the clipboard		
		set outputtext to do shell script "/Users/YOUR_USER_NAME/.local/bin/se titlecase " & "\"" & theString & "\""		
		set the clipboard to outputtext		
		paste		
	end tell
end tell
```

#### That funny dot
Most of the se commands need to act on a file or directory. `se split-file src/epub/text/body.xhtml` runs split-file on the body.xhtml file. But most of them ned to run on the whole project. So as long as your terminal is in proper directory e.g. pierre-choderlos-de-laclos_dangerous-liaisons_thomas-moore using the `.` will tell the command to act on the whole directory. Sometimes the Step-by-Step tells you to run command (like with `se find-mismatched-diacritics`) without specifically mentioning you have to run it with the dot at the end: `se find-mismatched-diacritics .` — just something to note.

### 2. Select an ebook
You will be ***strongly*** encouraged to pick a book off the [First Production List](https://standardebooks.org/contribute/wanted-ebooks) as your first project. Many people come to the list because they have a project in mind and balk at this restriction. After what is often a lot of argument, some reluctantly agree to do it the Standard Ebooks way and some depart unhappily. 

The reason for this restriction is two-fold. As a producer you will discover in some cases it is harder than it looks to balance the editorial and structural demands of a text (even little things like letters or posters can pose some tough semantic and coding problems). And length is a big factor in being able to balance the many dimensions of producing a quality project — many projects are abandoned each year because the producer just couldn’t sustain the effort. The other main reason is it is highly likely you will make errors on your first attempt and the reviewer assigned to you is left having to scrutinize not only the basics, but all that extra length and/or complexities involved in a longer, more complicated book.

So stick to something safe for the first book—and if you are new to coding, maybe the fist couple of books—before you strike out in an attempt to bring your favourite piece of literature to the world. The good new is that a first production was categorized as 40,000 words when I started and is now, thanks to improvements in the toolset, set at < 100,000 words.

Remember though, even given the restrictions you are free to use the methodology and toolset to produce your own book—it just won’t be eligible for inclusion in the Standard Ebook corpus.



### 3. Locate Page Scans

As a Canadian, finding texts (especially for cover searches) can often be problematic. Because of geo-blocking due to territorial rights and differing copyright periods often books that are freely available in the U.S. are not available to Canadian producers — I find Google Books especially frustrating on the score and rarely used it until I downloaded a tor browser and forced it to use an American-based location. 

There are often multiple sources for finding original texts and sorting through them to find the best, copyright free version is just another challenge you should be prepared to face.

- [Internet Archive](https://archive.org/) — The *go-to*. Start here when looking for page scans of pre-1925 books.
- [HathiTrust](https://www.hathitrust.org/) — Not quite as user-friendly as the Internet Archive, but a good source for scanned books if you strike out there.
- [Google books](https://books.google.com/) — As mentioned above, not as accessible to non-American locations.
- [Distributed Proofreaders](https://www.pgdp.org/ols/index.php) — The online home of the proofreaders who are supplying the main Gutenberg projects. Page scans are available as individual files so it makes it more cumbersome to work with.

#### Online or Download?
I used to only use the online version of the scans but more and more I have been downloading the pdf and having it open when I proof.  Often this can be faster and more convenient for comparison purposes than using the online version. But either way  works.

### 4. Create a skeleton
Standard form:
- `se create-draft --author="Pierre Choderlos de Laclos"  --title="Dangerous Liaisons" --pg-id=45512`

With translator:
- `se create-draft --author="Pierre Choderlos de Laclos" --translator="Thomas Moore" --title="Dangerous Liaisons" --pg-id=45512`

Remember you can always use the help files for adding translators etc.
`se create-draft -h`


### 5. Rough Cleanup
How rough can it get? You mainly have to get rid of all the cruft and leave only the basic body of the content including headers and titles.
 
Be sure to get rid of tables of contents, copyright pages and statements, title pages etc.

Leave in forewords, epigraphs, endnotes, afterwords etc. Occasionally you will end up dropping—or even adding in—extra material later but  as long as it resides in ints own file this can be done painlessly.


### 6. Split the text
If you are woking on something that isn't basic chapters (let's say they are named letter-1, letter-2 etc.), you can use `se split-file` to change the name (among other things).
- `se split-file -f letter-%n.xhtml src/epub/text/body.xhtml` 

**Hint** If you pull out any prefaces ore forewords into separate file before you run `split-file` then they will be numbered correctly and you can build the front matter files later. 

### 7. Clean the text
Sometimes it‘s broke — so you have to fix it. Running `se clean .` successfully relies on well-formed xhtml files. If there is an error somewhere in you project then it won't run. Occasionally I have had to run it , find and fix an error, run it again, find and fix and error etc. severe times before everything works.
- use a browser to help debug. If you open the problematic file in a web browser it will usually tell you where the problem is.
- the most common issue is  not closing the tags. If you have an opening <span> without the matching </span> then clean will complain. Occasionally the issue is widely spread such as when you accidentally delete a closing </section> and the error occurs at the opening one. Just take your time.

### 8. Typogrify
Pretty simple and straightforward. Make sure you run it more than just once, especially if you make changes. 

Make note of any typographical changes you revert by hand (sometimes there are a few), since you will have to do it again every time your run typogrify.

### 9. Endnotes & Illustrations
Not for beginners. More on this when I have this chance.

### 10. Convert British to America
*Single quotes? WTF mate?*

Often old  texts will have the use of quotes reversed from how we usually do it here in North America and instead uses single quotes around quotations. Running the `se british2american .` will switch them to double.

This will never be perfect so you will have to double check manually.

### 11. Add Semantics
*Coming soon*


### 12. Modernize Spelling
- how far to go. And when?


### 13. Diacritics
*Coming soon*


### 14. Title Elements
- but I already did this?


### 15. Build Manifest and Spine
*Coming soon*


### 16. Build ToC
*Coming soon*


### 17. Clean and Lint
- what, you haven’t done this yet?
- always changing and improving


### 18. Build and proofread
*Coming soon*


### 19. Create the Cover
Yes, he's serious; no, you can't do that; yes it's **hard**

Preview can:
- Adjust the size with Tools/Adjust Size. I use this more often for downrezing than up; e.g. if a picture is 3000h x 4500w, depending on what crop I want, I might resize it to 2200h x <whatever that would turn out to be>w. Preview will scale proportionally as long as the checkbox is checked, which it is by default, so you only have to specify one dimension.
- Identify a crop just by clicking and dragging the cursor (it shows you the dimensions as you drag, so you can see when you get to 2100x1400), then typing Cmd-C to copy it, and Cmd-N to open a new Preview window with that crop displayed full size in it, where it can then be saved, etc. The default file is PNG, so you have to change the file type before saving.
- It can also do rudimentary visual adjustments via Tools/Adjust Color, e.g. exposure, contrast, temperature, etc. The usual major things you see in a photo editor.
- It can also flip and rotate if needed.
#### Possible sources
- Alex’s spreadsheet” [https://docs.google.com/spreadsheets/d/1BqmDx4EvkRxbJAijFBIZOkawyflGBMJzom-fVhLC5-0/edit#gid=557113123]
- David’s PD Website [https://rightword.com.au/gallery/all-images/]

#### Gigapixel
- ask and you shall receive

### 20. Complete content.opf
**Lots more to come**

#### Library of Congress
You can search subject headings here:
[http://id.loc.gov/authorities/subjects.html]

#### Escaped HTML
You need to use escaped html text for the long description in the content.opf file. But you also need to ensure that each paragraph is indented by 3 tabs. This might be corrected by the latest version of lint.
- [Escaped text webpage](https://www.freeformatter.com/xml-escape.html) — You will be asked to use escaped text for the long description and this site can help do that automatically.

### 21. Imprint & Colophon
*Coming soon*
- multiple sources

### 22. Final Checks
*Coming soon*


### 23. Initial Publication
- ignore this, it’s a red herring!




