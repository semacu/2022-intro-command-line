<img align="right" src=img/course_logo.png width="200">

# Introduction to the Command Line

- Practical: Monday 18th January 2021 3-5pm (GMT)
- Pre-recorded video materials for self-paced study and helpdesk Q&A available in the [VLE](https://www.vle.cam.ac.uk/course/view.php?id=106822)



## Contents

- [Overview](README.md#overview)
- [Setup](README.md#setup)
  - [Data](README.md#data)
  - [Command line](README.md#command-line)
- [Introducing the command line](README.md#introducing-the-command-line)
  - [Access the command line](README.md#access-the-command-line)
  - [Navigating your file system](README.md#navigating-your-file-system)
  - [Tab completion](README.md#tab-completion)
  - [Summary 1](README.md#summary-1)



## Overview

Within the **Data Science for Bioinformatics** block, we are introducing the Unix command line (also known as *bash* or *shell*), which is a popular and important tool essential for bioinformatics. As part of a data-driven approach to answering research questions, the knowledge gained from this practical can be applied and transferred to different research domains.

Using the command line interface, we will demonstrate the basic structure of the Unix operating system and how we can interact with it using a basic set of commands. Applying this, we will learn how to navigate the filesystem, manipulate text-based data e.g. DNA sequencing `fastq` files and structure a simple pipeline out of these commands.



## Setup

It is possible to work through the practical on your laptop or local machine. To do this, you will need to download the data that we will use in the practical and start/install the command line if not available in your device. Instructions for doing this are below.


### Data

The data is available to download [here](https://github.com/semacu/2021-intro-command-line/blob/main/data/shell_data.zip). Click the `Download` button and save the `shell_data.zip` file into your Desktop. Then navigate to your Desktop and double-click on the zip file to uncompress it. A directory call `shell_data/` should be available


### Command line

**MacOS**: to start the command line go to `Applications` -> `Utilities` -> `Terminal`. Alternatively, in your keyboard press the Command button and the space bar  simultaneously, type "Terminal" (as you type it should auto-fill) and double click "Terminal" in the left sidebar

**Windows**: computers with Windows do not automatically have a Unix command line program installed. To install the Unix command line in Windows, follow this [video](https://www.youtube.com/watch?v=339AEqk9c-8) and/or the instructions available in the Windows tab [here](https://carpentries.github.io/workshop-template/#shell)

**Linux**: use the Terminal icon displayed in the main toolbar of most distributions (e.g. Ubuntu) to open the command line



## Introducing the command line

A command line is a computer program that presents an interface which allows you to control your computer using commands entered with a keyboard instead of controlling graphical user interfaces (GUIs) with a mouse/keyboard combination.

There are many reasons to learn about the shell:

- Many bioinformatics tools can only be used through a command line interface, or have extra capabilities in the command line version that are not available in the GUI
- Learning command line will allow you to automate repetitive tasks and leave you free to do more exciting things
- The command line makes your computational work less error-prone and more reproducible. Your computer keeps a record of every step that you’ve carried out and others can check your work or apply your process to new data
- Most supercomputers or cloud computing for running expensive calculations can only be accessed through the command line


### Access the command line

To start the command line depending on your operating system, have a look at the [Setup section](README.md#setup). We will spend most of our time learning about the basics of the command line by manipulating some experimental data


### Navigating your file system

The part of the operating system responsible for managing files and directories is called the file system. It organizes our data into files, which hold information, and directories (also called "folders"), which hold files or other directories. Several commands are frequently used to create, inspect, rename, and delete files and directories.

Let’s find out where we are by running a command called `pwd` (which stands for "print working directory"). At any moment, our current working directory is our current default directory, i.e., the directory that the computer assumes we want to run commands in, unless we explicitly specify something else. Here, the computer’s response is `/Users/kzqv978`, which is the top level directory within our cloud system:

```bash
$ pwd
```
```
/Users/kzqv978
```

**Note**: The dollar `$` symbol is a prompt, which indicates that the command line is waiting for input. When typing commands, either from these practical or from other sources, do not type the prompt, only the commands that follow it. Your command line may use a character different from `$` to indicate a prompt and may add information before the prompt. If you type the command `PS1='$ '` into your command line, followed by pressing the `Enter` key, your window should look like our example in this lesson. This isn’t necessary to follow along (in fact, your prompt may have other helpful information you may want to know about). This is up to you!

Let’s look at how our file system is organized. We can see what files and subdirectories are in this directory by running ls, which stands for "listing":

```bash
$ ls
```
```
Applications	Desktop		Documents	Downloads	Library		Movies		Music		Pictures	Public
```

`ls` prints the names of the files and directories in the current directory in alphabetical order, arranged neatly into columns. We’ll be working within the `Desktop/` subdirectory where we downloaded and created the `shell_data/` directory. The command to change locations in our file system is `cd`, followed by a directory name to change our working directory. `cd` stands for "change directory".

Let’s say we want to navigate to the `shell_data/` directory we created above. We can use the following commands to get there:

```bash
$ cd Desktop
$ cd shell_data
```

Let’s look at what is in this directory:

```bash
$ ls
```
```
sra_metadata	untrimmed_fastq
```

We can make the ls output more comprehensible by using the flag -F, which tells ls to add a trailing / to the names of directories:

```bash
$ ls -F
```
```
sra_metadata/		untrimmed_fastq/
```

Anything with a "/" after it is a directory. Things with an asterisk after them are programs. If there are no decorations, it’s a file.

`ls` has lots of other options. To find out what they are, we can type:

```bash
$ man ls
```

`man` (short for manual) displays detailed documentation (also referred as man page or man file) for commands. It is a powerful resource to explore commands, understand their usage and flags. Some manual files are very long. You can scroll through the file using your keyboard’s down arrow or use the `Space` key to go forward one page and the `b` key to go backwards one page. When you are done reading, hit `q` to quit.

The option `-l` option for the `ls` command is used often as it displays more detailed information for each item in the directory:

```bash
$ ls -l
```
```
total 0
drwxr-x---@ 3 kzqv978  RD\Domain Users    96B 30 Jul  2015 sra_metadata
drwxr-xr-x@ 4 kzqv978  RD\Domain Users   128B 15 Nov  2017 untrimmed_fastq
```

The additional information given includes the name of the owner of the file, when the file was last modified, and whether the current user has permission to read and write to the file, as we will see later

No one can possibly learn all of these arguments, that’s what the manual page is for. You can (and should) refer to the manual page or other help files as needed.

Let’s go into the `untrimmed_fastq` directory and see what is in there.

```bash
$ cd untrimmed_fastq
$ ls -F
```
```
SRR097977.fastq		SRR098026.fastq
```

This directory contains two files with `.fastq` extensions. fastq is a format for storing information about sequencing reads and their quality. 


### Tab Completion

Typing out file or directory names can waste a lot of time and it’s easy to make typing mistakes. Instead we can use tab to autocomplete names as a shortcut. When you start typing out the name of a file or directory, then hit the `Tab` keyboard key, the command line will try to fill in the rest of the directory or file name.

Return to your Desktop:

```bash
$ cd ~/Desktop  # in command line jargon ~ means the home directory 
```

then enter:

```bash
$ cd she<tab>
```

Once you press `Tab`, the command line will fill in the rest of the directory name for `shell_data`

Now change directories to `untrimmed_fastq` in `shell_data`

```bash
$ cd shell_data
$ cd untrimmed_fastq
```

Using tab complete can be very helpful. However, it will only autocomplete a file or directory name if you have typed enough characters to provide a unique identifier for the file or directory you are trying to access.

For example, if we now try to list the files which names start with `SR` by using tab complete:

```bash
$ ls SR<tab>
```

The shell auto-completes your command to `SRR09`, because all file names in the directory begin with this prefix. When you hit `Tab` again, the shell will list the possible choices.

```bash
$ ls SRR09<tab><tab>
```
```
SRR097977.fastq  SRR098026.fastq
```

Tab completion can also fill in the names of programs, which can be useful if you remember the beginning of a program name.

```bash
$ pw<tab><tab>
```
```
pwd         pwd_mkdb    pwhich      pwhich5.18  pwhich5.28  pwpolicy    
```

Please note that the results of the latter command will be different depending on your operating system


### Summary 1

We now know how to move around our file system using the command line. This gives us an advantage over interacting with the file system through a GUI (e.g. Finder in MacOS) as it allows us to work on a remote server, carry out the same set of operations on a large number of files quickly, and opens up many opportunities for using bioinformatics software that is only available in command line versions.

In the next sections, we’ll be expanding on these skills and seeing how using the command line shell enables us to make our workflow more efficient and reproducible.

Key points:

- The command line gives you the ability to work more efficiently by using keyboard commands rather than a GUI
- Useful commands for navigating your file system include: `ls`, `pwd` and `cd`
- Most commands take options (flags) which begin with the symbol `-`
- Tab completion can reduce errors from mistyping and make work more efficient in the shell



## 5 min break

Take a short break before starting with the next section






## License

This practical is derived from the [Introduction to the Command Line for Genomics](https://datacarpentry.org/shell-genomics/) &copy; The Carpentries, which is distributed under a [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/)

