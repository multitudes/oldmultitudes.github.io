---
layout: post
title:  "How to Create and Use Bash Scripts"
date:   2019-01-19 10:41:47 +0100
categories: OSX, Linux, SSH
comments: true
---
<div class="message">
Bash is a Unix shell, which is a command line interface (CLI) for interacting with an operating system (OS). Any command that you can run from the command line can be used in a bash script. Scripts are used to run a series of commands.
</div>

This is meant to be a short guide to getting started with making your first script, and learning some basic bash syntax.
Bash is available by default on Linux and macOS operating systems.  
scroll to the bottom to see how to integrate a bash script with GitHub.

This guide is for macOS. I’ll be using `/Users/laurenceb` for all examples, but it will be `/Users/your_username` for you.

Now on your mac open the Terminal. 

In this tutorial, we’re going to create a bash script that can be run from any directory on the computer.

### Create a bin directory.

The first step is to create a bin directory if not already existing. `bin` is the standard naming convention of a subdirectory that contains executable programs (bin stands for binary). `/bin` is a location for binary files which are programs and commands. note its not the only location where binary files can be stored

Navigate to your home directory `~` (which is a shortcut for current user home directory, or `/Users/laurenceb`). Typing `pwd` will confirm your location.
Create bin in that folder, or wherever you want your bash scripts to live.

{% highlight bash %}
cd ~      # this takes us to /Users/laurenceb
mkdir bin # this creates /Users/laurenceb/bin
{% endhighlight %}

### Export your bin directory to the PATH.

Open `.bash_profile`, which will be located at `/Users/laurenceb/.bash_profile`, and add this line to the file. If `.bash_profile` doesn’t exist, create it.

{% highlight bash %}
export PATH=$PATH:/Users/laurenceb/bin
{% endhighlight %}

After exporting the path `export PATH=$PATH:/Users/laurenceb/bin`, it's best to reload the `bash_profile` using `source ~/.bash_profile`. Otherwise you can restart the shell/terminal or open a new tab.

If you don’t see hidden files and directories, or those that begin with a `.`, press `Command` `+` `SHIFT` `+` `.`

### Create a script file and make it executable

Go to your bin folder located in `/Users/laurenceb`.

{% highlight bash %}

cd bin
touch hello-world  # Create a file called hello-world 
# Open the file in your code editor of choice ex nano
nano hello-world
# and type on the very beginning of the file:
#!/bin/bash
# followed by
echo Hello, World!

{% endhighlight %}

A bash script must always begin with `#!/bin/bash` to signify that the script should run with bash as opposed to any other shell. This is called a “shebang”. heck which bash interpreter you have in your terminal:
A bash script must always begin with `#!/bin/bash` to signify that the script should run with bash as opposed to any other shell. This is called a “shebang”. 

{% highlight bash %}

which bash

{% endhighlight %}

As is tradition, we’ll make a “Hello, World!” example to get this working.

Now, you can try to run the file in the terminal but you would get 
`-bash: hello-world: command not found`
We have to make it an executable file by changing the permissions.
{% highlight bash %}
chmod u+x hello-world
{% endhighlight %}

Now when you run the command, it will output the contents of the echo.

{% highlight bash %}
laurenceb@computer:~$ hello-world
{% endhighlight %}
You just got your first bash script up and running. You can also run this script from anywhere on the computer, not just in the bin directory. If the bash entry to declare the PATH is not correct you will only be able to execute the file with `./hello-world` in the same directory.

Strings do not need to use single or double quotes by default. However, single and double quoted strings work as well. A single quoted string will not interpolate variables, but a double quoted string will.
Variables
A variable is declared without a $, but has a $ when invoked. Let’s edit our hello-world example to use a variable for the entity being greeted, which is World.

{% highlight bash %}
#!/bin/bash
who="World"
echo Hello, $who!
{% endhighlight %}

Note that `who = "World"` is not valid – there must not be a space between variable and value.

### Reading
We declared a variable in the last example, but we can also have the user set the value of a variable dynamically. For example, instead of just having the script say Hello, World!, we can make it ask for the name of the person calling the script, then output that name. We’ll do this using the read command.

{% highlight bash %}
hello-world
#!/bin/bash
echo Who are you?
read who
echo Hello, $who!
{% endhighlight %}

### Conditionals
if statements use the if, then, else, and fi keywords. The condition goes in square brackets.
{% highlight bash %}
#!/bin/bash
echo How old are you?
read age
if [ "$age" -gt 20 ]
then
    echo You can drink.
else 
    echo You are too young to drink.
fi
{% endhighlight %}

Operators are slightly different in bash.

<table>
  <thead>
    <tr>
      <th>Bash Operator</th>
      <th>Operator</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>-eq</td>
      <td>==</td>
      <td>Equal</td>
    </tr>
    <tr>
      <td>-ne</td>
      <td>!=</td>
      <td>Not equal</td>
    </tr>
    <tr>
      <td>-gt</td>
      <td>></td>
      <td>Greater than</td>
    </tr>
    <tr>
      <td>-ge</td>
      <td>>=</td>
      <td>Greater than or equal</td>
    </tr>
    <tr>
      <td>-lt</td>
      <td><</td>
      <td>Less than</td>
    </tr>   
    <tr>
      <td>-le</td>
      <td><=</td>
      <td>Less than or equal</td>
    </tr>
    <tr>
      <td>-z</td>
      <td>==null</td>
      <td>Is null</td>
    </tr>
    
  </tbody>
</table>
### Looping

Bash uses for, while, and until loops. In this example, I’ll use the for...in loop to get all the files in a directory and list them.

{% highlight bash %}
#!/bin/bash
FILES=/Users/laurenceb/dev/*
for file in $FILES
do
  echo $(basename $file)
done
{% endhighlight %}

### Git Deploy Example Script

A bash script can use any commands you can use on the command line. An example of a script you might make for yourself is the one below, where the user is prompted for a git commit message and the process of adding, committing, and pushing to origin is all done with a single command.

Check git is installed on your mac! 

{% highlight bash %}
git --version
{% endhighlight %}

If it is not 'command not found' is returning then install Xcode from the App Store.
In XCode, install `Command Line Tools: > Preferences > Downloads > Command Line Tools`

I assume you have a GitHub account already set up. Go to your repository on GitHub and you will see a button: `Clone or Download`. There you will have the option to select `HTTPS` or `SSH`. Choose `HTTPS` and get the URL. For more infos see this link: [cloning a repository](https://help.github.com/en/articles/cloning-a-repository).

Choose where you want to have that folder on your hard disk. I used my home directory.


{% highlight bash %}
cd ~            # go to the home folder
# This will clone the repo to your hard disk
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
{% endhighlight %}

Make then this script in the bin directory

{% highlight bash %}
#!/bin/bash
read -r -p 'Commit message: ' desc  # prompt user for commit message
git add -A                          # track added deleted files
git commit -m "$desc"               # commit with message
git push origin master              # push to origin
{% endhighlight %}

The read command:
-r	do not allow backslashes to escape any characters
-p prompt	output the string PROMPT without a trailing newline before
enter `man read` in terminal to see more!

Again you will need to give the correct permissions:

{% highlight bash %}
chmod u+x hello-world
{% endhighlight %}

Restart the terminal with `source .bash.profile`
or open a new window

{% highlight bash %}
source ~/.bash_profile 
{% endhighlight %}

Then just run the command `push_git` in terminal.

![push_git](/assets/img/push_git.png)

You can always use add `./` before the file name (e.g. `./hello-world`) to run the script from the current directory.

I hope this article has been helpful for you to get started with bash scripting. 



