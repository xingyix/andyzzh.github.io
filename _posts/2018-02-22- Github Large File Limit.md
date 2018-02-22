---
layout: post
title: Github Large File Limit
---

I was trying to push a couple mat file onto my github repo today but I came across with a problem that I am not allowed to upload large files with size more than 100MB.
Since I already had multiple commits with multiple large files on my local and Github would looks at all files in Git history, only unstaging files doesn't work.
After some searching I finally solve this issue as it was suggested <https://stackoverflow.com/questions/19573031/cant-push-to-github-because-of-large-file-which-i-already-deleted>: 
Let's say we have two large files file1 and file2 in commit history
```git filter-branch -f --index-filter 'git rm -r --cached --ignore-unmatch file1 file2' HEAD
```
