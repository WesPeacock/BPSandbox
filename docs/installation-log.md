---
layout: page
title: Website Editing
permalink: /docs/installation-log/
---


### Setting up Ruby & Jekyll

Starting page for installing Ruby and Jekyll
https://jekyllrb.com/docs/installation/windows/
Install https://rubyinstaller.org/ download button
ridk install 1 then 3
PS D:\Wes\Documents\DLS\SFM2FLEx-Best-Practices> bundle add cd /ck

### Setting up Git for Windows

You probably want to install Git for windows too:
https://gitforwindows.org/

**git for Windows** uses *master* as the default branch. **Github** uses *main*. You can change that with this command:

```
git config --global init.defaultBranch main
```

### Setting up a local Jekyll instance

To initialize a new jekyll instance in CMD or Powershell.
 ``` bat
 cd ... # to above where you want to put the website repo.
 ...> jekyll new Website-reponame
 ...> cd Website-reponame
 ...\Website-reponame> git init
 ```
But if you have Git for Windows installed you probably want to do a git clone of the repository from github:
 * Find the repository and select the green button labelled Code
 ![green button](../assets/installation-log-33015840.png)
 and choose the clone option you want (If you choose the SSH option you have to have SSH set up on your computer with authorization for your github account).

* Open either Powershell or CMD

``` bat
cd ... # to above where you want to put the website repo.
# if you chose https
...> git clone https://github.com/Someone/SomeRepo.git
# OR if you chose SSH:
...> git clone git@github.com:Someone/SomeRepo.git
```

### Starting your local Jekyll server

`...\Website-reponame> bundle exec jekyll serve`

### Create the github remote repo & upload

Create new repo from your repo manager menu on github

``` bash
git remote add origin git@github.com:WesPeacock/SFM2FLEx-Best-Practices.git
git branch -M main
git push -u origin main
```

### Set up Github Pages

Go to Settings on the page and choose the **Pages** tab

I had set up the **just-the-docs** as my jekyll theme manually according to the just-the-docs page, so it was pre-chosen from github.


### Set up a Markdown Editor
I have been using Typora. It was free in Beta but is now $29.

A nice (but complex) free one is Atom.io. Instructions at:
[Installing Atom as a Markdown Editor](https://www.portent.com/blog/content/atom-markdown.htm)
