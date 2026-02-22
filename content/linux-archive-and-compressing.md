---
title: Linux Archive and Compress
date: 02/22/2026
tags:
  - linux
  - command-line
links:
id: "202602221331"
---
# Linux Archive and Compressing

Below are Linux shell commands that you can use to archive and compress your files.

## Tar command 

Tar command is used to bundle files into one file.

To create a new tar bundle

```
tar -cvf files.tar file1.txt file2.txt
```

- cf: create a new archive, followed by the archive name
- v: specifies verbose mode (optional

List contents of tar

```
tar -tf files.tar
```

Extract contents from tar

```
tar -xvf files.tar -C extract_files
```

## Gzip command

Gzip will compress the file.  Once you bundle the files into one you may want to compress that file to save some space

To compress the file to the following

```
gzip files.tar 
```

This will create a files.tar.gz file. If multiple files are specified then multiple gzip files will be created. One for each file.

If you need to uncompress the file, then the following command will work

```
gzip -d files.tar.gz
```

## Tar and GZIP in one command

It is possible to create a tar file and then compress it to a gzip format in one command.

```
tar -czvf files.tar.gz files_dir
```

To uncompress and extract the files

```
tar -xzvf files.tar.gz -C extracted-dir
```

## Zip command

The zip file format is the compress archive that is compatible with Windows operation systems. The zip command will allow you to compress into that format.

```
zip -r files.zip files
```


## Unzip command

The unzip command is used to extract files from a zip format.

```
unzip -d zip_files files.zip
```
