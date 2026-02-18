---
title: command-line-file-navigation
date: 02/17/2026
tags:
  - inbox
  - command-line
  - linux
links:
id: "202602172009"
---
# Command Line Navigation

The following are commands to help you know where you are, navigate to other directory, and list the contents of that directory.
## pwd Command

The command pwd will display the current directory that you are on.

```
~ > pwd
/home/user
```

If you are on a directory that is a symlink it will display the directory as follows

```
~/.config/nvim > pwd
/home/user/.config/nvim
```

If you want to display the directory of where the symlink is pointing towards use the -P flag

```
~/.config/nvim > pwd
/home/user/dotfiles/.config/nvim
```


##  cd command

The cd command is used to change directory.

```
~/ > cd Documents
```

Will move you into the documents folder.

```
~/Documents > cd ..
```

Use the .. to move back. You are able to move multiple folders backward and forward at a time.

```
~/ > cd Documents/stuff
~/ > pwd
/home/user/Documents/stuff
~/ > cd ../..
~/ > pwd
/home/user
```

Use the -P flag to move into the directory that symlink points to if available.

```
~/ > cd .config/nvim
```

Moves into ~/.config/nvim even though it is a symlink.

```
~/ > cd -P .config/nvim
```

Now you will be in /home/user/dotfiles/.config/nvim (or wherever your symlink points to)

## ls command

Command ls will list contents of the current directory.

```
~/src > ls
Makefile  README.md  src
```

Using -l flag will display the directory contents in long form

```
~/src > ls -l
drwxr-xr-x 2 andy andy 4096 Mar 18  2022 build
-rw-r--r-- 1 andy andy  163 Mar 18  2022 Makefile
-rw-r--r-- 1 andy andy  698 Mar 18  2022 README.md
drwxr-xr-x 2 andy andy 4096 Mar 18  2022 src
```

The -a flag will display all files and folders even hidden

```
~/src > ls -a
.  ..  build  .git  .gitignore	Makefile  README.md  src
```

Also note that as with all of the commands we can combine flags in one command.

```
~/src > ls -al
drwxr-xr-x  5 andy andy 4096 Mar 18  2022 .
drwxr-xr-x 20 andy andy 4096 Jan 10 14:40 ..
drwxr-xr-x  2 andy andy 4096 Mar 18  2022 build
drwxr-xr-x  8 andy andy 4096 Jan 10 22:21 .git
-rw-r--r--  1 andy andy    7 Mar 18  2022 .gitignore
-rw-r--r--  1 andy andy  163 Mar 18  2022 Makefile
-rw-r--r--  1 andy andy  698 Mar 18  2022 README.md
drwxr-xr-x  2 andy andy 4096 Mar 18  2022 src
```

## Other flags

- r: reverses the order shown
- t: sort by time, newest first
- S: sort by filesize largest first