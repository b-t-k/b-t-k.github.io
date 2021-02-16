---
layout: page
title: "A non-programmers guide"
permalink: /test
---

# A non-programmers guide to contributing to Standard Ebooks
## Introduction
### Why this guide
[Standard Ebooks](https://standardebooks.org/) is a project started by Alex Cabal 
> … takes ebooks from sources like Project Gutenberg, formats and typesets them using a carefully designed and professional-grade style manual, fully proofreads and corrects them, and then builds them to create a new edition that takes advantage of state-of-the-art ereader and browser technology.
It is  a volunteer driven project. If you are interested in   adding to the availability of public domain literature or just want to learn about how ebooks are made, this is a great project to take part in.

The downside is that it is very programmer-centric. A lot of what you need to know/do for complicated projects is beyond the ken of your basic computer user. But thankfully, with SE’s [detailed instructions](https://standardebooks.org/contribute/producing-an-ebook-step-by-step) and the provided [SE toolset](https://github.com/standardebooks/tools), getting started on basic projects is well within the means of the average user. You just have to have a grasp of some basics first.

And that’s what this tutorial is all about. I think it would be great if more of the right-brained set became a part of the project and I thought I would  see if I could lay out the basics. 

Be sure to visit the [Contributors page](https://standardebooks.org/contribute) if you want see the various ways you can help out even if this guide still leaves you too nervous to give it a try. 

#### Disclaimer
A lot of my terms and concepts are not going to be strictly accurate. For one, I don’t actually understand some of them myself, and for two, the analogies I offer are just that: analogies. You can do more research yourself if you really want to know more about what’s going on. My aim is just to demystify some of the more intimidating steps. Feel free to correct me if I am egregiously misleading anyone.

### OS X-centric
I am a Mac user. Most of what I write here will be focussed on working with a Mac. There won’t be much difference if you are using Linux (but there I assume by dint of being a linux user this guide won’t be as applicable to you) and if you are a Windows user the basics still apply but you will have to adjust your tools to suit the platform.

## Key concepts
To make an ebook you are, at root, making something very similar to a website that is packaged according to some very specific rules. This means that a working knowledge of html and css is helpful. You also will need to get over any nervousness you have regarding the *command line prompt*. That’s that thing that looks like an old-tymie computer interface with a blinking prompt where you have to enter arcane and often incompressible commands. But don’t worry—most times its simply a matter of cut and paste.

### Accessibility
One of the keys to understanding how and why a Standard ebook is formatted the way it is is realizing it is designed to be as *accessible* as possible — that means it can be used on multiple readers including screen readers for the visually impaired. As an example, it’s important that the  computerized reader can distinguish between the article ”I” and the Roman numeral I —something our brains do automatically. So if in the course of working on a project you are confused about whether to mark something up or not, a good touchstone is to ask yourself if a computer would be able to  distinguish what it was without further context.

Meta-data is also very important to the overall accessibility of the ebook. But more on that later.
 
### html & css
Html is a programming language used to make web pages. It has a few conventions you need to know.
#### tags
Html is formed by surrounding text with tags. Each tag has an opening and a closing tag. P, the tag that marks paragraphs is used like this: 

> `<p>This is a paragraph. It may have all sorts of text in it.</p>`

Some common html tags you will need to know: 
- **emphasis**: `<em>…</em>` — This is used in place of italics in most cases.
- **italics**: `<i>…</i>` — generally only used where italics are grammatically correct e.g. foreign languages, names of books etc.
- **strong**: `<strong>…</strong>` — This is used instead of bold in almost all cases.
- **bold**: `<b>…</b>` — very rarely used.
- **span**: `<span>…</span>` — generally used mid-sentence to surround something you might want to add information to when it isn’t appropriate to use any of the above tags.
- **br**: `<br/>` — an exception to the opening/closing tag rule, a br (break) is a line break that goes at the end of a line you want to break. The forward slash at the end indicates it is acting as both an opening and closing tag.
- **hr**: `<hr/>` — another exception. The hr (horizontal rule) tag is used to indicate section breaks that are usually shown by  white space or  glyphs in a printed book.
- **blockquote**: Essentially a ‘quote’ that is generally  formatted to stand out from the rest of the text e.g. a letter or a sign

  `<blockquote>`  
    &nbsp;&nbsp;&nbsp;`May contain multiple paragraphs`  
    &nbsp;&nbsp;&nbsp;`Or other parts.`  
  `</blockquote>`  
- **abbr**: `<abbr>Mr.</abbr>` — Indicates abbreviations, all of which should be marked appropriate in Standard Ebooks.

##### CSS & Classes
Many tags will also accept additional parameters which are part of the CSS (Custom Style Sheet) file. A Standard ebook usually has 3 style sheets (core.css, se.css, and local.css) found in the css folder. The only one  you as a producer will ever touch is **local.css** — at the beginning of the project it will be empty.

Briefly, the purpose of css is to add “custom” styles to blocks of text. For example if you want the signature line of a letter to be right justified you could enclose that line in a *p* tag and add a class: `<p class=“signature”>Bob Smith</p>`. You would then also add the appropriate css to the local.css stylesheet:

`.signature{`  
&nbsp;&nbsp;&nbsp;`text-align:right`  
`}`

But don’t worry. Almost all of the appropriate css is detailed in [The Standard Ebooks Manual of Style](https://standardebooks.org/manual/latest) and is simply a matter of cutting and pasting.

This is a huge part of a standard ebook referred to as semanticating. Adding semantics is very important to the well-formed nature of the final product and takes a lot of time and close reading to get correct, especially in more complex productions like plays or epistalory texts. More about that later.

### Ebook Structure
We’ve talked a bit about what an ebook is: essentially a self-contained website. When you start a new Standard ebook project a basic template will be created for you. But here is a brief description of the parts you will need to understand:
- **content.opf** This is the file that houses most of the metadata about the book and contains the “manifest” which details all the constituent parts of the ebook.
- **css folder** Contains all the css files to control how the book looks.
- **images folder** Contains the cover image (which is generated as one of the production steps).
- **onix.xml** Ignore it. Essentially a metadata file for book distributors. 
- **toc.xhtml** The Table of Contents. Automatically generated but  *very* occasionally will need to be tweaked.
- **text folder** Contains the  text files for your project including several standard files common to all Standard ebook projects.

### xhtml
Html stands for *hypertext markup language* and is the basic format that web browsers read. XML stands for *extensible markup language* and can be thought of as a “programable” version of html. The ebook is based on xhtml files which are, in a way, just a mashup of the two.

If you open an xhtml file in your web browser it will appear just like a web page — handy for proofing and checking if and where any errors might be lurking.


### Python, Brew and the Command line
#### Python
Standard Ebooks has a toolset that is based on the Python programming language. If you have a Mac it will come with python already installed but to date it is still Python 2 which is due to be deprecated. But when you install the Standard Ebooks [tools](https://github.com/standardebooks/tools) it will install the latest version of Python 3 for you.

#### Brew 
To install and maintain the tools on a Mac you use the Brew package manager. This is similar to an “app store” that leaves the heavy lifting to someone else. There are instruction on the Tools Github (More on Github in the next section) to get up and running. It will take some time all the while you terminal will be spitting out lines and line of gibberish. Just ignore and have a nice cup of tea or coffee.

#### Terminal
Most of the Standard ebook tools are not housed in a GUI (Graphical User Interface) — the thing you point and click with your mouse. You will need to be fairly comfortable with the Terminal interface to work on a project. But again it’s mostly cut and paste from the Manual.

### regex
Regular Expressions, generally known as regexes,  are, roughly speaking, a way to search and manipulate text through a series of wildcards. I will freely admit that, while I am pretty bad at constructing proper regexes, I am a huge fanboy. Imagine being able to replace every instance of a particular word in the first paragraph of a chapter across multiple files with Title Case. It saves a whole lot of legwork. Standard Ebooks step by step includes a bunch of regexes to replace a lot of manual labor and you can quickly learn to build some yourself.

More on this later.

### Github
[Github](https://github.com/) is what Standard Ebooks uses to manage and control the various projects. I am a real noob at using Github and frequently have to resort to using google-foo to figure out how to fix what I did wrong.

In a nutshell, Github is a website that allows you to exercise version control over your project. You create an initial repository and as you move through the steps you sync your local version to eh GitHub website. This allows you to  keep track of the steps you have taken and, more importantly, revert any changes you made that weren’t appropriate or were outright mistakes.

You will have to create a GitHub account for you to store your work in progress and when it is finalized and approved then Standard Ebooks will clone it to their [own GitHub repository](https://github.com/standardebooks/) in preparation to publishing. Incidentally this gives you access to all the repository for the couple of hundred ebooks that were already  published, providing a plethoras of examples on how to solve various issues.

## Tools
Ok. Now we are into the meat of it. This is my setup. There are many ways to skin this particular furry mammal but this is what I use.

### BBEdit & Text Editors
[BBEdit](https://www.barebones.com/products/bbedit/index.html) is basically a text editor — but it is one especially designed for coding. There are a lot of other options ([Visual Studio Code](https://code.visualstudio.com/), [Brackets](http://brackets.io/) etc.) all of which are more or less free.

And, in case you haven’t figured it out, editing text is a large part of what making an ebook is about. And editing text means exactly that: you will be editing raw text. Not rich text with bolds and italics and definitely not word processor text with all sorts of hidden code. Raw [ASCII](https://en.wikipedia.org/wiki/ASCII) text. 

The advantage of BBEdit (or other code editors) is that it allows you to do things like open entire folders in one window and more importantly do regex-based search and replaces to multiple files. I also am able to write external scripts to do things like rename files or convert bits of text to an url-friendly format (i.e. remove spaces and make lowercase) and then run them from within BBEdit.

### Github Desktop
As I mentioned above, you will have to use Github. And this is generally managed using the command line. There are a whole bunch of commands involved and frankly it almost made me give up when I first started. Then I realized that pretty much everything is available if you look for it and I downloaded [Github Desktop](https://desktop.github.com/) which is a GUI interface and that made my life a lot easier.

Github Desktop provides a visual/graphical tool to manage your repository. I pretty much ignore the command line for git purposes these days. The general sequence is that any changes you make in a file will be represented in the Github Desktop GUI. You elect which files you wan to sync; give that selection a name (e.g. initial commit or fixed typo) and then “commit” it. Then you can “push” the various commits up to the website or undo them.

### Terminal
On a Mac the command line interface is accessed through a program called *Terminal*. Simply hit cmd-spacebar and type terminal or go to Applications: Utilities and double click on the Terminal icon.

Terminal is an app like any other, but it opens a window into the functions that underpin how your computer works. Anyone who remember the DOS days will already be familiar with the concept.

Its helpful to know a bare minimum of Terminal commands. Depending on how old your OS is you will likely be using *bash* or *zsh* as your shell (this is inherited from the unix underpinnings of OSX) but you don’t really need to know that beyond perhaps wanting to google “bash how to change directory” or something similar.

When you open Terminal it will give you a prompt similar to `bob@my-mac ~ %`. As I said it will vary from shell to shell. You will general start in your user folder. If your user name is Bob then it will be in the Bob ‘home’ folder. Typing ‘ls’ and hitting enter will list the folders and files so you can check if that’s where you are.

#### Basic terminal commands
- **`ls`** list — lists files and folders
- **`cd`** change directory — allows you to change your directory. For example `cd /bob/Documents/Projects` would switch you to the Projects folder found in your Documents folder. Just like if you had double-clicked on the Document folder and then double-clicked on the Project folder.
  - Don’t panic! You can — and I always do — simply type `cd` followed by a space and then drag the folder you want to be in  from the GUI/Finder onto Terminal and, voila, you have the correct path name automatically ready for you to hit `enter`. Saves on the frustration.
- **`cd ..`** Change directory up one level. If yo are in /Projects/Bob’s book and you want to be in /Projects/ the will do the trick.

And finally there is a whole raft of Standard ebook commands that are again cut and paste from the guide. Here’s a common one: 
 - **`se clean .`** This tells terminal to use the `se` toolset, find the command `clean` and apply it to all the files and folders in the current directory `.` 
You will primarily be using Terminal to invoke these sorts of SE toolset commands.

### Photoshop/GIMP
The last tool you will have to use is an image editor. All you really need to use it for will be to crop the final cover image to  exactly 2100 pixels by 1400 pixels, but occasionally you might want to colour correct the image a bit or edit out a bad scratch.

I have Photoshop as apart of woking suite but GIMP is a totally free image editor that is pretty highly regarded.

## Get Started
So. Time to start. First off you need to subscribe to the [Standard Ebooks Google Group](https://groups.google.com/g/standardebooks) which where 99% of the communication back and forth happens.

Then you need to visit [Wanted Books](https://standardebooks.org/contribute/wanted-ebooks) page and find a book that appeals to you from the **First Production** section. Alex (and everyone else who has reviewed a book project) will strongly discourage you from choosing a book that isn’t on the list for a first project. Not only do you have to learn all the ins and outs but then. Review has to go through it closely to ensure you’ve done everything correctly. The longer and more complex the book, the harder it is for both parties.

Star a new thread in the Google Group and send off a note with your chose book and wait (patiently) to see if its approved. Then you are on your way and can follow the [Step by Step](https://standardebooks.org/contribute/producing-an-ebook-step-by-step).

***
## Methodologies
This section focuses a bit more on  specific methods I use and some hints and tricks I have discovered along the way.

### Search and Replaces

## Hints & Tips
- first projects
- escaped text
- Make it easy on reviewers: links to repos, attachments with images etc.

## Important links
Step by step
One page style guide
Escape text page

## My notes
Forking

