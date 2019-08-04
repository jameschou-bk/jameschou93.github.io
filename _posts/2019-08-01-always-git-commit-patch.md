---
layout: page
title: "Git Commit Patch"
description: >
  Stop adding useless lines
tag: [blog]
---

I've had many git commits where I inadvertently add a line of code that I forgot to remove when debugging. Luckily git has a nifty patch function that allows you to view each "hunk" of code that has been added or changed and selectively choose what is staged for your next commit. Here's how you can do this:

In your terminal, enter

~~~~
git commit -p
~~~~

A prompt should appear with your first hunk. For example:

![git patch]({{ site.baseurl}}/assets/img/git-patch.png)

from here, you have a few options:

- y: yes, add this hunk
- n: no, don't add this hunk
- d: don't add this hunk or any hunks after this one
- q: quit, nevermind adding anything
- s: split this hunk into smaller hunks
- e: edit this hunk (opens your text editor)

Once you're done deciding what to do with all your hunks, your text editor will open allowing you to write your commit message. You can edit/comment out any files you don't want to commit here.

Once you save and close this commit file, you're all set!
