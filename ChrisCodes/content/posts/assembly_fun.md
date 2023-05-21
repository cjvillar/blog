---
title: "ASSEMBLY FUN 💾"
date: 2023-3-2T11:30:03+00:00
weight: 4
# aliases: ["/first"]
tags: [assembly]
author: "Chris"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Assembly is fun and cool."
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
    image: "images/assembler_post.jpg" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page

---

After spending some time programming in C I wanted to explore the world of assembly. Naturally, I went to YouTube and searched for assembly code. I found some excellent resources like, 
[Fireship](https://youtu.be/4gwYkEK0gOk)’s Assembly Language in 100 Seconds.

I decided to install Netwide Assembler (NASM), an assembler for the x86 CPU architecture. I'm on a mac with an intel chip. To install the assembler I used HomeBrew:

 `brew install nasm`


Below is the code for hello world. If interested check out my GitHub repo: [assembly_fun](https://github.com/cjvillar/assembly_fun/blob/main/README.md) with more details on how to get it run.  


```
global    _main               ;entry point for linker
    section   .text           ;text contains logic for program
_main:                          
    mov       rax, 0x02000004 ;system call for write
    mov       rdi, 1          ;file handle 1 is stdout
    mov       rsi, message    ;address of string to output
    mov       rdx, 13         ;length or number of bytes
    syscall                   ;call kernel to do the write
    mov       rax, 0x02000001 ;system call for exit
    xor       rdi, rdi        ;exit code 0
    syscall                   ;call kernel to exit
    section   .data           ;constants
message:  
    db        "Hello, World", 10 
```




More resources:
[NSM Tutorial](https://cs.lmu.edu/~ray/notes/nasmtutorial/)