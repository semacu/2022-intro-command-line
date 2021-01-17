<img align="right" src=img/course_logo.png width="300">

# Introduction to the Command Line

- Practical: Monday 18th January 2021 3-5pm (GMT)
- Pre-recorded video materials for self-paced study with zoom support during the date/time of the practical
- Questions: helpdesk Q&A available in practical section in the [VLE](https://www.vle.cam.ac.uk/course/view.php?id=106822)
- Course [booklet](https://e.issuu.com/anonymous-embed.html?u=bioinfocambs&d=nstiibbsbioinformatics_20-21)



## Trainers

Alexia Cardona, Sergio Martínez Cuesta, Argyris Zardilis, Paul Judge and Cathy Hemmings



## Contents

- [Overview and setup](README.md#overview-and-setup)
- [Introducing the command line](README.md#introducing-the-command-line)
  - [Access the command line](README.md#access-the-command-line)
  - [Navigating your filesystem](README.md#navigating-your-filesystem)
  - [Tab completion](README.md#tab-completion)
- [Navigating Files and Directories](README.md#navigating-files-and-directories)
  - [Moving around the filesystem](README.md#moving-around-the-filesystem)
  - [Hidden directories](README.md#hidden-directories)
  - [Examining the contents of other directories](README.md#)
  - [Full versus Relative paths](README.md#)
- [Working with Files and Directories](README.md#)
  - [Working with Files](README.md#)
  - [Command History](README.md#)
  - [Examining Files](README.md#)
  - [Creating, moving, copying, and removing](README.md#)



## Overview and setup

Within the **Data Science for Bioinformatics** block, we are introducing the Unix command line (also known as *bash* or *shell*), which is a popular and important tool essential for bioinformatics. As part of a data-driven approach to answering research questions, the knowledge gained from this practical can be applied and transferred to different research domains.

Using the command line interface, we will demonstrate the basic structure of the Unix operating system and how we can interact with it using a basic set of commands. Applying this, we will learn how to navigate the filesystem, manipulate text-based data e.g. DNA sequencing `fastq` files and structure a simple pipeline out of these commands.

The practical demostration is recorded using the Apache Guacamole environment in place for the practical. Please follow the access details sent to you by Paul Judge and Alexia Cardona.

**Note:** optional -- it is possible to work through the practical in your own laptop or local machine after the course. To do this, you will need to start/install the command line and download the data for the practical following the instructions below.


### Command line

The command line is already available in the computer enviroment prepared for the practical. 

- Log in into the environment using your access details and click on the option `desktop` in the selection window. A display similar to the one below will become available
- Once in the Desktop, click on the `Terminal Emulator Use the command line` icon in the toolbar. A black command line box like the one displayed below will appear in the screen

<p align="center">
  <img width="500" src=img/guacamole.png>
</p>

<div align="center">Computer enviroment prepared for the practical</div>


**Note:** optional -- if you want to follow the practical in your own laptop after the course, you can start/install the command line using the following instructions:

  - **MacOS**: to start the command line go to `Applications` -> `Utilities` -> `Terminal`. Alternatively, in your keyboard press the Command button and the space bar  simultaneously, type "Terminal" (as you type it should auto-fill) and double click "Terminal" in the left sidebar
  - **Windows**: computers with Windows do not automatically have a Unix command line program installed. To install the Unix command line in Windows, follow this [video](https://www.youtube.com/watch?v=339AEqk9c-8) and/or the instructions available in the Windows tab [here](https://carpentries.github.io/workshop-template/#shell)
  - **Linux**: use the Terminal icon displayed in the main toolbar of most distributions (e.g. Ubuntu) to open the command line


### Data

The data for the practical is already available in the course environment in the directory: `/home/ubuntu/Course_Materials/shell_data/`

**Note:** optional -- if you want to follow the practical in your own laptop after the course, the data is available to download [here](https://github.com/semacu/2021-intro-command-line/blob/main/data/shell_data.zip). Click the `Download` button and save the `shell_data.zip` file into your Desktop. Then navigate to your Desktop and double-click on the zip file to uncompress it. A directory call `shell_data/` should then be available



## Introducing the command line

A **command line** is a computer program that presents an interface which allows you to control your computer using commands entered with a keyboard instead of clicking with the mouse on a **Graphical User Interface (GUI)**.

There are many reasons to learn about the command line:

- *Many bioinformatics tools can only be used through a command line interface*, or have extra capabilities in the command line version that are not available in the GUI
- *Learning command line will allow you to automate repetitive tasks* and leave you free to do more exciting things
- *The command line makes your computational work less error-prone and more reproducible*. Your computer keeps a record of every step that you’ve carried out and others can check your work or apply your process to new data
- *Most supercomputers and cloud computing systems for running intense calculations can only be accessed through the command line*

<p align="center">
  <img width="500" src=img/cli_vs_gui.png>
</p>

<div align="center">Command line (top) vs GUI (bottom)</div>


### Access the command line

To start the command line follow the instructions described in the [Setup section](README.md#setup) above


### Navigating your filesystem

The part of the operating system responsible for managing files and directories is called the *filesystem*. It organizes our data into files, which hold information, and directories (also called "folders"), which hold files or other directories. Several commands are frequently used to create, inspect, rename, and delete files and directories.

Let’s find out where we are by running a command called `pwd` (which stands for "print working directory"). At any moment, our current working directory is our current default directory, i.e., the directory that the computer assumes we want to run commands in, unless we explicitly specify something else.

```bash
$ pwd
```
```
/home/ubuntu/Course_Materials
```

**Note**: The dollar `$` symbol is a prompt, which indicates that the command line is waiting for input. When typing commands, either from these practical or from other sources, do not type the prompt, only the commands that follow it. Your command line may use a character different from `$` to indicate a prompt and may add information before the prompt. If you type the command `PS1='$ '` into your command line, followed by pressing the `Enter` key, your window should look like our example in this practical. This isn’t necessary to follow along (in fact, your prompt may have other helpful information you may want to know about). This is up to you!

Let’s look at how our *filesystem* is organized. We can see what files and subdirectories are in this directory by running `ls`, which stands for "listing":

```bash
$ ls
```
```
shell_data
```

`ls` prints the names of the files and directories in the current directory in alphabetical order, arranged neatly into columns. We’ll be working within the `shell_data/` subdirectory containing the files for the practical. The command to change locations in our filesystem is `cd`, followed by a directory name to change our working directory. `cd` stands for "change directory".

Let’s say we want to navigate to the `shell_data/` directory we created above. We can use the following command to get there:

```bash
$ cd shell_data
```

Let’s look at what is in this directory:

```bash
$ ls
```
```
sra_metadata	untrimmed_fastq
```

We can make the `ls` output more comprehensible by using the flag -F, which tells `ls` to add a trailing / to the names of directories:

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
total 8
drwxr-x--- 2 ubuntu  ubuntu   4096 30 Jul  2015 sra_metadata
drwxr-xr-x 2 ubuntu  ubuntu   4096 15 Nov  2017 untrimmed_fastq
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

This directory contains two files with `.fastq` extensions. fastq is a format for storing information about DNA sequencing reads and their quality.

At the end of the day after a long stream of typing commands, you may want to clean all the output of your command line. To do so, type the command `clear`:

```bash
$ clear
```



### Tab Completion

Typing out file or directory names can waste a lot of time and it’s easy to make typing mistakes. Instead we can use `Tab` to autocomplete names as a shortcut. When you start typing out the name of a file or directory, then hit the `Tab` keyboard key, the command line will try to fill in the rest of the directory or file name.

Return to the `Course_Materials` folder:

```bash
$ cd ~/Course_Materials  # in command line jargon the symbol ~ means the home directory, here /home/ubuntu 
```

then enter:

```bash
$ cd she<Tab>   # here <Tab> means that you press the Tab keyboard button
```

Once you have pressed `Tab`, the command line will fill in the rest of the directory name for `shell_data`. Now press Enter.

Now change directory to `untrimmed_fastq`:

```bash
$ cd untrimmed_fastq
```

Using tab completion can be extremely helpful. However, it will only autocomplete a file or directory name if you have typed enough characters to provide a unique identifier for the file or directory you are trying to access, othwerwise it will show you the different options

For example, if we now try to list the files which names start with `SR` by using Tab complete:

```bash
$ ls SR<Tab>
```

The shell auto-completes your command to `SRR09`, because all file names in the directory begin with this prefix. When you hit `Tab` again, the shell will list the possible choices.

```bash
$ ls SRR09<Tab><Tab>
```
```
SRR097977.fastq  SRR098026.fastq
```

Tab completion can also fill in the names of programs, which can be useful if you remember the beginning of a program name.

```bash
$ pw<Tab><Tab>
```
```
pwd  pwdx    
```

**Note**: the results of the latter command may differ depending on your operating system


### Summary

We now know how to move around our filesystem using the command line. This gives us an advantage over interacting with the filesystem through a GUI (e.g. File Manager in Ubuntu or Finder in MacOS), it allows us to work on a remote server, carry out the same set of operations on a large number of files quickly and opens up many opportunities for using bioinformatics software that is only available in command line versions.

In the next sections, we’ll be expanding on these skills and seeing how using the command line enables us to make our workflow more efficient and reproducible.

Key points:

- The command line gives you the ability to work more effectively by using keyboard commands rather than a GUI
- Useful commands for navigating your file system include: `ls`, `pwd` and `cd`
- Most commands take options (flags) which begin with the symbol `-`
- Tab completion can reduce errors from mistyping and make work more efficient in the shell

<img align="right" src=img/coffee.png width="300">

## 5 min break

Take a short break before starting with the next section :)



## Navigating Files and Directories


### Moving around the filesystem

We’ve learned how to use `pwd` to find our current location within our filesystem. We’ve also learned how to use `cd` to change locations and `ls` to list the contents of a directory. Now we’re going to learn some additional commands for moving around within our filesystem.

Use the commands we’ve learned so far to navigate to the `shell_data/untrimmed_fastq` directory, if you’re not already there.

```bash
$ cd ~/Desktop/shell_data/untrimmed_fastq
```

What if we want to move back up and out of this directory and to our top level directory? Can we type `cd shell_data`? Try it and see what happens.

```bash
$ cd shell_data
```
```
-bash: cd: shell_data: No such file or directory
```

Your computer looked for a directory or file called `shell_data` within the directory you were already in. It didn’t know you wanted to look at a directory level above the one you were located in.

We have a special command to tell the computer to move us back or up one directory level.

```bash
$ cd ..
```

Now we can use `pwd` to make sure that we are in the directory we intended to navigate to, and `ls` to check that the contents of the directory are correct.

```bash
$ pwd
```
```
/Users/kzqv978/Desktop/shell_data
```

```bash
$ ls
```
```
sra_metadata	untrimmed_fastq
```

From this output, we can see that `..` did indeed take us back one level in our filesystem.

You can chain these together like so:

```bash
$ ls ../..
```

prints the contents of `/Users/kzqv978`


### Hidden directories





## License

This practical is derived from the workshop [Introduction to the Command Line for Genomics](https://datacarpentry.org/shell-genomics/) &copy; The Carpentries, which is distributed under a [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/). 

For further command line topics including redirection, writing scripts and project organisation, check out episodes 4-6 of the Carpentries workshop

