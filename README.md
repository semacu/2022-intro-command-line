<img align="right" src=img/course_logo.png width="300">

# Introduction to the Command Line

- Practical helpdesk: Thursday 20th January 2022 4-5pm (GMT)
- Pre-recorded video materials for self-paced study with in-person support during the date/time of the practical helpdesk
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
  - [Examining the contents of other directories](README.md#examining-the-contents-of-other-directories)
  - [Full versus Relative paths](README.md#full-versus-relative-paths)
  - [Hidden directories and files](README.md#hidden-directories-and-files)
- [Working with Files and Directories](README.md#working-with-files-and-directories)
  - [Working with Files](README.md#working-with-files)
  - [Command History](README.md#command-history)
  - [Examining Files](README.md#examining-files)
  - [Creating, moving, copying and removing](README.md#creating-moving-copying-and-removing)



## Overview and setup

Within **Block A - Data Science for Bioinformatics**, we are introducing the Unix command line (also known as *bash* or *shell*), which is a popular and important tool essential for bioinformatics. As part of a data-driven approach to answering research questions, the knowledge gained from this practical can be applied and transferred to different research domains.

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
$ cd ~/Course_Materials/shell_data/untrimmed_fastq
```

What if we want to move back up and out of this directory e.g. onto our top level directory? Can we type `cd shell_data`? Try it and see what happens.

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

Now we can use `pwd` to make sure that we are in the directory we intended to go, and `ls` to check that the contents of the directory are correct.

```bash
$ pwd
```
```
/home/ubuntu/Course_Materials/shell_data
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

which prints the contents of `/home/ubuntu`


### Examining the contents of other directories

By default, the `ls` command lists the contents of the working directory (i.e. the directory you are in). You can always find the directory you are in using the `pwd` command. However, you can also give `ls` the names of other directories to view. Navigate to your home directory if you are not already there.

```bash
$ cd
```

Then enter the command:

```bash
$ ls Course_Materials/shell_data
```
```
sra_metadata	untrimmed_fastq
```

This will list the contents of the `shell_data` directory without you needing to navigate there.

The `cd` command works in a similar way.

Try entering:

```bash
$ cd
$ cd Course_Materials/shell_data/untrimmed_fastq
```

This will take you to the `untrimmed_fastq` directory without having to stop over an intermediate directory.

**Note:** running the command `cd` is equivalent to `cd ~`, which is also equivalent to `cd /home/ubuntu`. They all take us to the home directory. Although you may think that the home directory is `/home`, in most Unix systems it is actually `/home/ubuntu`


### Full versus Relative paths

The `cd` command takes an argument which is a directory name. Directories can be specified using either a *relative* path or an *absolute* path. The directories on the computer are arranged into a hierarchy. The full path tells you where a directory is in that hierarchy. Navigate to the home directory, then enter the `pwd` command.

```bash
$ cd
$ pwd
```
```
/home/ubuntu
```

This is the *absolute* path of your home directory. This tells you that you are in a directory called `ubuntu`, which sits inside a directory called `home` which sits inside the very top directory in the hierarchy. The very top of the hierarchy is a directory called `/` which is usually referred to as the root directory. So, to summarize: `ubuntu` is a directory in `home` which is a directory in `/`.

If we want to get to `untrimmed_fastq` using the *absolute* path, enter the following command:

```bash
$ cd /home/ubuntu/Course_Materials/shell_data/untrimmed_fastq
```

Alternatively, if you want to get to the same directory using a `relative` path:

```bash
$ cd 
$ cd Course_Materials/shell_data/untrimmed_fastq
```

These two commands have the same effect, they both take us to the `untrimmed_fastq` directory. The first uses the *absolute* path, giving the full address from the `home` directory. The second uses a *relative* path, giving only the address from the working directory. An *absolute* path always starts with a `/`. A *relative* path does not.

A *relative* path is like getting directions from someone on the street. They tell you to “go right at the stop sign, and then turn left on Main Street”. That works great if you’re standing there together, but not so well if you’re trying to tell someone how to get there from another country. An *absolute* path is like the GPS coordinates. It tells you exactly where something is no matter where you are right now.

You can usually use either an *absolute* path or a *relative* path depending on what is most convenient. If we are in the `home` directory, it is more convenient to enter the *absolute* path. If we are in the working directory, it is more convenient to enter the `relative` path since it involves less typing.

Over time, it will become easier for you to keep a mental note of the structure of the directories that you are using and how to quickly navigate amongst them.


### Hidden directories and files

Hidden files and folders in Unix are often used to store settings and configuration information. They start with `.`, for example `.my_hidden_directory`. There is a hidden directory and a hidden file within the `shell_data` directory. Explore the options for `ls` to find out how to see hidden directories and list its contents.

```bash
$ man ls
```

The `-a` option is short for all and says that it causes `ls` to "not ignore entries starting with ." This is the option we want.

```bash
$ cd ~/Course_Materials/shell_data
$ ls -a
```
```bash
.  ..  .DS_Store  .hidden	sra_metadata  untrimmed_fastq
```

The name of the hidden directory is `.hidden` and the name of the hidden file is `.DS_Store`. We can navigate to the `.hidden` directory using `cd`

```bash
$ cd .hidden
```

And then list the contents of the directory using `ls`

```bash
$ ls
```
```
youfoundit.txt
```

The name of the text file in the hidden directory is `youfoundit.txt`


### Summary

The root directory is the highest level directory in your filesystem and contains files that are important for your computer to perform its daily work. While you will be using the root (`/`) at the beginning of your *absolute* paths, it is important that you avoid working with data in these higher-level directories, as your commands can permanently alter files that the operating system needs to function. 

In many cases, trying to run commands in root directories will require special permissions which are not discussed here, so it’s best to avoid them and work within your `home` directory. Dealing with the `home` directory is very common. The tilde character, `~`, is a shortcut for your `home` directory. In our case, the root directory is two levels above our home directory, so `cd` or `cd ~ `will take you to `/home/ubuntu` and cd `/` will take you to `/`.

The commands `cd` and `cd ~` are very useful for quickly navigating back to your `home` directory. We will be using the `~` character in later sections to specify our `home` directory.

Note that in most commands the flags can be combined together in no particular order to obtain the desired results/output.

```bash
$ cd ~/Course_Materials/shell_data
$ ls -Fla
```

Key points:

- The `/`, `~`, and `..` characters represent important navigational shortcuts
- *Relative* paths specify a location starting from the current location, while *absolute* paths specify a location from the root of the filesystem
- Hidden files and directories start with `.` and can be viewed using `ls -a`

<img align="right" src=img/coffee.png width="300">

## 5 min break

Take a short break before starting with the next section :)



## Working with Files and Directories

### Working with Files

#### Our data set: FASTQ files

Now that we know how to navigate around our directory structure, let’s start working with our sequencing files. We did a sequencing experiment and have two results files, which are stored in our `untrimmed_fastq` directory.

#### Wildcards

Navigate to your `untrimmed_fastq` directory:

```bash
$ cd ~/Course_Materials/shell_data/untrimmed_fastq
```

We are interested in looking at the FASTQ files in this directory. We can list all files with the `.fastq` extension using the command:

```bash
$ ls *.fastq
```
```
SRR097977.fastq  SRR098026.fastq
```

The `*` character is a special type of character called a wildcard, which can be used to represent any number of any type of character. Thus, `*.fastq` matches every file that ends with `.fastq`

This command:

```bash
$ ls *977.fastq
```
```
SRR097977.fastq
```

lists only the file that ends with `977.fastq`

`echo` is a built-in shell command that writes its arguments, like a line of text to standard output. The `echo` command can also be used with pattern matching characters, such as wildcard characters. Here we will use the `echo` command to see how the wildcard character is interpreted by the shell.

```bash
$ echo *.fastq
```
```
SRR097977.fastq SRR098026.fastq
```

The `*` is expanded to include any file that ends with `.fastq`. We can see that the output of `echo *.fastq` is the same as that of `ls *.fastq`

What would the output look like if the wildcard could not be matched? Compare the outputs of `echo *.missing` and `ls *.missing`:

```bash
$ echo *.missing
```
```
*.missing
```

```bash
$ ls *.missing
```
```
ls: cannot access '*.missing': No such file or directory
```


### Command History

If you want to repeat a command that you’ve run recently, you can access previous commands using the up arrow on your keyboard to go back to the most recent command. Likewise, the down arrow takes you forward in the command history.

A few more useful shortcuts:

- `Ctrl`+`C` will cancel the command you are writing, and give you a fresh prompt
- `Ctrl`+`R` will do a reverse-search through your command history. This is very useful.
- `Ctrl`+`L` or the `clear` command will clear your screen.

You can also review your recent commands with the `history` command, by entering:

```bash
$ history
```

to see a numbered list of recent commands.


### Examining Files

We now know how to switch directories, run programs, and look at the contents of directories, but how do we look at the contents of files?

One way to examine a file is to print out all of the contents using the program `cat`

Enter the following command from within the `untrimmed_fastq` directory:

```bash
$ cd ~/Course_Materials/shell_data/untrimmed_fastq
$ cat SRR098026.fastq
```

This will print out all of the contents of the `SRR098026.fastq` to the screen.

`cat` is a terrific program, but when the file is really big, it can be annoying to use. The program, `less`, is useful for this case. `less` opens the file as read only, and lets you navigate through it. The navigation commands are identical to the `man` program.

Enter the following command:

```bash
$ less SRR098026.fastq
```

Some navigation commands in `less`: `Space` - to go forward and `q` - to quit

`less` also gives you a way of searching through files. Use the `/` key to begin a search. Enter the word you would like to search for and press `Enter`. The screen will jump to the next location where that word is found.

If you hit `/` then `Enter`, `less` will repeat the previous search. less searches from the current location and works its way forward. For instance, let’s search forward for the sequence `TTTTT` in our file. You can see that we go right to that sequence, what it looks like, and where it is in the file. If you continue to type `/` and hit `Enter`, you will move forward to the next instance of this sequence motif. If you instead type `?` and hit `Enter`, you will search backwards and move up the file to previous examples of this motif.

Remember, the `man` program actually uses `less` internally and therefore uses the same commands, so you can search documentation using `/` as well!

There’s another way that we can look at files, and in this case, just look at part of them. This can be particularly useful if we just want to see the beginning or end of the file, or see how it’s formatted.

The commands are `head` and `tail` and they let you look at the beginning and end of a file, respectively.

```bash
$ head SRR098026.fastq
```
```
@SRR098026.1 HWUSI-EAS1599_1:2:1:0:968 length=35
NNNNNNNNNNNNNNNNCNNNNNNNNNNNNNNNNNN
+SRR098026.1 HWUSI-EAS1599_1:2:1:0:968 length=35
!!!!!!!!!!!!!!!!#!!!!!!!!!!!!!!!!!!
@SRR098026.2 HWUSI-EAS1599_1:2:1:0:312 length=35
NNNNNNNNNNNNNNNNANNNNNNNNNNNNNNNNNN
+SRR098026.2 HWUSI-EAS1599_1:2:1:0:312 length=35
!!!!!!!!!!!!!!!!#!!!!!!!!!!!!!!!!!!
@SRR098026.3 HWUSI-EAS1599_1:2:1:0:570 length=35
NNNNNNNNNNNNNNNNANNNNNNNNNNNNNNNNNN
```

```bash
$ tail SRR098026.fastq
```
```
+SRR098026.247 HWUSI-EAS1599_1:2:1:2:1311 length=35
#!##!#################!!!!!!!######
@SRR098026.248 HWUSI-EAS1599_1:2:1:2:118 length=35
GNTGNGGTCATCATACGCGCCCNNNNNNNGGCATG
+SRR098026.248 HWUSI-EAS1599_1:2:1:2:118 length=35
B!;?!A=5922:##########!!!!!!!######
@SRR098026.249 HWUSI-EAS1599_1:2:1:2:1057 length=35
CNCTNTATGCGTACGGCAGTGANNNNNNNGGAGAT
+SRR098026.249 HWUSI-EAS1599_1:2:1:2:1057 length=35
A!@B!BBB@ABAB#########!!!!!!!######
```

The `-n` option to either of these commands can be used to print the first or last n lines of a file e.g. to display the first and the last read of the file

```bash
$ head -n 4 SRR098026.fastq
```
```
@SRR098026.1 HWUSI-EAS1599_1:2:1:0:968 length=35
NNNNNNNNNNNNNNNNCNNNNNNNNNNNNNNNNNN
+SRR098026.1 HWUSI-EAS1599_1:2:1:0:968 length=35
!!!!!!!!!!!!!!!!#!!!!!!!!!!!!!!!!!!
```

```bash
$ tail -n 4 SRR098026.fastq
```
```
@SRR098026.249 HWUSI-EAS1599_1:2:1:2:1057 length=35
CNCTNTATGCGTACGGCAGTGANNNNNNNGGAGAT
+SRR098026.249 HWUSI-EAS1599_1:2:1:2:1057 length=35
A!@B!BBB@ABAB#########!!!!!!!######
```

As a bonus, explore the section "Details on the FASTQ format" at your own pace in the following [link](https://datacarpentry.org/shell-genomics/03-working-with-files/index.html) to learn about the encoding of sequencing reads in FASTQ files and the nucleotide base calling quality.


### Creating, moving, copying and removing

Now we can move around in the file structure, look at files, and search files. But what if we want to copy files or move them around or get rid of them? Most of the time, you can do these sorts of file manipulations without the command line, but there will be some cases where it will be impossible. You’ll also find that you may be working with hundreds of files and want to do similar manipulations to all of those files. In cases like this, it’s much faster to do these operations at the command line.

#### Copying Files

When working with computational data, it’s important to keep a safe copy of that data that can’t be accidentally overwritten or deleted. For this lesson, our raw data is our FASTQ files. We don’t want to accidentally change the original files, so we’ll make a copy of them and change the file permissions so that we can read from, but not write to, the files.

First, let’s make a copy of one of our FASTQ files using the `cp` command. Navigate to the `shell_data/untrimmed_fastq` directory and enter:

```bash
$ cd ~/Course_Materials/shell_data/untrimmed_fastq
$ cp SRR098026.fastq SRR098026-copy.fastq
$ ls -F
```
```
SRR097977.fastq  SRR098026-copy.fastq  SRR098026.fastq
```

We now have two copies of the `SRR098026.fastq` file, one of them named `SRR098026-copy.fastq`. We’ll move this file to a new directory that we will create shortly called `backup` where we’ll store our backup data files.

#### Creating Directories

The `mkdir` command is used to make a directory. Enter `mkdir` followed by a space, then the directory name you want to create:

```bash
$ mkdir backup
```

#### Moving / Renaming

We can now move our backup file to this directory. We can move files around using the command `mv`:

```bash
$ mv SRR098026-copy.fastq backup
$ ls backup
```
```
SRR098026-copy.fastq
```

The `mv` command is also how you rename files. Let’s rename this file to make it clear that this is a backup:

```bash
$ cd backup
$ mv SRR098026-copy.fastq SRR098026-backup.fastq
$ ls
```
```
SRR098026-backup.fastq
```

#### File Permissions

We’ve now made a backup copy of our file, but just because we have two copies, it doesn’t make us safe. We can still accidentally delete or overwrite both copies. To make sure we can’t accidentally mess up this backup file, we’re going to change the permissions on the file so that we’re only allowed to read (i.e. view) the file, not write to it (i.e. make new changes).

View the current permissions on a file using the `-l` (long) flag for the `ls` command:

```bash
$ ls -l
```
```
-rw-r--r-- 1 ubuntu ubuntu 43332 Jan 17 22:55 SRR098026-backup.fastq
```

The first part of the output for the `-l` flag gives you information about the file’s current permissions. There are ten slots in the permissions list. The first character in this list is related to file type, not permissions, so we’ll ignore it for now. The next three characters relate to the permissions that the file owner has, the next three relate to the permissions for group members, and the final three characters specify what other users outside of your group can do with the file. We’re going to concentrate on the three positions that deal with your permissions (as the file owner).

<p align="center">
  <img width="500" src=img/permissions.png>
</p>

Here the three positions that relate to the file owner are `rw-`. The `r` means that you have permission to read the file, the `w` indicates that you have permission to write to (i.e. make changes to) the file, and the third position is a `-`, indicating that you don’t have permission to carry out the ability encoded by that third space (this is the space where `x` or executable ability is stored).

Our goal for now is to change permissions on this file so that you no longer have `w` or write permissions. We can do this using the `chmod` (change mode) command and subtracting `-` the write permission `-w`.

```bash
$ chmod -w SRR098026-backup.fastq
$ ls -l 
```
```
-r--r--r-- 1 ubuntu ubuntu 43332 Jan 17 22:55 SRR098026-backup.fastq
```

#### Removing

To prove to ourselves that you no longer have the ability to modify this file, try deleting it with the `rm` command:

```bash
$ rm SRR098026-backup.fastq
```
```
rm: remove write-protected regular file 'SRR098026-backup.fastq'? 
```

You should enter `n` for no. If you enter `n` (for no), the file will not be deleted. If you enter `y`, you will delete the file. This gives us an extra measure of security, as there is one more step between us and deleting our data files.

Important: The `rm` command permanently removes the file. Be careful with this command. It doesn’t just nicely put the files in the Trash. They’re really gone.

By default, `rm` will not delete directories. You can tell `rm` to delete a directory using the `-r` (recursive) option. Let’s delete the backup directory we just made.

Enter the following command:

```bash
$ cd ..
$ rm -r backup
```

This will delete not only the directory, but all files within the directory. If you have write-protected files in the directory, you will be asked whether you want to override your permission settings.

#### Summary

- You can view file contents using `less`, `cat`, `head` or `tail`
- The commands `cp`, `mv` and `mkdir` are useful for manipulating existing files and creating new directories
- You can view file permissions using `ls -l` and change permissions using `chmod`
- The `history` command and the up arrow on your keyboard can be used to repeat recently used commands.

#### Exercise 1

Starting in the `shell_data/untrimmed_fastq/` directory, do the following:

1. Make sure that you have deleted your `backup` directory and all files it contains.
2. Create a backup of each of your FASTQ files using `cp`. (Note: You’ll need to do this individually for each of the two FASTQ files. We haven’t learned yet how to do this with a wildcard.)
3. Use a wildcard to move all of your backup files to a new backup directory.
4. Change the permissions on all of your backup files to be write-protected.

#### Solution 1

Take five minutes to try out the steps above, then check out the [solution](ex/solution1.md)

Thank you for your attention! :smile:

As a bonus to continue learning about the command line at your own pace if you are interested: try the advanced searching of sequences in the fastq files and the writing of `for` loops in lecture 4 of the [Introduction to the Command Line for Genomics by The Carpentries](https://datacarpentry.org/shell-genomics/04-redirection/index.html). 

Have fun!



## License

This practical is derived from the workshop [Introduction to the Command Line for Genomics](https://datacarpentry.org/shell-genomics/) &copy; The Carpentries, which is distributed under a [CC BY 4.0 license](https://creativecommons.org/licenses/by/4.0/). 
