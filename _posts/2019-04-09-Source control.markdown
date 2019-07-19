---
layout: post
title:  "Source Control in Xcode 10 - Git"
date:   2019-06-19
categories: iOS, developer
comments: true
published: true
---
 
### A disclaimer first of all

Here are some issues I have encountered using Git on Xcode 10.2.1 on Mojave 10.14.5.

A problem to warn you about is that some commits and actions need time to get displayed and will not be shown immediately when doing `command-2` or going to the source control tab in Xcode. This really did confuse me for a while. I thought I was doing something wrong, or that I should be giving up on git. Do not despair. This is apparently normal!

I tested 'discard changes' in the menu `Source Control` and it does not seem to work properly. Discard all changes is always mostly highlighted but the other option discard changes in file is not always! The second option would be quite useful. Dont understand what is happening there.. oh .. it is just very slow to update. I now got the option to discard athe changes in the file, it only took 5 minutes!

After discarding the local not committed changes and when I check out to another branch, it seems that I need to manually delete files because Xcode gives me the error message "File not found" . 

Another problem: Git should work in terminal as well. It did not. I get the message command not recognized!
Looking on stackOverflow I get this solution, install or update the Xcode command line:

``` bash
xcode-select --install
```
but it turns out this doesnt work anymore.   
The current solution is to go to the [apple developer site](https://developer.apple.com/download/more/) and download the last version of command line tools.( It is 1 Gb! it is necessary? I had already the command line tools installed..)
Do not despair, there is another solution! 
``` bash
xcode-select --reset
```
and this worked! after that my git commands were recognized...

## Source Control

Source control is amazing because it helps you more easily revert to older versions of your code, add new features without risk to your working app, see how your code has changed over time, and work as a team.  
We are going to look into detail of the source control built in Xcode: Git!

Git is a distributed version control system initially developed by Linus Torvalds, the principal force behind the development of the Linux kernel.  
When you create a new project Xcode will give you this option when you will be asked where to save the new project :

![image](/assets/img/git/1.png)


In the course of working on a project, you’ll usually add files, modify code, and change your project many times.  
When you make big changes to your project and the project is in a "known good" working state, it is usually a good idea to commit the changes to the repository.

Open the Source Control navigator, the second tab on the left panel. Use Command-2 as the keyboard shortcut.
Click on the master branch, then click the Initial commit in the editor window and you will see the details of Xcode’s automatic commit.
![image](/assets/img/git/2.png)
Go back to the main file explorer with Command-1.  
When you change a file you will see M for modified next to it.  The status “A” is for new files not yet committed to the repository.

![image](/assets/img/git/3.png)

## Commit

Compile your program and see that it runs without error messages.
Select Source Control\Commit… from the menu or do `alt-command-c`
![image](/assets/img/git/4.png)

You will see the screen split into two panes. The left pane shows the file in its current state with all changes made since the last commit.
Each change is checked by default. To exclude a specific change from this commit, uncheck it.
Before you can complete a commit, Xcode requires you to enter a commit message.  
These messages help you better understand at a glance the purpose of each commit.  

Now click `Commit`!

![image](/assets/img/git/5.png)

## Branching Out

By working on different branches, you can keep features separated and reduce your risk of totally breaking your project.
All of your work so far has been on the master branch which should always keep the main copy of your project.

![image](/assets/img/git/6.png)

Instead of the Commit button, switch to the Source Control navigator and click the gear icon in the lower left corner. Select Branch from “master”…. and name your new branch. After that you still need to commit the changes in the new branch!

## Discarding changes

You can selectively discard the changes you’ve made to the project. 
Select Source Control\Discard Changes in “...”  from the menu.

![image](/assets/img/git/7.png)

## How to revert back to working code

If you choose to discard changes made to a file, Git will restore the last committed version of the file and only the last.

select View\Version Editor\Show Comparison View from the menu. Alternatively, you can click the third button in the Editor section on the toolbar at the top right of the Xcode window.

![image](/assets/img/git/8.png)

The version editor is split into two panes

This allows you to compare two revisions of the selected file and works exactly like the comparison view in the Commit window. By default, your current source file is shown on the left and the most recent revision stored in the repository – Git calls this the HEAD – is shown on the right.

![image](/assets/img/git/9.png)

## Merging Branches

when you finish development of a feature and want to release it? Simple! You merge your development branch into your master branch.
Switch to the Source Control navigator, right-click on the master branch and select Branch from “master”….
![image](/assets/img/git/10.png)

## Create a .gitignore file
Some files do not need to be tracked because are internal and Xcode can regenerate them.
However this did not work for me in Terminal! If any tips please let me know in the comments!
the command would be:
``` bash
$ git config --global alias.ignore '!gi() { curl -L -s https://www.gitignore.io/api/$@ ;}; gi'
```

## Xcode and GitHub

You can add your GitHub credentials to Xcode. Open Xcode Preferences and select the Accounts tab. Press the + in the lower left corner and select GitHub as the account type. Xcode will prompt for your GitHub credentials
In the Source Control navigator, right-click on the project name (GitUseExample) at the top of the left-hand pane and select Create “aGitTutorial” Remote on GitHub….  

![image](/assets/img/git/11.png)


### sources

[A Ray Wenderlich tutorial ](https://www.raywenderlich.com/675-how-to-use-git-source-control-with-xcode-9)  
[StackOverflow about terminal and git](https://stackoverflow.com/questions/52522565/git-is-not-working-after-macos-mojave-update-xcrun-error-invalid-active-devel)  
[Command Line Tools](https://developer.apple.com/download/more/)  
