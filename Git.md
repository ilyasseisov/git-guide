# Git

---

## git config

---

### set user name and email

$ git config --global user.name "your name"
$ git config --global user.email email@gmail.com

### check config

cat ~/.gitconfig

### git init

- initialization of git in dir

### un-git a directory

- rm -rf .git (have to be in the .git dir)

### git status

- check status of the repo

### git add

- adds files to staging
- ex: git add file.txt
- ex: git add --all
- ex: git add . [entire_dir]

### git commit

- commits files to local repo
- ex: git commit -m 'Initial commit'

### git log

- to see history of changes
- ex: git log --oneline (concise version)

## create SSH key

- navigate to home dir - _cd ~_
- check the presence of SSH keys - _ls -la .ssh/_
- generate SSH key - _ssh-keygen -t ed25519 -C "mygithubemail@gmail.com"_
- check the presence of SSH keys - _ls -la .ssh/_

### git remote add

- to connect a remote repo
- ex: git remote add origin git@github.com:ACCOUNT_NAME/first-project.git

### git remote -v

- to check that remote repo has been connected

## Branches

- if commit is a snapshot of project files, then a branch is a timeline

### git push

- to push commits from local repo to remote one
- ex: git push origin master

## Hash

- hash is a primary ID of a commit.
- looks like this (40 chars)"314725593efb1eef5e2ef8eca4be4cd768d0df22"

## HEAD

- it's a file that displays the last commit

### how to use

1. cd .git
2. cat HEAD | inside: "ref: refs/heads/master"

- "refs/heads/master" is file named "master" in dir refs/heads

3. cat refs/heads/master | inside: "e007f5035f113f9abca78fe2149c593959da5eb7"

- hash of a last commit

---

## File statuses

1. untracked - newly created
2. tracked - already added and commited
3. staged - in staging area (after git add command)
4. modified - commited and changed

## Commit messages

- concise and informative
- conventional commits: https://www.conventionalcommits.org/en/v1.0.0/
- ex (corporate): "LGS-239: Add new numbers to the list A1"
- ex (conventional): "feat: add total number of week orders"
- ex (Github style): "Edit #334, add temprature chart"

## How to edit commit

### Edit the last commit

- git commit --amend --no-edit
- "--amend" flag tells git to update the last commit and not to create a new one
- "--no-edit" flag tells git to leave the message as it is

#### Explanation of the process

Let's say we have two files _index.html_ and _style.css_ we have added and commited only _index.html_. Now to add _style.css_ to the last to commit we should:

1. git add style.css
2. git commit --amend --no-edit

And changes can go and on.

### Edit the last commit and its message

- git commit --amend -m "New message"

### Unstage files

- git restore --staged <file>
- git restore --staged .

### Reset repo back to <HASH>

- git reset --hard <commit hash>
- delete all changes from staging and work area till that commit

### Undo file changes

- git restore <file>

### git diff

- to see changes in modified files
- git diff <HASH1> <HASH2>

### gitignore

- file to add files and dirs to not to track
- _\*.jpeg_ - to ignore all _.jpeg_ files

---

### git clone

- to clone repo from Github
- ex: git clone git@github.com:yandex-praktikum/git-clone-lesson.git

### fork

- copy an existing Github repo to your account and then modify it

## Branches

### git branch

- to see the list of all branches
- _(\*)_ - a branch you are currently at

### git branch <NAME>

- to create a new branch

#### branch naming rules

- <KW>/<NAME>
- ex: feature/add-animation-on-scroll
- ex: bugfix/scroll-ios

### git checkout <NAME>

- to change the branch
- ex: git checkout _bugfix/scroll-ios_

#### commit navigation

_~N_ - (N is a number). N is counted back from 0 (current commit).

- HEAD or HEAD~0 is a current commit
- HEAD~1 is a previous commit from a current one
- HEAD~2 is second back commit from a current one

- ex: git diff HEAD~2 HEAD will show a difference between current commit (HEAD) and second back (HEAD~2)
