---
layout: post
title: About Github Large File Limit
---

I was trying to push a couple mat file onto my github repo today but I came across with a problem that I am not allowed to upload large files with size more than 100MB.
<br/>Since I already had multiple commits with multiple large files on my local and Github would looks at all files in Git history, only unstaging files doesn't work.<br/><br/>
After some searching I finally solve this issue as it was suggested
[Here](https://stackoverflow.com/questions/19573031/cant-push-to-github-because-of-large-file-which-i-already-deleted)<br/><br/>
Let's say we have two large files file1 and file2 in commit history<br/>, we can solve this by command: <br/><br/>
```git filter-branch -f --index-filter 'git rm -r --cached --ignore-unmatch file1 file2' HEAD
```, which looks at all your commit history and remove the large files.
