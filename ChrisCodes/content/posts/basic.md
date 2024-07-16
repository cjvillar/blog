---
title: "Let’s try something BASIC."
date: 2023-3-06T11:30:03+00:00
weight: 2
# aliases: ["/first"]
tags: [BASIC, APPLE]
author: "Chris"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Coding with Javascript-emulated Applesoft BASIC."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "images/basic_book.jpg" # image path/url
    imageWidth: 100
    imageHeight: 100
    alt: "what AI thinks the 80s was like" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page

---

A few years ago I had the pleasure of going to Cambridge, England for work. While enjoying some free time,  a bunch of colleagues and I went to the [The Centre for Computing History](http://www.computinghistory.org.uk/). Aside from learning about the history of tech from knowledgeable staff, I really enjoyed playing with the old computers.
Below is an Apple II. I think it's clear I had no idea what I was doing.  


![Apple II](../../images/appleii.jpg)

Recently, I decided to search for some emulators of older systems to try older computer languages such as BASIC (Beginners' All-purpose Symbolic Instruction Code). That’s when I found: [jsbasic](https://www.calormen.com/jsbasic/),   a javascript BASIC emulator. 

![BASIC programing book](../../images/basic_book.jpg)

Above is a book on the BASIC programming language that was available to use with open computers at the museum. Using the jsbasic emulator let’s see what the code on the cover does!




```
10 FOR I=1 TO 10
20 PRINT TAB (30);
30 FOR J=1 TO I
40 PRINT "*";
50 NEXT J
60 PRINT
70 NEXT I
80 END
```

![OUTPUT](../../images/basic_output.png)

I think that's pretty rad! 
