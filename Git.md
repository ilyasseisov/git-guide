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
