---
templateKey: blog-post
title: How to add tracked files to .gitignore
date: 2020-07-20T20:11:24.568Z
tags: git,react,deployment
thumbnail: /image/github-mark.png
slug: how-to-add-tracked-files-to-gitignore
description: In this article, we talk about how to add tracked files to your .gitignore.
---

At one point or the other you might have committed some files or folders to your remote repo and after several commits you decide that you no longer want to track those files and you try to edit directly the .gitignore file but it doesn't work or sometimes I go as far as cutting the folder push a commit and paste the folder and add the folder to .gitignore then push as though it were a new one.

The reason for this issue is that the rules in your .gitignore only applies to untracked files therefore subsequent edits would apply to the following files and not the old ones.

Run this 
```
git rm -r --cached directory-to-remove
git commit -m 'feat: remove "directory-to-remove" from remote repo'
git push origin master
```

```
git rm -r --cached directory-to-remove
```
This command provides you with a preview of what is going to be deleted from your git cache.


However you need to note that this doesn't remove the history of the file or folder from your git history and make it appear as though it never existed. To do that you can check out [BFG Repo Cleaner](!https://rtyley.github.io/bfg-repo-cleaner/) or you use `git filter-branch`. [Check out this guide](!https://docs.github.com/en/github/authenticating-to-github/removing-sensitive-data-from-a-repository#using-filter-branchs) on how to use it.

Have fun!