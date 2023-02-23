---
title: "CS50x Week 2"
date: 2023-3-22T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: [CS50x, Arrays, C, Python]
author: "Chris"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Some fun with C and Python."
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
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page

---
I just finished week 3 of the Harvard CS50x course and it’s getting interesting.
Last week they introduced arrays. I finished the assignment to create a program in C that prompts the user for a message and then outputs the text in binary with dark and light emojis representing 0 and 1, respectively. It was fun to play around with and I wanted to translate my solution from C to python. 

The CS50 course provides a C library, CS50, which includes some types that aren’t native to C, like `string` and `get_string()`. In my C code example below, I will omit the CS50 library so that it’s easier to compile and run without having to link the library's binary file. 

the output will look something like this:
```
⚫🟡⚫⚫🟡⚫⚫⚫
⚫🟡🟡⚫⚫🟡⚫🟡
⚫🟡🟡🟡🟡⚫⚫🟡
```

Can you guess what it says?

```C
#include <ctype.h>
#include <stdio.h>
#include <string.h>

const int BITS_IN_BYTE = 8;
int arr[8];

void print_bulb(int bit);

int main(void)
{
    printf("Message: ");
    char message [400]; // get string of at max 400 characters
    scanf("%s", message);

    //loop through each word
    int n = strlen(message);
    for (int i = 0; i < n; i++)
    {
        int bits = 8;
        //loop through the ASCII number to convert to binary
        for (int j = 1; j <= BITS_IN_BYTE; j ++)
        {
            int bit = message[i];
            message[i] = bit % 2;
            arr[j] = message[i];
            bit = bit / 2;
            message[i] = bit;
            bits = bits - 1;

        }
        //reverse loop through array for each binary
        for (int x = 8; x > 0; x --)
        {
            print_bulb(arr[x]);
        }
        printf("\n");
    }
}

void print_bulb(int bit)
{
    if (bit == 0)
    {
        // Dark emoji
        printf("\U000026AB");
    }
    else if (bit == 1)
    {
        // Light emoji
        printf("\U0001F7E1");
    }
}
```

And now for my python example:

```python
"""
Bulbs from cs50 adapted for python
"""
import math as m

BITS_IN_BYTE = 8

message = input("Message:")
# loop through each character
for i in message:
    char = ord(i)
    arr = []  # put each characters 8 bit conversion in list

    j = 1
    while j <= BITS_IN_BYTE:
        # calculate the 8 bits of a char
        bit = char
        char = bit % 2
        bulb = m.trunc(char)
        # append emoji light if 1 or dark if 0 to arr
        if bulb == 0:
            arr.append("\U000026AB")

        elif bulb == 1:
            arr.append("\U0001F7E1")
        bit = bit / 2
        char = bit
        j += 1

    # print output of arr in reverse on single line
    # use reverese print because thats how the bits would be represented.
    print(*arr[::-1], sep="")
```

*the message says 'hey'*