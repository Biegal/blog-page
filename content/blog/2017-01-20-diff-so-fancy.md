---
author: "Marcin Biegała"
categories:
  - Code
  - Tools
date: "2017-01-20T03:35:31+02:00"
description: ""
title: "Diff so fancy"
type: "post"
---
I'm a 'console guy'. I usually prefer any type of console/text based interface over sweet and colorful UI.
Same applies to my favorite source control - GIT. But there is nothing that prevents us to get fancy in our terminals. Meet [`diff-so-fancy`](https://github.com/so-fancy/diff-so-fancy).  
GIT is great for handling your code, showing repository log in any way you want, but when it comes to showing a diff, we're basicly stuck with the standard patch format.  
Don't get me wrong, it's very informative, but sometimes dealing with all those +++ and --- makes things more complicated.  
Below you can see a screenshot take from projects website:
![](/img/diffsofancy.png)
We get nice asci art like headers for file names, no more +/- characters to mess our code and even changed part of lines highlighted.  
It's not the best thing since sliced bread for sure, but definetly it's a nice touch to your every day git life :)  
So how do we get this ?  
I will just show you how to get this easiest on mac, but you can find instalation instructions for other OS on the projects [github page](https://github.com/so-fancy/diff-so-fancy).  
We will use `brew` to install the package:  
```
brew install diff-so-fancy
```
Now we can use it inside our repositories  
```
git diff --color | diff-so-fancy
```
You can of course plug it into GIT configuration, again examples are on projects [github page](https://github.com/so-fancy/diff-so-fancy)