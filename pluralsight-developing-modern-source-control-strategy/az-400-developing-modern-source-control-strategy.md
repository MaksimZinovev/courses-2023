---
tags: [course, azure]
aliases: []
description: "My notes for AZ-400 exam preparation. Course: Microsoft DevOps Solutions: Developing a Modern Source Control Strategy "
public: true
dg-publish: true
created: 2023-04-18
---

# AZ-400 Microsoft DevOps Solutions: Developing a Modern Source Control Strategy

## Links

- [Microsoft DevOps Solutions: Developing a Modern Source Control Strategy | Pluralsight](https://app.pluralsight.com/library/courses/microsoft-devops-solutions-developing-modern-source-control-strategy/table-of-contents)

## Developing a modern source control strategy

### What is considered modern?

- centralized
- distributed (Git)

Azure Devops supports both.

Git - commits applied to local repo. Pushing to central repo makes changes available for other team members.

## Differences

Centralized (SVN, Source Safe, TFS)

- scales to very large code bases
- fine level permission control
- allow usage monitoring
- lock files exclusively

Distributed (Git, Mercurial) - considered a modern SC strategy

- full offline experience and speed
- complete repository with portable history
- cross-platform
- growing usage in the market
- pull requests for code review

## Migrating to GitHub or Azure Devops

- tip migration often enough (no full history)
- enable git credential manager
- remove old files linked to old version control system
- create/update .gitignore, .gitattributes
- use suggested .gitignore files

## Setting new github repository and gitignore file

1. Create git repo and gitignore file

```
git init project 
git add *
# remove all added files
git rm --cache *
git status 
# clean, nothing staged
# go to github/gitignore > select your gitignore file, copy as raw 
notepad .gitignore 
# paste gitignore content
git add *
git commit -m "Initial"
```

2. Create GitHub repo
3. Add remote

```bash  

git remote add origin http://github...

```

4. Rename branch

```bash
git branch -M main

```

5. Push to remote

```git push -u origin main

```

## Supported migrations and Git Sub Modules

GitHub:

- Git
- Subversion
- Mercurial
- TFS

Azure DevOps

- TFS server
- Azure DevOps server

Subtree
Is a copy of repository pulled into parent repo. Easier to pull and harder to push.

Submodule
A pointer to a specific commit in anther repository. Easer to push but harder to pull.

## Manage and store large files in git repo

Do not commit

- outputs produced by build
- large and frequently changed binary files (images, videos)
- compressed archives (use individual files instead)

Git LFS

- LFS is extension to git
- Stores binary files in separate remote storage
- keeps standard Git workflow
- no limitations in size

Limitations

- every client used by team must install Git LFS client and configure correctly
- no  merge possible for binary files

eExample

```bash

git clone 

# add large video file  

git status 

git add * 

git status 

git commit -m "Add large "

git push 

# will give error due to large file and provide git LFS url 

# remote is not updated
# install git-lfs.github.com

git reset --soft HEAD~1

# video file is not staged

git lfs install 
git lfs track *.mp4

# gitattributes file gets updated

git add *
git commit -m "Add large LFS"
git push
```

## Cross repository sharing

Package management solutions

- NPM (Nodejs)
- Maven (Java)
- NuGet (.NET)
- Ruby Gems (Ruby)
