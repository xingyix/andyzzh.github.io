# Welcome to my website:
<https://andyzzh.github.io>

Introduction:

  People cannot upload large files which is more than 100MB sometimes, the author provide his solution here.
  
  If there are two larger files like file1 and file 2 in commit history, then the solution command is:
  
  git filter-branch -f --index-filter 'git rm -r --cached --ignore-unmatch file1 file2' HEAD , which looks at all your commit history and remove the large files.


