---
title: "Let me introduce you to GIT.. err TIG!"
author: Marcin Biegała
type: post
categories:
  - Code
  - Git
date: 2019-01-07T08:40:43+01:00
---
I'm GIT fan for years.  
I was presenting it on a few occasions and even [created a video course](https://videopoint.pl/kurs/git-kurs-video-pracuj-wygodnie-z-najpopularniejszym-systemem-kontroli-wersji-marcin-biegala,vgitv.htm#format/w)
(sorry it's only in Polish for the moment).
But for all that time there was one piece of a puzzle missing in my setup.  
I'm not a command line guru, but I prefer using it over clicking in the GUI.  
GIT fits here perfectly, but I always had a problem with browsing through the logs.
The _git log_ command it pretty flexible and it can show you different kind of information, from just commit message 
up to full-blown diff of changes. But browsing through all that if you're not sure what you're looking for is pretty tedious.

That's when I've found [TIG](https://jonas.github.io/tig/).  
Reiterating from the website:

> Tig is an ncurses-based text-mode interface for git.

In other words, it's a command line tool that lets you communicate with GIT in a slightly different manner.
Ncurses is a popular library for creating text interfaces, with menus, keyboard support, 'dialogs' etc.  
And that's exactly what TIG handles.  

Let's see how it looks for a moment, to get a better understanding of what we're talking about.  
Below is a screenshot from my terminal on some [random repository](https://gobuffalo.io) after calling _tig_ from the 
command line inside the repo folder (more screenshots on [the official flickr account](https://www.flickr.com/photos/jonasfonseca/sets/72157614470764617).

{{< img-post path="/img/" file="tig_main.png" alt="TIG main view" >}}

You can  see here a list of commits with dates, author names, and messages.  
We can scroll through the list with up and down arrows or k and l keys like in vim.  
Pressing _Enter_ on selected lines will open up diff view side by side, like this one:
{{< img-post path="/img/" file="tig_diff.png" alt="TIG diff view" >}}

We can now move focus from 'window to window' with _tab_ key and for example browse through various commits
and investigate code changes.  
If you want to close 'window' use _q_.

That's how I mainly use TIG, but it has far more use cases, it has blame view, tree view, can help you with status, 
staging or stashing. For me it makes some of git related work easier but leaves me still in that keyboard oriented 
command line mode - no reaching for a mouse of switching context.

Just to close the topic I wanted to note that TIG can act as a pager for GIT commands too.  
Try to run commands like:  

> git show | tig  
> diff -u a.txt b.txt | tig  
> git log --author="mark@markbates.com" --since="2018-05-29" | tig  

So you can incorporate TIG into your neatly created fancy aliases 

If you want to learn more about TIG and check how to install it on your OS (for macos just use brew) go to
[the official webpage](https://jonas.github.io/tig/). For more info about how to use it check the [manual online](https://jonas.github.io/tig/doc/manual.html)
or press _h_ key while in TIG.

