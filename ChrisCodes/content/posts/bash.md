---
title: "Not to bash on Bash."
date: 2023-3-09T11:30:03+00:00
weight: 5
# aliases: ["/first"]
tags: [bash, terminal]
author: "Chris"
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Just because you can doesn't mean you should."
canonicalURL: "https://canonical.url/to/page"
disableShare: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "images/bash_post.jpg" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page

---
My job out of college was working on the UCSC Genome Browser QA team. One of the first things I had to do was get comfortable with the Born again shell (bash). I found it really helpful to have a quiver of one-liners for repetitive tasks.


 For example, I can create a dummy data file with 1000 lines:

```bash
for((i=1;i<=1000; i++)); do echo "data_point_$i" >> data_munging.txt; done
```

Let’s say I needed to add each entry in an SQL query (for some reason)
I’d need to remove the new lines and add a comma as a separator with each data_point in single quotes. I wouldn’t want to do that manually! 

```bash
echo $(sed "$ ! s/.*/'&',/; $ s/.*/'&'/" data_munging.txt)
```
Aaaand we’re done. So fast. 

Recently, I had the idea to try a Leet Code problem with a bash script. There is really no reason to do this other than curiosity.  

Let’s try Two Sum. The problem is as follows: Given an array of integers (nums) and an integer target, return the indices of the two numbers such that they add up to the target. Assume each input has exactly one solution and you may not use the same 
element twice. 

```bash 
#!/bin/bash

nums=(1 22 4 8 10 32 40 3 100 1 89 3 9 0)
target=6

for i in ${!nums[@]} 
    do  
    diff=$(($target - ${nums[$i]})) 
    for j in ${!nums[@]} 
    do    
        if [[ "${nums[j]}" = "$diff" && $i != $j ]] 
        then 
            echo "[$i,$j]"                    
            break 2 
        fi
    done       
done 

```


I’ll break down the code below:

```bash
nums=(1 22 4 8 10 32 40 3 100 1 89 3 9 0)
target=6
```
Initialize an array, nums, and a variable, target. 

```bash
for i in ${!nums[@]}
```
This line begins a for loop that loops through the nums array’s indices. 

```bash
diff=$(($target - ${nums[$i]}))
```
Then we calculate the difference between the target and each element in the nums array.

```bash
for j in ${!nums[@]}
```
Nested loop to go through the elements in nums.

```
if [[ "${nums[j]}" = "$diff" && $i != $j ]]
```
If the difference of target and index "i" is found in the array and the index that it’s found at is not the same as "i", proceed.

```bash
echo "[$i,$j]" 
break 2
```
Output the indices found and break out of the nested loop.

```
[7,11]
```

It works! However, not to bash on Bash, that doesn't mean you should do it. 

