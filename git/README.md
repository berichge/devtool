# Git

Git is a popular version control system.

## Setup

After downloading git, you can use follow command to setup local git env variables.

    git config --global user.name "my name"
    git config --global user.email "my@gamil.com"
    // to verify
    git config --global list

## Basic comments

- git clone
 clone a repo from remote to local.

    `https://github.com/berichge/devtool`

- git status

- git add
    this command will move file changes from ***work directory*** to git ***staging area***.
  - -A add all changes

- git commit -m "msg"
    move changes from staging area to local git repo. Your local branch will ahead of origin/master by commits.
- git push origin master
    ***origin*** is the name of ***remote*** by default. ***Master*** refers to our default and only local branch, that will can use to exchange file changes to and from. ***origin/master*** is the copy of master branch in remote.
- git init [repo name]
- git reset HEAD [name of file]. unstage changes on file.->move file back to unstage work directory.
- git checkout [name of file], discard changes in local work directory.
  - -- [filename]: git checkout -- [filename]
- git mv [current file name] [new file name]
- git rm [file to be deleted]
- git log: check all commits
  - git log --oneline --graph --decorate
  - git log [from commit] [to commit]
  - git log --since="3 days ago"
  - git log --follow -- [file]
  - git show [commit id]

## Basic Operations

### git fork(from UI)

fork a repo to a new remote branch.

### ignore files

by .gitignore. This file need to be added for version control

    .DS_Store
    *.log
    log -- folder from same path

### init a remote branch

Steps
1. Create a repo branch from git web page
2. In local branch, run `git init`
3. run command `git remote add origin {your remote git url}
4. confirm remote branch is added by `git remote -v`, you should see git remote url aliased as the origin remote
5. create a master branch by `git checkout -b master`
6. commit change to local git staging repo, `git commit -m "create a master branch" --allow-empty`
7. git push origin master
8. reset branch by `git reset --hard origin/master`
9. git pull origin master

### Git merge commits
git rebase -i HEAD~{$numOfCommits}.   
git commit --amend.  
git push -f.  
http://jartto.wang/2018/12/11/git-rebase/

Undo:
git reset --hard @{1}

https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2
