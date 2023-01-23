---
type: blog-post
layout: post
title: "How to connect Zotero with Obsidian"
category: notes
tags: Zotero Obsidian Guide 
---

I use [Zotero](https://www.zotero.org) for reference management and [Obsidian](https://obsidian.md) for note taking. There is a whole religion around note taking with concepts such as "second brain," "Personal Knowledge Management (PKM)" and "Zettelkasten." I find that a bit too much but enjoy the software, it saves everything in clean .md files in your file system (makes it future proof, you can change software later on and still have all your notes) and supports wiki style linking between notes. I use Zotero simply because it is the best reference manager I have found, it is also free and open source if you are in to that. 

My workflow is such that I start by reading an article in my Zotero library, and make highlights and notes directly on the PDF in the app. I do this in the official app, either on my iPad, phone or computer. I then import these highlights and notes into obsidian for storage and further processing.

Here is how it looks in Zotero:

![Screenshot](/assets/img/ZO1.png)

And here is how it looks in Obsidian:

![Screenshot](/assets/img/ZO2.png)
![Screenshot](/assets/img/ZO3.png)
![Screenshot](/assets/img/ZO4.png)

As you can see, the colors of the highlights (and notes) are preserved. 

The process is pretty straightforward, but when setting this up I found confusing and outdated information (even the used plugin's own documentation is dated) which is why I provide this guide for anyone looking to do the same. To be clear: This works in jan 2023, with Obsidian 1.1.9 and Zotero 6, I will try to update this guide if anything changes.

## Set up Zotero

- Install the [Better BibTeX for Zotero](https://retorque.re/zotero-better-bibtex/installation/) plugin.
- Make sure you have selected a quick copy style. In Zotero open preferences -> export and under "quick copy," select a suitable citation style
![Screenshot](/assets/img/ZO5.png)
- Test quick copy style by opening an article in zotero, choose edit -> Copy Bibliography, and try to paste it somewhere. 

## Set up Obsidian

- Install the community plugin "Zotero Integration." 
	- Open preferences (bottom left in the main Obsidian window), under Options select Community plugins and click browse (if this is the first community plug in you install, you will have to turn off "restricted mode.").
	- Search for "Zotero Integration," click install and enable.
	
![Screenshot](/assets/img/ZO6.png)
![Screenshot](/assets/img/ZO7.png)

- In preferences, under Community plugins, select Zotero Integration.
	- Install PDF Utility if prompted
	- Under Database, choose Zotero
	- Under Import formats, choose add import format

![Screenshot](/assets/img/ZO8.png)
![Screenshot](/assets/img/ZO9.png)

I want to stop here briefly, because this is where it gets a little bit complicated. You have to tell Obsidian what to import from Zotero and how to structure the new note that it will create, by default obsidian will import nothing. To do this, you provide Obsidian with a template. You also have to provide where in your Obsidian vault files will be located. 
 
The template file has to be written in Nunjucks templating language. If you are familiar with this you can write your own template file. Otherwise you can search the web for other users templates, but please be aware that the Zotero Integration plugin was previously named something else and used a different template system. 
 
You can also download my [template from my github](https://github.com/georgnaver/Templates/blob/main/ZoteroNote.md) and use that. It is pretty basic, but I am sure if you give it some thought, you can adapt it to your liking. I personally find it cumbersome to edit templates in Obsidian and use another text editor (BBEdit) for this purpose, but that is up to you. Save the template file as a .md file somewhere in your vault.
 
OK, back to adding a import format.

![Screenshot](/assets/img/ZO10.png)

- Choose a name you can remember
- Choose an output path for your future notes. This is how your new notes will be named and where in your vault they will be saved. The citekey variable i suitable since it will create an unique and readable name for each article/note. I have chosen to put my new notes in a folder named Zotero but if you prefer them at top level, just write {{citekey}}.md
- Choose where to save imported images and how to name them.
- Add the path to your template file, mine is called ZoteroNote.md and is located in folder called Templates which is located in a folder called Misc
- Choose a bibliography style.

## Importing a note

- Make sure Zotero is open and that you have an annotated article in your library.
- In Obsidian use the keyboard shortcut cmd+p (ctrl+p on windows) to open the command palette. Search for the name of your import format ("Zotero note" in my case). Press enter.

![Screenshot](/assets/img/ZO11.png)

- This will open a search bar in Zotero. Search for your article in your library and press enter.

![Screenshot](/assets/img/ZO12.png)

- Your first note with highlights from an article in your Zotero library should now be imported.

### Comment

Disagree with something? Anything you want to discuss? Please [email me](mailto:gizn@georgnaver.se) or comment on [twitter](TWITTERLÄNK) or [mastodon.](MASTODONLÄNK)
