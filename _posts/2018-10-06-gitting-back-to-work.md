---
layout: page
title: "Gitting Back to Work"
description: >
How to undo a git commit
tags: [blog]
---
I just had my first official day as a paid dev!

![Confetti](/assets/img/confetti-kid.gif)

Excited to dive into an established code base and break all the things. But today's highlight was my realization that my knowledge of git is a fuzzy memory.

A mistake a have made every time I start a new project is **forgetting to create a new branch** before writing code to be merged!

## **Question:**
What do I do if I made a commit in the wrong branch?!

## **Answer:**
Good ol'

~~~
git reset --soft HEAD~1
~~~

This command will remove your new code from staging without deleting the files.

The **--soft** tag isn't really needed since the git reset command default to soft but I just wanted to emphasize that **--hard** would delete any changes you made locally. Use with caution!

**HEAD~1** specifies that I would like to revert back to one commit before the commit I mistakenly made. If I wanted to revert back to two commits ago I would change the tag to **HEAD~2**

Hope this helps someone! Hopefully more mistakes to come.
