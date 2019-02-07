---
layout: post
title:  "How to Create and Use Bash Scripts"
date:   2019-01-19 10:41:47 +0100
categories: OSX, Linux, SSH
---
<div class="message">
Bash is a Unix shell, which is a command line interface (CLI) for interacting with an operating system (OS). Any command that you can run from the command line can be used in a bash script. Scripts are used to run a series of commands.
</div>

On your mac open the Terminal. 


{% highlight bash %}
$ cd ~/.ssh/              #Go to your local ssh folder (hidden)
$ sudo ssh-keygen -t rsa  #generate a RSA private/public key pair

#then enter the name of the file in which you wish to save the key and
#enter a password for the key
{% endhighlight %}



Bash is available by default on Linux and macOS operating systems.

This is meant to be a short guide to getting started with making your first script, and learning some basic bash syntax.

Prerequisites

This guide is for macOS. I’ll be using /Users/laurenceb for all examples, but it will be /Users/your_username for you.

In this tutorial, we’re going to:
Create a bash script that can be run from any directory on the computer.
Learn about variables, conditions, looping, and user input with bash.

Create a simple Git deployment script.
1. Create a bin directory

The first step is to create a bin directory. bin is the standard naming convention of a subdirectory that contains executable programs.

You can make sure you’re in the main user directory by navigating to ~ (which is a shortcut for current user home directory, or /Users/laurenceb). This will also be the default directory Terminal always opens in. Typing pwd will confirm the location, as well.

Create bin in that folder, or wherever you want your bash scripts to live.

cd ~      # this takes us to /Users/laurenceb
mkdir bin # this creates /Users/laurenceb/bin
2. Export your bin directory to the PATH

Open .bash_profile, which will be located at /Users/laurenceb/.bash_profile, and add this line to the file. If .bash_profile doesn’t exist, create it.

export PATH=$PATH:/Users/laurenceb/bin
If you don’t see hidden files and directories, or those that begin with a ., press Command + SHIFT + . (dot)

3. Create a script file and make it executable

Go to your bin folder located in /Users/laurenceb.
{% highlight bash %}
cd bin
{% endhighlight bash %}
touch hello-world  #Create a file called hello-world 


#Open the file in your code editor of choice and type
#!/bin/bash
A bash script must always begin with #!/bin/bash to signify that the script should run with bash as opposed to any other shell. This is called a “shebang”. You can confirm where the bash interpreter is located with which bash.

which bash
/bin/bash
As is tradition, we’ll make a “Hello, World!” example to get this working.

hello-world
#!/bin/bash

echo Hello, World!
Now, you can try to run the file in the terminal.

hello-world
But it won’t work.

-bash: hello-world: command not found
We have to make it an executable file by changing the permissions.

chmod u+x hello-world
Now when you run the command, it will output the contents of the echo.

laurenceb@computer:~$ hello-world
Hello, World!
Congrats, you just got your first bash script up and running. You can also run this script from anywhere on the computer, not just in the bin directory.

Strings do not need to use single or double quotes by default. However, single and double quoted strings work as well. A single quoted string will not interpolate variables, but a double quoted string will.
Variables

A variable is declared without a $, but has a $ when invoked. Let’s edit our hello-world example to use a variable for the entity being greeted, which is World.

hello-world
#!/bin/bash

who="World"

echo Hello, $who!
laurenceb@computer:~$ hello-world
Hello, World!
Note that who = "World" is not valid – there must not be a space between variable and value.

Reading

We declared a variable in the last example, but we can also have the user set the value of a variable dynamically. For example, instead of just having the script say Hello, World!, we can make it ask for the name of the person calling the script, then output that name. We’ll do this using the read command.

hello-world
#!/bin/bash

echo Who are you?

read who

echo Hello, $who!
laurenceb@computer:~$ hello-world
Who are you?
laurenceb
Hello, laurenceb!
Conditionals

if statements use the if, then, else, and fi keywords. The condition goes in square brackets.

check-id
#!/bin/bash

echo How old are you?

read age

if [ "$age" -gt 20 ]
then
    echo You can drink.
else 
    echo You are too young to drink.
fi
laurenceb@computer:~$ check-id
How old are you?
28
You can drink.
Operators are slightly different in bash than what you might be used to.

Bash Operator	Operator	Description
-eq	==	Equal
-ne	!=	Not equal
-gt	>	Greater than
-ge	>=	Greater than or equal
-lt	<	Less than
-le	<=	Less than or equal
-z	== null	Is null
Looping

Bash uses for, while, and until loops. In this example, I’ll use the for...in loop to get all the files in a directory and list them.

#!/bin/bash

FILES=/Users/laurenceb/dev/*

for file in $FILES
do
  echo $(basename $file)
done
Git Deploy Example Script

As I mentioned previously, a bash script can use any commands you can use on the command line. An example of a script you might make for yourself is the one below, where the user is prompted for a git commit message and the process of adding, committing, and pushing to origin is all done with a single git-deploy command.

git-deploy
#!/bin/bash

read -r -p 'Commit message: ' desc  # prompt user for commit message
git add .                           # track all files 
git add -u                          # track deletes
git commit -m "$desc"               # commit with message
git push origin master              # push to origin
If you’ve never used Git, check out Getting Started with Git for a primer.
Then just run the command.

laurenceb@computer:$ git-deploy
Commit message: Making some vague updates
[master 0b0caaa] Making some vague updates
 3 files changed, 44 insertions(+), 1 deletion(-)
 create mode 100644 file.js
 create mode 100644 file2.js
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 823 bytes | 823.00 KiB/s, done.
Total 5 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/me/repo.git
   79f061b..0b0caaa  master -> master




I hope this article has been helpful for you to get started with bash scripting. 

bin stands for binary. /bin is a location for binary files which are programs and commands. note its not the only location where binary files can be stored

try chmod 700 hellow-world

try executing the file with ./hello-world

After exporting the path `export PATH=$PATH:/Users/laurenceb/bin`, it's best to reload the `bash_profile` using `source ~/.bash_profile`. This will allow users to use the `hello_world` script right away without restarting the shell/terminal.


November 7, 2018 at 9:02 pm
I used command
chmod +x hello-world
then
./hello-world
and it ran.

After adding "export PATH=$PATH:/YOUR_PATH_TO_BIN/bin" to your bash_profile, you'll need to reload it using `source ~/.bash_profile`. This will allow you to use the `hello-world` right away. Otherwise, you'll need to restart your terminal/shell.

You can always use add "./" before the file name (e.g. "./hello-world") to run the script from the current directory.

I believe you can make the script a bit more portable with the $HOME environment variable and a !#/usr/bin/env bash shebang. Either way, I found it very useful tutorial. Was wondering how to setup so I can call my scripts from anywhere. Thank you!

What is meaning of the -r and -p used in the git-deploy script.
-r	do not allow backslashes to escape any characters

-p prompt	output the string PROMPT without a trailing newline before

source: http://www.linuxcommand.org/lc3_man_pages/readh.html
