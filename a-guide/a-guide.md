---
layout: page
title: "A non-programmers guide to contributing to Standard Ebooks"
permalink: /a-guide
---

![standard ebooks logo](/images/selogo.png)

### <a id="toc"></a>Table of Contents
1. [Introduction](#introduction)
2. [Key Concepts](#key_concepts)
3. [Tools](#tools)
4. [Get Started](#get_started)
5. [Methodologies](#methodologies)
	1. [BBEdit](#bbedit)
	2. [Search & Replaces and Regexes](#search_replaces_and_regexes)
	1. [CSS](#css)
6. [Hints & Tips](#hints_tips)
	1. [Handy links](#handy_links)
	2. [My Notes](#my_notes)

## <a id="introduction"></a>Introduction <span class="notbold">[↺](#toc)</span>
### Why this guide
[Standard Ebooks](https://standardebooks.org/) is a project started by Alex Cabal that…
> takes ebooks from sources like Project Gutenberg, formats and typesets them using a carefully designed and professional-grade style manual, fully proofreads and corrects them, and then builds them to create a new edition that takes advantage of state-of-the-art ereader and browser technology.
It is a volunteer driven project. If you are interested in  adding to the availability of public domain literature or just want to learn about how ebooks are made, this is a great project to take part in.

The downside is that it is very programmer-centric. A lot of what you need to know/do for complicated projects is beyond the ken of your basic computer user. But thankfully, with SE’s [detailed instructions](https://standardebooks.org/contribute/producing-an-ebook-step-by-step) and the provided [SE toolset](https://github.com/standardebooks/tools), getting started on basic projects is well within the means of the average user. You just have to have a grasp of some basics first.

And that’s what this tutorial is all about. I think it would be great if more of the right-brained set became a part of the project and I thought I would see if I could lay out the basics. 

Be sure to visit the [Contributors page](https://standardebooks.org/contribute) if you want see the various ways you can help out even if this guide still leaves you too nervous to give it a try. 

#### Disclaimer
A lot of my terms and concepts are not going to be strictly accurate. For one, I don’t actually understand some of them myself, and for two, the analogies I offer are just that: analogies. You can do more research yourself if you really want to know more about what’s going on. My aim is just to demystify some of the more intimidating steps. Feel free to correct me if I am egregiously misleading anyone.

### OS X-centric
I am a Mac user. Most of what I write here will be focussed on working with a Mac. There won’t be much difference if you are using Linux (but then I assume by dint of being a linux user this guide won’t be as applicable to you) and if you are a Windows user the basics still apply but you will have to adjust your tools to suit the platform.

## <a id="key_concepts"></a>Key concepts <span class="notbold">[↺](#toc)</span>
To make an ebook you are, at root, making something very similar to a website. One that is packaged according to some very specific rules. This means that a working knowledge of html and css is helpful—but don’t let that daunt you. You will also need to get over any nervousness you have regarding the *command line prompt*. That’s that thing that looks like an olde-tymie computer interface with a blinking prompt, where you have to enter arcane, and often incomprehensible, commands. But don’t worry—most times it's simply a matter of cut and paste.

### Accessibility
One of the keys to understanding how and why a Standard ebook is formatted the way it is, is realizing it is designed to be as *accessible* as possible — that means it can be used on multiple readers including screen readers for the visually impaired. As an example, it’s important that the computerized reader can distinguish between the article “I” and the Roman numeral I —something our brains do automatically. So if in the course of working on a project you are confused about whether to mark something up or not, a good touchstone is to ask yourself if a computer would be able to distinguish what it is without further context.

Metadata is also very important to the overall accessibility of the ebook. But more on that later.
 
### html & css
Html is the “programming” language used to make web pages. It has a few conventions you will need to know.

#### tags
Html (hyper text markup language) is formed by surrounding text with tags. Each tag set has an opening and a closing tag. The web browser (or in this case reader)  reads the text between the tags and intreats according to the appropriate html rules. For example `p`, the tag that marks paragraphs is used like this: 

> `<p>This is a paragraph. It may have all sorts of text in it.</p>`

The text will then be displayed as a paragraph with whatever settings (first line indent, space after etc.) that have been assigned to paragraphs.

Some common html tags you will need to know: 
- **emphasis**: `<em>…</em>` — This is used in place of italics in most cases.
- **italics**: `<i>…</i>` — generally only used where italics are grammatically correct e.g. foreign languages, names of books etc.
- **strong**: `<strong>…</strong>` — This is used instead of bold in almost all cases.
- **bold**: `<b>…</b>` — very rarely used.
- **span**: `<span>…</span>` — generally used mid-sentence to surround something you might want to add information to when it isn’t appropriate to use any of the above tags i.e.`<span class="poetry"> ... </span>`. We will get into classes later.
- **br**: `<br/>` — an exception to the opening/closing tag rule, a br (break) is a line break that goes at the end of a line where you want it to break. The forward slash at the end indicates it is acting as both an opening and closing tag.
- **hr**: `<hr/>` — another exception. The hr (horizontal rule) tag is used to indicate section breaks that are usually shown by white space or glyphs (e.g. * * * ) in a printed book.
- **abbr**: `<abbr>Mr.</abbr> James <abbr>H.</abbr> Smythe-Jones` — Indicates abbreviations, all of which should be marked appropriately in Standard ebooks—otherwise how would a screen reader know who to pronounce them?
- **blockquote**: Essentially a ‘quote’ that is formatted to stand out from the rest of the text e.g. a letter or a sign

```
 <blockquote> 
      <p>May contain multiple paragraphs<br/>
      lines, or other parts.</p>
 </blockquote>
```


##### CSS & Classes
Many tags accept additional parameters which are part of the CSS (Cascading Style Sheet) file. This is where you would set such things as the size of the `p`’s first line indent or top and bottom margins.

A Standard ebook usually has 3 style sheets (core.css, se.css, and local.css) found in the css folder. The only one you as a producer will ever touch is **local.css** — at the beginning of the project it will be empty.

Briefly, the purpose of css is to define the standard style and then allow you to add “custom” styles to tags and blocks of text. For example if you want the signature line of a letter to be right justified you could enclose that line in a `p` tag and add a class: `<p class=“signature”>Bob Smith</p>`. You would then add the appropriate css to the local.css stylesheet:

```
.signature{
    `text-align: right;
}
```

But don’t worry. Almost all of the necessary css for a beginner is detailed in [The Standard Ebooks Manual of Style](https://standardebooks.org/manual/latest) and is simply a matter of cutting and pasting.

###### Semantics
Adding classes is a huge part of a Standard ebook production, in general referred to as semanticating. Adding semantics to individual parts of the text is very important to the well-formed nature of the final product and takes a lot of time and close reading to get correct, especially in more complex productions like plays or epistolary texts. More about that later.

### Ebook Structure
We talked about what an ebook is: essentially a self-contained website. The constituent files have been compressed into an archive and that forms the basic epub file. When you start a new Standard ebook project a basic template will be created for you. But here is a brief description of the parts you will need to understand:
- **content.opf** — This is the file that houses most of the metadata about the book and contains the “manifest” which details all the constituent parts of the ebook, and the “spine” which sets out the reading order.
- **css folder** — Contains all the css files to control how the book looks. Remember you will only ever edit the local.css file.
- **images folder** — Contains the cover image (which is generated as one of the production steps).
- **toc.xhtml** — The Table of Contents. Automatically generated but *very* occasionally will need to be tweaked.
- **text folder** — Contains the text files for your project including several standard files common to all Standard ebook projects: title page.xhtml, chapter-1.xhtml etc.

### xhtml
Html stands for *hypertext markup language* and is the basic format that web browsers read. XML stands for *extensible markup language* and can be thought of as a “programable” version of html. The ebook is based on xhtml files which are, in a way, just a mashup of the two.

![xhtml](/images/xhtml_before.png "xhtml")  

*Code view*

![xhtml](/images/xhtml_after.png "xhtml in epub")  

*Epub view*

If you open an xhtml file in your web browser it will appear just like a web page — handy for proofing and checking if and where any errors might be lurking.

<img src="/images/xhtml_web.png" width=“400" alt=“xhtml on the web">
<img src="/images/screen_error.png" width=“400" alt="errors on the web">

*Sometimes using a web browser can be a convenient way of finding errors.*

### Metadata
Coming Soon
- purpose
- format


### Output File Types
Coming Soon: Epub, kepub, azw3 and advanced pub (epub3)
 
### Python, Brew and the Command line
This is the programming stuff. But it’s not actually as daunting as it seems. Cut and paste is your friend, and along the way you will continue to build on your knowledge until soon you can strikeout on your own :-)

#### Terminal
Most of the Standard ebook tools are not housed in a GUI (Graphical User Interface) — the thing you point and click with your mouse. You will need to become fairly comfortable with the terminal interface to work on a project. But again it’s mostly cut and paste from the [Manual](https://standardebooks.org/manual/).

*Terminal* can be found by searching for terminal using Spotlight (Cmd+space) or navigating to to *Applications: Utilities* and double click on the Terminal icon. We will talk more about this later, but you will need to the program in order to install the tools.

#### Brew 
To install and maintain the tools on a Mac you use the [Homebrew package manager](https://brew.sh/). This is similar to an “app store” — basically some non-gui software that leaves the heavy lifting of installing and updating to someone else. There are instructions on the [tools Github](https://github.com/standardebooks/tools) (More on Github in the next section) to get up and running. IN a nutshell you will copy the command from   the website into terminal and hit enter. At this point the this is the command (but it may changes be safe and copy it from the website).

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)”`

It will take some time, all the while your terminal will be spitting out lines and line of gibberish. Just ignore and have a nice cup of tea or coffee.

#### Python
Standard Ebooks has a toolset that is based on the Python programming language. When you install the Standard Ebooks [tools](https://github.com/standardebooks/tools) it will install the latest version of Python 3 for you, so *dinnae fash yersel* as the Scots might say.

Just follow the step by step in the tools repository README.md. Remember it’s all cut-and-paste. 
- `brew` commands install the support software that the tools need to use
- `pipx` commands install the python programs
- `sudo` is a terminal command that allows the the install to take place at *root* level i.e as an administrator. It will likely  ask for your password for permission.

I would ignore the *Optional* elements at the this point unless you know what they mean. From time to time you be required to update the SE software as new versions come out.

### Github
[Github](https://github.com/) is a website that employs [Git](https://www.atlassian.com/git/tutorials/what-is-git), a source control system. Normally used as a way of managing source code (and if you think about it, that’s what making an ebook essentially is), it’s what Standard Ebooks uses to manage and control the various projects. I am a real noob at using `Git` and Github and I frequently have to resort to using google-foo to figure out how to fix what I did wrong.

In a nutshell, `Git` is a process to exercise version control over your project and Github is a website that allows you store this online. You create an initial repository (with the folder containing your files) and as you move through the steps, you sync your local version to the GitHub website. This allows you to keep track of the steps you have taken and, more importantly, to revert any changes you made that weren’t appropriate or were outright mistakes. The repository is often referred to as the repo.

You will have to create a [GitHub account](https://github.com/).  Its pretty standard and once you are signed up you will have your own place to store your work as you progress. 

When a project is finalized and approved then Standard Ebooks will clone it to their [own GitHub repositories](https://github.com/standardebooks/) in preparation to publishing. Incidentally those repos give you access to all the ebooks that have been already published, providing a plethora of examples on how to solve various issues.

### A brief introduction to Regular Expressions (regex)
Regular Expressions, generally known as regexes, are, roughly speaking, a way to search and manipulate text through a series of wildcards and pattern matching. I will freely admit that, while I am pretty bad at constructing proper regexes, I am a huge fanboy. Imagine being able to replace every instance of a particular word in the first paragraph of a chapter across multiple files with Title Case. It saves a whole lot of legwork. Standard Ebooks step by step includes a bunch of regexes to replace a lot of manual labour, and you can quickly learn to build some yourself.

More on this later. Much more.

***

Ok enough background. I remember this making my head explode way back when, but remember it’s made a lot easier by the range of tools you use to manage everything. Which is what the next section is about.

But to review:
- ebooks are essentially packaged websites
- Standard Ebooks are designed  to be well formed and accessible
- Python is as easy as cut & paste.
-Github will try to be your friend. Let it.

## <a id="tools"></a>Tools [↺](#toc)
Ok. Now we are into the meat of it. This is my setup. There are many ways to skin this particular furry mammal but this is what I use. Try to remember that each tools can be approached by ignoring 90% of its functionality and you can add in  bits and pieces as they start to make sense.

### BBEdit & Text Editors
[BBEdit](https://www.barebones.com/products/bbedit/index.html) is basically a text editor — but it is one especially designed for coding. There are a lot of other options ([Visual Studio Code](https://code.visualstudio.com/), [Brackets](http://brackets.io/) etc.), all of which are more or less free.

And, in case you haven’t figured it out, editing text is a large part of what making an ebook is about. And editing text means exactly that: you will be editing raw text. Not rich text with bolds and italics and definitely not word processor text with all sorts of hidden code. Raw [ASCII](https://en.wikipedia.org/wiki/ASCII) text. 

The advantage of BBEdit (or other code editors) is that it allows you to work more efficiently — you can do things like open entire folders in one window; or do regex-based search-and-replaces across the entire project. Its a tool mostly designed to doing exactly this job, s while you can use textedit why not use something that will bring added functionality the process?

### Github Desktop
As I mentioned above, you will have to use Github. Access to Github is generally managed using the command line. It is one of the more arcane processes when working on a project — frankly it almost made me give up when I first started. Thankfully I found [Github Desktop](https://desktop.github.com/) which is a GUI interface, which brought most of the process back to the click-my-mouse world and that made my life a lot easier.

Github Desktop provides a visual/graphical tool to manage your repository. I pretty much ignore the command line when using git and GitHub these days. The general sequence is that any changes you make in a file will be represented in the Github Desktop GUI. You elect which files you want to sync; give that selection a name (e.g. initial commit or fixed typo) and then “commit” it. Then you can “push” the various commits up to the website or undo them.

![GitHub Desktop](/images/github-desktop.png "A GitHub Desktop window")

The red highlighted text above was the original, the green highlighted text contains the sole change I made between versions.

### Terminal
On a Mac the command line interface is accessed through a program called *Terminal*. Simply hit cmd-spacebar and type "terminal" or go to *Applications: Utilities* and double click on the Terminal icon.

Terminal is an app like any other, but it opens a window into the functions that underpin how your computer works. Anyone who remembers the DOS days will already be familiar with the concept.

It's helpful to know a bare minimum of Terminal commands. Depending on how old your OS is you will likely be using *bash* or *zsh* as your shell (this is inherited from the unix underpinnings of OSX) but you don’t really need to know about that beyond perhaps wanting to google “bash how to change directory” or something similar.

![terminal window](/images/terminal.png "A Terminal window")

When you open Terminal it will give you a prompt similar to `bob@my-mac ~ %`. As I said it will vary from shell to shell. You will generally start in your user/home folder. If your user name is Bob then it will be in the Bob ‘home’ folder. Typing `ls` and hitting enter will list the folders and files so you can check if that’s where you are—you can compare it to the Finder window and should be able to see exactly the same files and folders.

#### Basic terminal commands
- **`ls`** list — lists files and folders
- **`cd`** change directory — allows you to change your directory. For example `cd /bob/Documents/Projects` would switch you to the Projects folder found in your Documents folder. Just like if you had double-clicked on the Document folder and then double-clicked on the Project folder.
 - Don’t panic! You can — and I always do — simply type `cd` followed by a space and then drag the folder you want to be in from the Finder onto Terminal and, voila, you have the correct path name automatically ready for you to hit `enter`. Saves on the frustration.
 
![terminal window](/images/terminal-directory.png "A Terminal window with a directory")

- **`cd ..`** Change directory up one level. If you are in /Projects/Bob’s Book and you want to be in /Projects/ this will do the trick.

And finally there is a whole raft of Standard ebook commands that are again cut and paste from the guide. Here’s a common one: 
 - **`se clean .`** This tells terminal to use the `se` toolset, find the command `clean` and apply it to all the files and folders in the current directory `.` .
You will primarily be using Terminal to invoke these sorts of SE toolset commands. This one cleans up the files, removes extraneous spaces and returns and then lines everything up neatly.

### Photoshop/GIMP
The last tool you will have to use is an image editor. All you really need to use it for will be to crop the final cover image to exactly 2100 pixels by 1400 pixels, but occasionally you might want to colour correct the image a bit or edit out a bad scratch.

I have Photoshop as a part of my working suite but [GIMP](https://www.gimp.org/) is a totally free and open source image editor that is pretty highly regarded.

### Ebook Reader
Of course it always good to have a stand alone ebook reader( i.e. a Kindle or a Kobo) to try out your projects on but a desktop one is easier (in my opinion) to use when proofing. I generally use the built in Apple Books, but occasionally also use the Calibre ebook reader built into the excellent [Calibre e-book Management](https://calibre-ebook.com/) software. There are plenty of options out there.


## <a id="get_started"></a>Get Started [↺](#toc)
So. Time to start. First off you need to subscribe to the [Standard Ebooks Google Group](https://groups.google.com/g/standardebooks) which is where 99% of the communication back and forth happens.

Then you need to visit [Wanted Books](https://standardebooks.org/contribute/wanted-ebooks) page and find a book that appeals to you from the **First Production** section. Alex (and everyone else who has reviewed a book project) will strongly discourage you from choosing a book that isn’t on the list for a first project. Not only do you have to learn all the ins and outs but then a reviewer has to go through it closely to ensure you’ve done everything correctly. The longer and more complex the book, the harder it is for both parties. After you've done your first project successfully you will likely be invited to try something a bit harder.

Start a new thread in the Google Group and send off a note with your chosen book and wait (patiently) to see if it's approved. Then you are on your way and can follow the [Step by Step](https://standardebooks.org/contribute/producing-an-ebook-step-by-step).


For your first projects you should start by following the provided *Step by Step* pretty closely, feeling free to ask questions as often as necessary. People are generally pretty helpful with beginners but a lot of it can be found in the manual if you look there first.

***

# <a id="methodologies"></a>Methodologies [↺](#toc)
This section focuses a bit more on specific methods I use, some hints and tricks I have discovered along the way and some in-depth tips on specific actions.

## <a id="bbedit"></a>BBEdit [↺](#toc)
### opening projects
Open the project using File:Open but then click on the folder containing the project instead of any individual file and hit Open. 

![bbedit window](/images/bbedit-folder.png "BBEdit folders"")

Now you can open individual files simply by selecting them in the left column.

![bbedit window](/images/bbedit-openfolder.png "BBEdit folders open")

### Change Case
The SE toolset offer a way to change case, but frankly the workflow I’ve developed makes using BBEdit’s built in Change Case function. Out of the box there is no keyboard shortcut assigned to the various change case functions—
- All Upper Case,
- All Lower Case,
- Make Title Case,
- Capitalize Words,
- Capitalize Sentences,
- Capitalize Words.

But BBEdit is highly customizable and it is easy enough to go to *BBEdit > Preferences > Menus & Shortcuts > Text* and assign a keyboard shortcut to any one of the above (or any other menu function).

### External scripts
BBEdit also offers a way to run external scripts to extend its functionality. I have made a few to cover some of the more repetitive tasks like “rename file to clipboard” and “lowercase and dashes” (makes text url friendly) which you do a lot of when making headers for compilations and these again have keyboard shortcuts assigned to them. 

Macs come with a program called *Script Editor* and it’s pretty easy to write (or download) simple scripts:

**Rename Active Document to clipboard.scpt**
```
on run
	tell application "BBEdit"
		activate
		
		set doc to active document of text window 1
		set oldName to name of doc
		set newName to my promptForName(oldName)
		-- If the name did not change we can bail.
		if newName = oldName then return true
		my renameDoc(doc, oldName, newName)
		
	end tell
end run
```

**lowercase and dashes.scpt**
```
tell application "BBEdit"
	tell window 1
		change case selection making lower case with replacing target
		copy selection
		set theString to the clipboard
		set L to length of theString
		set P to the offset of space in theString
		repeat until P = 0
			if P = 1 then
				set theString to "_" & texts 2 through -1 of theString
			else if P = L then		
				set theString to texts 1 through (L - 1) of theString & "_"
			else
				set theString to texts 1 through (P - 1) of theString & "-" & texts (P + 1) through -1 of theString
			end if
			set P to the offset of space in theString
		end repeat
		set the clipboard to theString
		paste
		select
	end tell
end tell
```
There are lots of help files available but essentially you can just drop these files in the BBEdit scripts folder and then assign a shortcut to them.

### Search and Replaces
This is where using an editor like BBEdit shines. Much of the work you do in creating a Standard ebook is searching out patterns created by the original producer and replacing them with a properly formatted ‘standard’ pattern. BBEDit’s *Multi-File Search* can make short work of a lot of the tediousness.

Remember to open your project (see above) rather than individual files. The select *Multi-File Search* and ensure your project folder is selected in the *Search in:* box. You will also want to ensure that in most cases Case Sensitive, Entire Word and Grep are selected. Grep stands for “global regular expression print” and is the utility that uses any regexes you build to search the files.

![multi file find window](/images/multi-file.png "BBEdit Multi-file find")

The search and replace in the image will find words in all caps and replace them with upper/lower. We will look at the specifics of that later.

## <a id="search_replaces_and_regexes">Search & Replaces and Regexes [↺](#toc)
**Coming soon:** 
- a beginners guide to regexes
#### BBEdit searches

#### A Basic Pattern
Let's say you wanted to search for `<h2>This is the title</h2>` and replace it with `<h2 epub:type="title">This is the title</h2>`. First you identify the pattern, which in this case is text between two `<h2>` tags. Then you build a regex to identify this pattern:
- `<h2>.*?</h2>`

The `.*?` wildcards will find the `<h2>` tags with all text and characters between the two h2s. But in order to replace it we need to copy the text between the tags into the replace statement. This is accomplished by placing the wildcard pattern between in parentheses: `(.*?)`. This essentially writes that text into memory and can then be called back on the replace statement using a backslash and the number of the occurrence. So...

Find: `<h2>(.*?)</h2>`

Replace: `<h2 epub:type="title">\1</h2>`

Or if you had multiple tags you wanted to replace or delete like getting rid of the extra tags in the opening paragraphs: `<p class="nind">A <small>GIRL</small> stood on the shingle that fringes Millbourne Bay</p>`:

Find: `<p class="nind">(.*?)<small>(.*?)</small>(.*?)</p>`

Replace: `<p>\1\2\3</p>`

This will result in `<p>A GIRL stood on the shingle that fringes Millbourne Bay</p>`. 

You will then have to run another regex to change the all caps to lowercase. You can see if you needed to change the opening paragraphs across one or two chapters it might be easier to do it by hand, but if you had 30 or 40 chapters to fix it is definitely easier to spend a moment building the regex.

#### Basic wildcards/metacharacters
- `\n` — find new line (i.e paragraph break)
- `\t` — find a tab
- `\s` — find white space (including line breaks)
- `^` beginning of a line
- `$` end of line
- `[]` — find set e.g. `[A-Z]` capital letters between A and Z
- `{x,y}` — limit set e.g. `[A-Z]` 

**Note:** if you need to search for characters like a period, dollar sign or question mark etc. you will need to 'escape' it by preceding it with a backslash e.g. `\$` will find any dollar signs and `$` will find the end of a line.

- `|` — Or i.e. `this|that` will find 'this' or 'that'
- `.*?` — is your basic wildcard e.g. \<p>.*?\</p> will find everything between the two tags. See *Advanced Patterns* for a breakdown of this combination.

#### Basic replace functions
- `\L` — set all text to the right as lowercase
- `\l` — first letter to the right as lowercase
- `\U` — set all text to the right as uppercase
- `\u` — first letter to the right as uppercase
- `\E` — end change case i.e. \U or \L 

#### Look ahead or Look behind
- `(?=text)` — finds the position that immediately follows 'text'
- `(?<=text)` — finds the position that immediately precedes 'text'
- `(?!text)` — asserts that what immediately follows the position is not 'text'
- `(?<!text)` — asserts that what immediately precedes the position is not 'text'

In other words if you have two sentences:
> 1. This is a fact about dogs.
>
> 2. This is a fact about bad dogs.

`(?<!bad) dogs` will find the position before dogs in #1 but not in #2 and you could then alter the text.

Find: `(?<!bad) dogs`

Replace: ` stray dogs`

would result in:

> 1. This is a fact about stray dogs.
>
> 2. This is a fact about bad dogs.


#### Some Advanced Patterns
Here is a handy [RegEx Cheat Sheet](https://gist.github.com/ccstone/5385334) to get you started.
 - `.*?` 
	- `.` means any character except returns
	- `\*` means 0 or more of the . (If you use + instead it will only find things if there are 1 or more)
	- `?` makes it non greedy i.e. it will only grab until the first instance.
		- Thus `<.*?>` will find \<h2> but <.+?> will find \<h2>This is a head\</h2>
- `[0-9]{2,}` — find any 2 digit numbers containing 0 to 9
- `([A-Z])([A-Z]{2,})` with `\U\1\L\2`
	- This would replace a word that starts with a capital and is followed by 2 or more capitals (e.g. SOD) with a single capital and the rest lowercase (e.g. Sod), but it would not change AD or BC.


## <a id="css"></a>CSS [↺](#toc)
**Coming soon:**
- targeting 


# <a id="hints_tips"></a>Hints & Tips [↺](#toc)
### First Projects
You will be ***strongly*** encouraged to pick a book off the [First Production list](https://standardebooks.org/contribute/wanted-ebooks) as your first project. Many people come to the list because they have a project in mind and balk at this restriction. After what is often a lot of argument, some reluctantly agree to do it the Standard Ebooks way and some depart unhappily. 

The reason for this restriction is two-fold. As a producer you will discover in some cases it is harder than it looks to balance the editorial and structural demands of a text (even little things like letters or posters pose some semantic and coding problems). And length is a big factor in being able to balance the many dimensions of producing a quality project—many projects are abandoned each year because the producer just couldn’t sustain the effort. The other main reason is it is highly likely you will make errors on your first attempt and the reviewer assigned to you is left having to scrutinize not only the basics, but all that extra length and/or complexities involved in a longer, more complicated book.

So stick to some thing say for the first book—and if you are new to coding, maybe the fist couple of books—before you strike out in an attempt to bring your favourite piece of literature to the world. The good new is that a first production was categorized as 40,000 words when I started and is now, thanks to improvements in the toolset, set at < 100,000 words.

Remember though, even given the restrictions you are free to use the methodology and toolset to produce you own book—it just won’t be eligible for inclusion in the Standard Ebook corpus.

#### Some quick hints
- Make it easy on reviewers: include the links to your repos (repositories), include attachments with images, link to specific pages when providing source material etc.
- You need to use escaped html text for the long description in the content.opf file. But you also need to ensure that each paragraph is indented by 3 tabs. This might be corrected by the latest version of lint.
- finding errors: (coming soon)
- .DS_Store files: managing etc. (coming soon)

### Semantication
**Coming soon:** 
- hints

### Sources
As a Canadian, finding texts (especially for cover searches) can often be problematic. Because of geo-blocking due to territorial rights and differing copyright periods often books that are freely available in the U.S. are not available to Canadian producers—I find Google Books especially frustrating on the score and rarely use it. 

There are often multiple sources for finding original texts and sorting through them to find the best, copyright free version is just another challenge.

- [Internet Archive](https://archive.org/) — The go-to. Start here when looking for page scans of pre-1925 books.
- [HathiTrust](https://www.hathitrust.org/) — Not quite as user-friendly as the Internet Archive, but a good source for scanned books if you strike out there.
- [Google books](https://books.google.com/) — As mentioned above, not as accessible to non-American locations.
- [Distributed Proofreaders](https://www.pgdp.org/ols/index.php) — The online home of the proofreaders who are supplying the main Gutenberg projects. Page scans are available as individual files so it makes it more cumbersome to work with.



## <a id="handy_links"></a>Handy links [↺](#toc)
Start with the Standard Ebook [Get Involved](https://standardebooks.org/contribute) page. It has most of the links you’ll need.
- [Step by step](https://standardebooks.org/contribute/producing-an-ebook-step-by-step) — This is the one to read first to see if you are up to the challenge.
- [One page style guide](https://standardebooks.org/manual/latest/single-page) — There is an extensive style guide but this version displays it all on one huge page making it easer to search.
- [Escaped text page](https://www.freeformatter.com/xml-escape.html) — You will be asked to use escaped text for the long description and this site can help do that automatically.


## <a id="my_notes"></a>Some of My Notes [↺](#toc)
### Forking (copying)
Forking is a way to make a copy of an existing repo, apply some changes and then resubmit it. Its much more than that, but for Standard Ebook purposes it acts as a way to submit changes to a book. Here is a basic guide to forking for further reference: [fork-a-repo](https://help.github.com/articles/fork-a-repo/).

This is my step-by-step to fork a project  so you can work on it.

#### Make a Fork
Go to [Standard Ebook repository](https://github.com/standardebooks) and find the repository you want to edit.
- Click fork (upper right). This make a fork (copy) of the project in your Github account.
- Go to Github Desktop on your computer.
- Click on the arrow that says curent repository and select *Add*.
- Select *Clone Repository* and find the fork you just made. 
  - Ensure you are going to download it to the proper folder for where you store your projects and click *Clone*.

Open the project (in BBEdit) and make changes.

#### Submit Changes
Once you've made all the changes , now you need to submit it to the original "owner" for a approval and integration into the main  project. This is where the usage of  version management schemes like Github are  really useful. The owner of the project can continue to make changes to their files and still be able integrate changes from outside teven though the original project isn't the same.

- Navigate to the original repository you created your fork from.
- Select *Pull requests* from beside *Issues*.
  - Click New pull request.
- Select the link that says *Compare across forks*. Its at the end of the sentence under the heading **Compare changes**.

There are drop-down menus for choosing the head and base repositories.
- The **base repository** is where the main files are (the repository you originally got the files from and where you'd like to merge changes into.
- Use the **head repository** drop-down menu to select the branch you made your changes in.
	
- Edit the Pull request title and description fields
  - Type a title and description for your pull request.

- Create pull request button
  - To create a pull request that is ready for review, click *Create Pull Request*.
  
You will be notified if the/when the changes are accepted.

