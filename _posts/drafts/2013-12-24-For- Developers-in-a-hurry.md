---
layout: post
title: How to get your website up and running with Jekyll and GitHub hosting 
published: false
---

(For developers in a hurry )
My great inspiration recently has been a course about Machine and Deep Learning from Jeremy Howard at the San Francisco University, currently free to follow as a MOOC on the ![fast.ai](https://course.fast.ai) website. One of the things he said remained with me. He said: 'Start a blog about the things you are learning even if you think you are not quite there yet, it does'nt matter. Writing will be of great help to understand the study material better, and it is a great exercise.'
So this is one thing which motivated me to start a blog and not just have a profile page. I gave myselt three days time to get this blog started. Started last Friday morning and by Friday midday I already spent two hours looking at different fonts. It means it took me two hours max to get the template uploaded and working! It is so fast to get going and I will explain how in this tutorial. I found a few bugs which were annoying. This theme has been released in 2013 and since then a few things have changed.
I am working on a macBook with High Sierra and I use a terminal. Windows users might need a different approach or they can try to download ![git bash](https://gitforwindows.org) for windows 

Why Jekyll? I wanted a blog which is customisable, and quick to get started. And Jekyll is free. It has also support for syntax highlighting which is great for coders and a number of other advantages, like supporting markdown which I love. It is such a perfect markup language for writing on the web.
oh, another inspiration for this blog has been ![daring fireball](https://daringfireball.net), he invented markdown by the way... but lets get started! 

### step 1

You need to create an account with GitHub. Git is one essential tool for developers so if you dont have an account yet head over to [GitHub](http://) com and create an account.

### step 2

Create an empty repository with the same name as your github profile handle.
ex, mine is "multitudes.github.io" 
And keep it on master. Clone or download the new repo to your mac or pc. It will be empty but with a hidden file .git which is the file keeping track of your versions.

### step 3

Github natively support the ![Jekyll](http://jekyllrb.com) plattform and will host one static website for you at no cost. Jekyll has templates and themes. you can see here some ![examples](https://jekyllrb.com/showcase/).

Clone or download the theme to your computer. Copy all the files minus the .git hidden file to your previously downloaded repo.
If you don’t see hidden files and directories, or those that begin with a ., press Command + SHIFT + . (the last one is a dot)

### step 4
Now it is the time to push the changes to your github account.
{% highlight bash %}

cd multitudes.github.io  # Go to your folder in terminal
git add -A               # Add everything you changed to the staging area
git status               # check status    
git commit -m "first commit"        # commit with a short message 
git push -u origin master           # push your changes to GitHub

{% endhighlight %}

Go to your page and check the result. You should see the template with the default.

### step 5
We will need to troubleshoot. I choose the Hyde and Poole ![Hyde and Poole](https://github.com/poole/hyde) theme because frankly I wanted something like the fastai website and it looks similar and quite simple.

However this theme is already a few years old and doesnt work out of the box anymore. No worries, only a few changes were necessary.
I will list them here. 
- edit the file CNAME and delete its contents. Save.
- edit your yml file and replace the 'highlighter : pigments' with rouge. Like this:
{% highlight bash %}
highlighter:      rouge
{% endhighlight %}
- replace the URL line with your URL
- comment out the line: "markdown:         redcarpet"

To comment it our set a '#' at the beginning of the line.

Then eventually the landing page will work but the about me site has no styling! We need to edit the CSS file and the head file as follows:

Replace the all instances of {{ base_url }} in the head.html file in _includes folder with {{ '/' | relative_url }} 
do the same in the sidebar.html. 
This is because of an issue caused by a git hub upgrade that broke this theme a while ago. 


## step 6
push the changes done locally on your github account. for this 
open your terminal and :


## step 7 
Need to check that the links are working. We Look at the folders posts.
The Jekyll pages are auto generated from those files. There is a certain format we need to keep. The title has to start with the date, followed by the name.. like this example:
2012-02-06-whats-jekyll.md
md is the markdown extension. You can read more about markdown ![here](https://daringfireball.net/projects/markdown/) and there are different flavours, but it is really easy to get started.
I would start to duplicate the post file with command-d (on a mac) and edit it. You can use your favourite editor or use brackets ![Brackets](http://brackets.io), which is free. The first few lines enclosed in '---' have to be present in every post. We change the title of course.

We add pictures with
![image-title-here](/path/to/image.jpg){:class="img-responsive"}

push the changes and see your first post on your new website!!


step 8 
This theme is customisable however the optional color schemes as described in the documentation  did not work for me. I think it is best to modify the CSS and add some HTML in the template. Fonts can be modified easily for instance I changed the font of the main title and the blog to the system fonts.  

step 9
Optional. You can set up a development environment for Jekyll on your computer. The necessary files and downloads are on their website, however expect to spend some time debugging various issues and bugs. I prefer to edit my post and push them to github an see the results there. 

step 10 a hint.
keep the draft of the post in the same folder, just add unpublished to the header above as follows:

published: false

The post will be unvisible until change to published.

ps extra point

How to do a pull request.
Go to the repository. In thia example I will go to the Hyde[Hyde](https://github.com/poole/hyde) theme
On the top right I will click on fork to save a copy in my repository.
I will start by copying the link on my clipboard an will open my terminal to download it locally.
git clone https://github.com/multitudes/hyde.git

cd hyde/

ls

open _config.yml 

I remove the line: relative_permalinks: true 
This setting is deprecated as has been removed from the latest version of Jekyll.

It would give me an error message if I keep it.

I do git status
add to the staging directory
git add _config.yml 
git commit -m "line removed: 'relative_permalinks: true'. This setting is deprecated" 

then 
origin is the place where the code originates from, so it is the remote repository on github, my fork copy. then I specify master which is the branch. In this case it was expressely requested from the source to submit pull requests to master..


git push origin master

go back to our fork.. go back to the original page.
click new pull request
click on compare across forks
need to select my repo and then click on pull request button.
Now it is up to the developer to reply or accept our changes and merge the two repos.
I can see on his page that I am not the only one who asked for changes and the requests are mostly unanswered. Anyway it is good practice!


I hope you enjoy this tutorial. Please see how to create a bash script to push your commits to github if you want to optimize your workflow.
 

Thanks for reading!