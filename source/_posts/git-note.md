---
title: git_note
date: 2025-04-12 14:14:31
tags:
---

# Git 筆記
## clone
```
git clone [url]

## SSH (Recommand)
# git clone git@github.com:yuxzs/blog.git

## HTTPS
# git clone https://github.com/yuxzs/blog.git
```

## pull
```
git pull
```

## add
```
git add [file_path]

## all file
git add .
```
## commit
```
git commit -m "[commit text]"

## example
git commit -m "Hello World"

## commit and add all_file (有時候不會生效)
git commit -a -m "Hello Wolrd"
```

## push
```
git push
```

## branch
```
git branch
```

## checkout
```
git checkout [branch_name]

## change branch
# git checkout main

## create and change branch
# git checkout -b [branch_namee]
```

## marge
```
git fetch
git merge [branch_name]
```