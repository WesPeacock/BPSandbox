---
layout: default
title: General setup
parent: Set up infrastructure
grand_parent: Workflow
nav_order: 10
---

The first phase involves setting the stage for a successful import process.
Importing an SFM file into FLEx is a complicated venture.
To increase the chances of success, it is best to follow each of these steps in detail.

1. Set up communication methods between import specialist and linguist.
  - Email?  Skype?  How often?
2. Determine goal of import: Webonary, PDF or paper publication, further work in FLEx (by whom?), archive.
These answers will shape how much effort you put into different aspects of the import project.
3. If the goal is to publish on Webonary
  - Encourage linguist to apply for the site right away ([Webonary Application](https://www.webonary.org/application-for-webonary-account/) )
  - Ask them to start thinking about front/back matter, and connect them with someone who can help them start putting that on the site, even before the import is done.
  - Explain that you will place sample uploads on this site as you go along.
  - Explain the difference between being able to see the sample site, versus the site actually being published.
4. Determine if any aspects of the data are sensitive.  When creating folders for data or talking about it with other import specialists, respect the wishes of the linguist regarding whether to use the actual language name or not, or names of specific individuals.
5. Decide if you will be working in a Windows terminal or a Linux terminal.
  - In a Windows terminal, you can use Strawberry Perl to run Perl scripts.  However, there are additional details needed for working in a Windows environment, and those are not covered here.
  - A simple way to get a Linux terminal is to [install Ubuntu](/docs/workflow/set-up-infrastructure/set-up-a-linux-terminal) for Windows 10.
6. Be sure you understand how to [access perl scripts on Github](/docs/workflow/set-up-infrastructure/how-to-download-perl-scripts-from-github).
7. Set up your working directory.
  - This would be whatever folder on your Windows system contains the data files you are working on.
  - You may have a lot of files associated with this project.  You may find it easiest to make a "working folder" that starts out with only the Toolbox .db file that you will be importing.  As you go through the process on this site, you will be adding scripts and creating various versions of that file in this folder, so it may be helpful to have everything else related to the project stored in separate folders before you begin.
  - As you encounter scripts that you need, you would download those into this directory also.  Most of them assume that the script is in the same directory as the data file.
8. Establish an approach for "version control" for the data.
  - Why do we need "version control"?
    - It is helpful to have "breakpoints" as you make different changes to the file.  If you need to "undo" some significant change you made, the easiest thing may be to revert to an earlier stage.
    - It is also important to be able to use a diff tool to compare the "before" and "after" when you make a significant change.  The changes we make are sweeping enough, with enough possible "edge cases", that it is crucial that we validate each one.  You want few enough changes between each version of the file that you could glance over most of the changes.
      - [kdiff3](https://www.google.com/url?q=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fkdiff3%2Ffiles%2F&sa=D&sntz=1&usg=AFQjCNElk951FMD4g4BmZjCn3I9rwFS_Rw) is a really helpful visual diff tool
      - There are many others out there; it doesn't matter, as long as you use something.
  - How can we do version control?
    - If you are comfortable with git or other source control software, you can use that.  [Details not posted here, at least not for now.]
    - If you are not comfortable with something like "git", you can mimic that by making a copy of the file every so often, and giving it a new name.  For instance, the first modification of the file might be dictionary-mod01.db.  You will make some edits in that, and then just before you make some other major change, you will copy it to a file called dictionary-mod02.db.  Each time you copy the file to a new name, you will make an entry in your log indicating what change was made between the versions.
  - What "best practices" will help with the "do it yourself" version control?
    - If you are using the "make copies along the way" approach to having breakpoints, at some point you may find that you need to go back to an earlier version of the file.  At that point it is helpful to clear out the files that you made changes to but have not abandoned.  There are several possibilities:
      - You could delete them.
      - You could create a folder called "Pass1" and move them into there.
      - You could make a copy of your entire working directory and begin working over in this new copy.  Before you begin working, delete the files you have abandoned.  The previous copy of the working folder still has them, in case you do need to get them back.  (For instance, you may start out working in a folder called Working-2020.01.05.  After you have done some work, you want to "clear your workspace".  Make a copy of that whole folder and call the new one Working-2020.01.19.  In the new folder delete unwanted files (or start with it empty, and only bring in the ones you want), and then continue working in that folder.
