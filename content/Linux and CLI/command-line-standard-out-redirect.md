---
title: Command Line Standard Out Redirection to File
date: 02/20/2026
tags:
  - linux
  - command-line
links:
id: "202602172117"
---
# Command Line Standard Out Redirection to File

Standard out from commands can be redirected to a file or from a file to a command.

## Redirect Output to a File


Redirect standard out to a file by using >

```
echo "hello" > hello.txt
```

This will insert the word hello to a file called hello.txt.  If hello.txt file already existed then contains would be erased.

## Redirect Output and Append


To append standard out to an exsiting file use >>. 

```
echo "hello" >> hello.txt
```

## Redirect from Right to Left

The < takes stdout from right and inputs it in the left.

```
cat < hello.txt
```

This takes the text of the file and inputs it in the cat command
