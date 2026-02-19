---
title: command-line-file
date: 02/18/2026
tags:
  - command-line
  - linux
links:
id: "202602172039"
---
# Command Line Working with Files

The following commands are used to create, move, copy, and delete files and folders.

# touch

Touch is a command that will create a new file or update modified and access time of file depending on whether it exist or not.

```
~/ > touch new.txt
```

Creates a new file called new.txt in the current directory that you are in.

If you don't want to create a new file then use the -c flag

```
~/ > touch -c new.txt
```

Only modifies the access and modify time of file if it already exists

## mkdir

To create new directories the mkdir command is used.

```
~/ > mkdir newDir
```

Directory called newDir will now exist in your current directory.

No output will be displayed by default, but if you wish to see a message after creating the new directory use the -v flag for verbose mode.

```
~/ > mkdir -v newDir
mkdir: created directory 'newDir'
```

You are able to create a new folder and a folder within that folder in one command using the -p flag

```
~/ > mkdir -p newDir/newChildDir
```

# rmdir

To remove a directory the rmdir command can be used but only if the directory is empty.

```
~/ > rmdir newDir
```

To remove both the child and parent directory in one command use the -p flag

```
~/ > rmdir -p newDir/childDir
```


## Other flags

- a: only modify the access time
- m: only modify the modified time

## mv

The command mv will move and/or rename a file.

To move a file to another directory

```
~/ > mv file1.txt target_dir/
```

Move multiple files with one command

```
~/ > mv file1.txt file2.txt file3.txt target_dir/
```

Move several files using wildcard

```
~/ > mv *.txt target_dir/
```

This moves any file with extension txt to target_dir

Rename the current file by putting the new filename in the target

```
~/ > mv file1.txt file4.txt
```

The file file1.txt is renamed to file4.txt in the current directory. Can also move and rename in a different directory

When moving to a new directory it will overwrite any file in that directory that has the same name. To prevent that use -b which will backup the existing file

```
~/ > mv -b file1.txt target_dir/
```

If file1.txt exist in that file then it will be appended with ~1 to become file1~1.txt.

To specify what the backup file is appended with use -S option

```
~/ > mv -S .back -b file1.txt target_dir/
```

The backup file will be file1.txt.back

## Other flags

- n: prevents overwriting
- i: ask if you want to overwrite
- f: force move if file is protected

## cp 

The copy command is cp.  This command can be used to copy one or more files to another directory.

Copy file in current directory to a new directory.

```
~/ > cp file1.txt newDir/
```

Copy several files at once to a new directory

```
~/ > cp file1.txt file2.txt newDir/
```

Copy any file in the current directory with the .txt file extension to a new directory

```
~/ > cp *.txt newDir
```

## Other Flags

- -r: move folders
- -b or --backup= backup existing files if exist in destination
- -i: prompt before overwriting

# rm

The remove command is rm.  This will remove one or more files depending on how many files you put as an option.

Remove file called file1.txt

```
~/ > rm file1.txt
```

Remove multiple files

```
~/ > rm file1.txt file2.txt
```

Remove any file with .log

```
~/ > rm *.log
```


If the directory contains files than the rmdir will not be able to delete the directory.  Instead use rm with the -r flag.

```
~/ > rm -r newDir/
```

## Flags

- -i: interactive.  Ask permission before deleting
- -f: force.  Delete file even it write protected



