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

- it's a file that displays the last commit on the branch
- also may refer to a current branch

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
- git checkout -b feature-branch development
  (This will create a new branch named _feature-branch_ and switch to it, based on the _development_ branch.)

#### branch naming rules

- <KW>/<NAME>
- ex: feature/add-animation-on-scroll
- ex: bugfix/scroll-ios

### git checkout <NAME>

- to change the branch
- ex: git checkout _bugfix/scroll-ios_

### git checkout to create local versions of remote branches

- sometimes after cloning a repo you see only main branch, to recreate other branches use _git checkout feature/one_

#### commit navigation

_~N_ - (N is a number). N is counted back from 0 (current commit).

- HEAD or HEAD~0 is a current commit
- HEAD~1 is a previous commit from a current one
- HEAD~2 is second back commit from a current one

- ex: git diff HEAD~2 HEAD will show a difference between current commit (HEAD) and second back (HEAD~2)
- ex: git diff master master~1

### git branch -d <NAME>

- to delete a branch

### git merge

- to merge a _feature_ or _bugfix_ branches with a _main_

1. checkout to a main branch: `git checkout main`
2. merge: git merge _feature/new-feature_

#### conflict

A conflict is a situation in which one or more people have modified the _same file_. At the same time, the results of such modifications are incompatible and only a human can figure out which of the variants is correct.

In development, for example, conflicts most often arise when multiple programmers change code in the same place at the same time.

##### How to resolve conflicts: general guidelines

During merging, Git itself highlights files that it was unable to merge. To understand the situation, you need to do the following:

1. Look in the file where the conflict occurred.
2. Examine both sides of the conflict - your version and your colleague's version. Your task is to correctly merge the two versions into a final version, so that the changes of both sides are not lost. The new version will become the current up-to-date version.
3. _Manually_ remove or tweak irrelevant changes, if any.
4. Prepare the changes for saving and commit.

### git push - send local branch to Github

1. create a branch in a local repo
2. do some commits
3. git push -u origin <BRANCH_NAME>

#### pull request

In the world of software development, a pull request is a way for one person to suggest changes to a codebase and ask another person to review and merge those changes into the main code.

It helps ensure that everyone on the team is on the same page and that the changes are high-quality and won't cause any issues in the project. It's like a way of collaborating and making sure everything runs smoothly!

##### PR algo

1. You work on a task in your branch - for example, you write code for new functionality.
2. You finish your work, and then create a pull-request.
3. Your colleagues check that the code looks neat and concise and that the program works correctly; they also leave comments. This process is called code review.
4. After the final approval, you upload your branch to the main one.

##### Workflow in teams

1. git clone <URL>
2. git branch feature-1
3. git checkout feature-1
4. do some commits
5. git push -u origin feature-1

### git pull

- to download changes from remote repo

When you run _git pull_ without specifying a branch name while being on the _main_ branch, Git will pull changes from the remote branch that _main_ is tracking, which is typically _origin/main_. To see the remote tracking branch use _git branch -vv_.

For example, if you're currently working on the _develop_ branch locally, running _git pull_ will fetch changes from the corresponding branch _(develop)_ on the remote repository and merge them into your local _develop_ branch.

Algo:

1. checkout to _master_ branch
2. git pull

#### best practice: algo before PR

1. _git checkout master_ - checkout to master
2. _git pull_ - pull new changes to master
3. _git checkout my-branch_ - checkout to your branch
4. _git merge master_ - merge main into my-branch
5. _git push -u origin my-branch_ - push my-branch into remote repo

#### feature branch workflow

In that flow work on every new feature/bugfix starts in a new branch. And the every branch is merged into main.

#### collaboration workflow in companies

1.1. clone project
1.2. create a new branch (_feature-new_)
1.3. check current status of a project

Before starting work each day, it's a good practice to ensure your local repository is up-to-date with the latest changes from the remote repository.

Run _git pull origin develop_ (assuming the main development branch is named _develop_). This command fetches changes from the remote _develop_ branch and merges them into your current local branch (_feature-new_).

1.4. work and make commits
1.5. push that branch to remote origin
1.6. create a PR

2.1. review PR at Github
2.2. add comments to things to change
2.3. set status "Request changes"

3.1. fix changes, commit and push
3.2. leave a message at Github (note the commits' hash)

4.1. check that all changes are correct
4.2. set status "Approve"

5.1. merge branch into main
5.2. delete branch

6.1. git checkout main
6.2. git pull
6.3. delete branch locally

### Git commands visualization

https://dev.to/lydiahallie/cs-visualized-useful-git-commands-37p1

## Algo for solo projects

Assuming we have _main_ branch as a primary.

1. create new _feature_ or _fix_ branch
2. work there and do commits
   when finished
3. checkout to _main_
4. _git merge --no-ff --no-edit *feature*_
5. delete _feature_ branch

This is a good approach as it creates a merge commit.

## Exit Vim

Esc + Shift + zz

## Situation: remote _origin/master_ branch was reverted back and you need to reflect those changes in the local repo

1. _git pull_
   This will pull changes, but the state of the local files will remain as it was. And git will offer to push changes.

2. _git reset --hard origin/master_
   This will set the state of local files as in remote repo.

   or

---

1. _git pull --rebase_
