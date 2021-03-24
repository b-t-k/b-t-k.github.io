---
layout: page
title: "How to’s for contributing to Standard ebooks"
permalink: how-to/
---

![standard ebooks logo](/images/selogo.png)

### <a id="toc"></a>Table of Contents
#### Part 1
1. [Introduction](/a-guide/#introduction)
2. [Key Concepts](/a-guide/#key_concepts)
3. [Tools](/a-guide/#tools)
4. [Get Started](/a-guide/#get_started)

#### Part 2
5. [How To’s](#methodologies)
	1. [BBEdit](#bbedit)
		2. [Search & Replaces and Regexes](#search_replaces_and_regexes)
	1. [GitHub Desktop](#github_desktop)
	1. [CSS](#css)
6. [Hints & Tips](#hints_tips)
	1. [Handy links](#handy_links)
	2. [My Notes](#my_notes)


# <a id="howto"></a>How To’s [↺](#toc)
This section focuses a bit more on specific methods I use, some hints and tricks I have discovered along the way and some in-depth tips on specific actions.

## The Mac Keyboard and Typography
We all know the difference between straight quotes and curly quotes right? How about a regular dash and an n-dash? These are important distinctions and unlike when using your helpful word processor, you are going to have to learn to enter them properly from the keyboard. 
#### quotes
- left quote (“): opt+[
- right quote (”): opt+shift+[
- left single quote (‘): opt+]
- right single quote (’): opt+shift+]
#### dashes
- n-dash: opt+-
- m-dash: opt+shift+-
#### accents
- grave (á): opt+e followed by the necessary letter.
- acute (à): opt+` followed by letter.
- circumflex (ê): opt+i followed by letter.
- umlaut (ä): opt+u followed by letter.

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
**More soon:** 
- a beginners guide to regexes
- BBEdit and advanced searches

### A Basic Pattern
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

### A bit more advanced
So what else can you do? In reality the options are unlimited but parsing the code can be a bit of a nightmare. There are online regex testers ([regextester.com](https://www.regextester.com/), [freeformatter.com/regex-tester.html](https://www.freeformatter.com/regex-tester.html) etc.) that will allow you to test out patterns before you try them on your project. Testing is often a good idea because while the undo function will often rescue you if you make a typo, every once in a while you will find you’ve made a mistake that is unrecoverable.

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

## <a id="github_desktop"></a>Github Desktop [↺](#toc)
**Coming soon:**
- Step by step 


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

