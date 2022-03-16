---
layout: default
title: Set up a Linux terminal
parent: Set up infrastructure
grand_parent: Workflow
nav_order: 20
---
Many of the instructions on this site assume you have a Linux terminal.  Windows Subsystem for Linux (WSL) is one way to get that on a Windows machine.  The preferred Linux system is Ubuntu, currently 18.04. The purpose for setting up a Linux terminal is that DLS has created some Perl scripts to do things (like add, delete, rename or rearrange fields, etc.) to the SFM files in order to make the file easier to import correctly into FLEx. These scripts can only be run in a Linux terminal.

1. ###  To install WSL:

- - - Depending on your version of Windows, you may need to update your Windows Settings to allow WSL.  (If your version of Windows is new enough, this may no longer be needed.)
      - [https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://www.google.com/url?q=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fwsl%2Finstall-win10&sa=D&sntz=1&usg=AOvVaw2rg8Oevb8P1rNg_joDWCyY)
    - Go to the Microsoft Store and look for Ubuntu
    ([https://www.microsoft.com/en-us/p/ubuntu-1804-lts/9n9tngvndl3q?activetab=pivot:overviewtab](https://www.google.com/url?q=https%3A%2F%2Fmicrosoft.com%2Fen-us%2Fp%2Fubuntu-1804-lts%2F9n9tngvndl3q%3Factivetab%3Dpivot%3Aoverviewtab&sa=D&sntz=1&usg=AOvVaw04REeFb4a6tD5U-9Dnmc-O)
   - Even though there are newer versions, we currently recommend using version 18.04 anyway, for various compatibility reasons.)
    - Install WSL with Ubuntu 18.04.
      - Note that you have to reboot after installing WSL.
      - When you first run it, it will ask you to create a username and password.  Be sure to write this down where you can find it in the future, as you will need it for the following steps, and you may need it sometime far into the future when you may have forgotten that you even created a password.
      - After you have installed WSL and have it running, you will want to tell it to update any software packages that were installed with it.  To do that, run the following command within the WSL terminal window:
        - sudo apt update && sudo apt upgrade
        - It will ask you for a password.  Provide the password you created when you installed WSL.

1.

   ### To install some Perl modules needed for the scripts on this site and other useful utilities and configuration:

- - - Run the following commands within the terminal window.  [Note:  if you select a string of text and copy it (for instance, using Ctrl-C on the commands on this site), then you can paste that string into the WSL terminal by right-clicking at the prompt.]
      - echo "export PERL_UNICODE=SDA" >> ~/.bashrc
      - echo 'export PERL5OPT="-Mutf8 -MEnglish"' >> ~/.bashrc
      - sudo apt install build-essential libxml-libxml-perl dos2unix zip unzip
    - The system should install a large number of packages. If it asks for permission, reply "yes"
      - sudo cpan install Config::Tiny
    - To test  your installation, the following command should return to the  command line without errors:
      - perl -E "use Config::Tiny; use XML::LibXML;"
    - Optionally install  Consistent Changes and the TECkit Unicode converter in the SIL packages repository:
      - (wget -O- https://packages.sil.org/keys/pso-keyring-2016.gpg | sudo tee /etc/apt/trusted.gpg.d/pso-keyring-2016.gpg)&>/dev/null
      - (. /etc/os-release && sudo tee /etc/apt/sources.list.d/packages-sil-org.list>/dev/null <<< "deb http://packages.sil.org/$ID $VERSION_CODENAME main")
      - sudo apt update
      - sudo apt install silcc teckit

It is beyond the scope of this material to explain how to use WSL, but the most important things you need to know are:

- - How to start it and get a terminal window
  - How to find a Windows folder/directory from the terminal
  - How to change directories within your Windows directory structure
  - How to run Perl

### Finding a Windows folder from the terminal in WSL

- - Linux documentation refers to Windows folders as "directories".
  - The way to change directory in Linux is with the command "cd" and the path you want to get to.
  - If you are typing a command and somehow get stuck (for instance, you have typed something where it is waiting for you to input something, but you don't know what, or you didn't mean to type that), you can get out of the command by typing Ctrl-D or Ctrl-C.  One or the other of those should get you back to the command prompt so you can start a new command.
  - Windows and Linux specify directories differently
    - \ vs / directory marker
    - Case is significant in Linux filenames and commands
    - name in quotes vs using \<space>
    - Some examples:
      - If you have a file named "Notes to Myself.txt" in a sub-directory "Stuff"
      - Windows can specify the file as:
        - ".\Stuff\Notes to Myself.txt" or ".\STUFF\NOTES TO MYSELF.TXT"
      - Linux uses:
        - ./Stuff/Notes\ to\ Myself.txt
  - To get to any of the folders on your Windows system, you have to start by specifying a path that starts with "/mnt/c/Users"  (This is called an absolute path, because it references the full path, starting from the root.  An absolute path references the same folder, no matter which folder you are in when you use it.)
  - For instance, to get to your Documents folder, you would give the command:

cd /mnt/c/Users/<MyUserName>/Documents

- - The command prompt in the terminal shows you the path of the folder you are currently in.
  - Once you are in any Windows folder, you can use relative paths with the cd command (see below).

### Navigating directories

- - Normally you would use a command like "cd PathToMyFolder" where "PathToMyFolder" represents the path to the directory you want to get to.  "PathToMyFolder" can be either an absolute path or a relative path.
  - If the folder you want to get to (for instance, WorkingFolder) is a child of the one you are in, you only have to say "cd WorkingFolder"  (This is called a "relative path", because you are only specifying the portion of the path relative to where you are currently located.)
  - You can use "cd .." to get to the directory that is the parent of the one you are in.
  - You can use "cd -" to go to the previous directory you were in before the last cd command.
  - Once you are in a directory, you can use the command "ls" to see what is in the directory. "ls -la" gives a more complete listing with
  - Autocompletion:  When you are changing to a directory, you can type "cd" followed by the beginning of a filename.  Once you have typed a few letters, press tab, and it will attempt "auto completion".  If there is only one filename that matches, it will fill that out.  If there is more than one, it will show you all that match.  If you type a few more letters, you may have enough to press tab again and get the match.
  - Autocompletion works whenever you are giving a command that expects a file or path.
  - If you gave a command at the command line, but it wasn't quite right, and you need to adjust just a small portion of it, you can use the "up arrow" to get to your previous command, and then edit it.  Using "up arrow" more than once gets you to more commands that you gave earlier.

### Using redirection and pipes in WSL

In WSL, many commands can read their input either from a file or from a previous command in a pipeline of commands. There are four that control the flow of data between commands or files.

- The bar character, "|", between two commands says send the output to the next command.
- The less than character, "<" says get the input for a command from the file following the <
- The greater than character, ">" says send your output to a file.
- Two greater than characters, ">>" says add your output to the end of a file.



Some additional things to note:

- If there's no ">" or ">>" the output of the last command goes to the screen.
- Error and status messages are normally sent to the screen.
- In documentation etc., the input, output and error/status message streams are named **STDIN**, **STDOUT** and **STDERR**.
- If you have **command1 | command2** then **STDOUT** for **command1** becomes **STDIN** for **command2.**



There's an example of piping in the [instructions to enumerate the markers](https://www.google.com/url?q=https%3A%2F%2Fsites.google.com%2Fsil.org%2Fimporting-sfm-to-flex%2Fworkflow%2Fii-analyze-the-database%2Fb-enumerate-the-markers&sa=D&sntz=1&usg=AFQjCNGtE4OEyRaWGM8K8D6HNWWOYMhSUg)[ in a file](https://www.google.com/url?q=https%3A%2F%2Fsites.google.com%2Fsil.org%2Fimporting-sfm-to-flex%2Fworkflow%2Fii-analyze-the-database%2Fb-enumerate-the-markers&sa=D&sntz=1&usg=AFQjCNGtE4OEyRaWGM8K8D6HNWWOYMhSUg). Let's look at it in detail:

- **cat filename.db | sed -e "s/ .\*$//" | sort | uniq -c > sfm-list.txt**

There's 4 commands in the pipeline:

- **cat** gets a filename(s) on the command line and sends the contents to **STDOUT.**

- **cat filename.db | sed  -e "s/ .\*$//"**
- is the same as:
- **sed -e "s/ .\*$//" < filename.db**

- **sed** -e does some regular expression commands on **STDIN** and then passes the result to  **STDOUT**

- This pipe does the sed command **s/from/to/**
- **s/from/to/** takes text that matches **from** and changes it into **to**.
- the **to** can be empty, in which case **from** is deleted.
- The effect here is to delete everything following the first space, i.e., everything but the leading SFM.
- That converts each line into just its SFM.

-  **sort** does what it says; it sorts **STDIN** and then passes the result to  **STDOUT**

- this puts all the same SFMs together.

- **uniq** reads **STDIN** and ignores repeats. then passes the result to **STDOUT**
  - - - The **-c** option adds a count of how many times a line was repeated.
  - The **> sfm-list.txt** at the end store the sorted, counted list of SFM marker into **sfm-list.txt**
