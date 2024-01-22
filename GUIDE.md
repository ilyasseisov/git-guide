# GIT

---

## Terminal

---

# cd (change directory)

## cd ~

- navigates to home directory

## cd /

- navigates to root directory

## cd [dirname] - into that folder

- ex: $ cd github
- ex: $ cd github/open-source-project

## cd .. - one level up

# pwd

- displays a current directory

# ls

- to see all files and folders in a current dir

## ls -a

- to all files + hidden ones

# touch [filename]

- to create a file
- ex: $ touch my-new-file.txt

# mkdir [dirname]

- to create a folder
- ex: $ mkdir new-dir

# cp [filename] [directory to copy in]

- to copy a file
- ex: cp file.txt dir

# mv [filename] [directory to move in]

- to move (cut) a file
- ex: mv file.txt dir

# cat [filename]

- read a file
- ex: cat file.txt

# rm [filename]

- to delete a file
- ex: rm file.txt

## rm -r

- to delete a directory with all files
- ex: rm -r dir

# rmdir [dirname]

- to delete a directory
- ex: rmdir dir

---

---

## git config

---

# set user name and email

$ git config --global user.name "your name"
$ git config --global user.email email@gmail.com

# check

cat ~/.gitconfig
