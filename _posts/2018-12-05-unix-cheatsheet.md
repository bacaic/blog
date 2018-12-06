---
title: UNIX cheatsheet
author: Florian Courgey
layout: post
categories:
  - opensource
  - bash
  - shell
  - unix
---
Excerpt here.
<!--more-->

## UNIX filesystem
```bash
/bin # essential user binaries
  bash, cat, cp, grep, ls, nano, touch, tar, uname
/dev # devices
  null # to redirect unwanted stdout
/etc # config files (text based, so easily editable)
  crontab, hosts, init.d, passwd, timezone
/home # home folders for users
/lib # shared C libraries
/mnt # "mounted" drives
/opt # other softwares. Not binaries as there's 1 folder per software (with config, bin, lib, etc). Like Program Files on Windows.
/root # home folder for user "root"
/sbin # "system binaries"
  fdisk, fsck, init, reboot
/tmp # temp folder, gets emptied at reboot
/usr # "users", 
  bin/ games/ lib/ local/ sbin/ 
/var # "variable", folder for files that change often
  log/ mail/ www/
```
See [wikipedia Unix_filesystem](https://en.wikipedia.org/wiki/Unix_filesystem)

## Bash basics

```bash
id # Identification, displays current user (and uid), main group (and guid) and other groups (with guid)
who -H # Who is logged in, with column Headers
pwd # Print Working Dir
ls -alh # list All (even hidden .) as a List in a Human-readable format
ls -ld /usr/{,local/}{bin,sbin,lib} # ls only dir with Shell Expansion
echo -e "hello\n$(cat file)" > file # prepend to file
echo "hello" >> file # append to file
wget https://myfile.com -O output # save a web file to disk
```

## grep (find in file and files)

```bash
grep 'word' file1 file2
grep -w 'word_only' file1 file2
grep -r 'word' dir
```

## GCC Gnu C Compiler

```bash
gcc -v
gcc file1.c file2.c -O bin
gcc -Wall file1.c file2.c -O bin # to print all warnings
```

## PATH & softwares

`/usr/local/bin` to install any bin shared amongst users on the local machine

```bash
bash -c 'echo $PATH'
```
```terminal
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games # for Linux
/usr/local/bin /usr/bin /bin /usr/sbin /sbin # for Mac
```

## Symbolic links - symlinks

```bash
ln -s source target
ln -s ~/my_executable /usr/local/bin/my_executable # to add a binary to PATH
```

## TAR

```bash
tar cvf test.tar .# TAR current dir: <kbd class="none">c</kbd>=create, <kbd class="none">v</kbd>=verbose <kbd class="none">f</kbd>=file
tar tvf test.tar # list content of TAR file: <kbd class="none">t</kbd>=table of content
tar xvf test.tar # unTAR all files: <kbd class="none">x</kbd>=xtract
tar xvf test.tar file1 # unTAR specific file
```

## GZIP

ZIP format archives and compresses files and folders. >> Popular on Windows
GZIP format compresses 1 file. To compress multiple files with GZIP, they have to be archived into a single TAR file (called tarball). Hence .tar.gz. >> Popular on UNIX
```bash
gzip file1 # GZIP file1 to file1.gz (and delete file1)
gzip -k file1 # GZIP file1 to file1.gz and keep file1
gzip -r dir # GZIP all files in dir
gzip -d file1 # Decompress GZIP file
```

## ZIP & UNZIP

```bash
zip file.zip file1 file2
unzip file.zip # Unzip in current dir
unzip file.zip -d /target # Unzip in /target dir
unzip -l file.zip # List (display) content of zip
unzip -t file.zip # Test if valid zip
unzip -v file.zip # Display information such as Length, Method, CRC-32...
unzip -j file.zip # Unzip without directory structure (flat)
unzip -P plain_password file.zip # Unzip with plain text password
unzip -q file.zip # Unzip with quietly (no output)
```

[man zip](https://linux.die.net/man/1/zip),
[man unzip](https://linux.die.net/man/1/unzip)