---
layout: post
title: For developers in a hurry: How to get your website up and running with Jekyll and GitHub hosting 
---

My great inspiration has been a course about Machine and Deep Learning from Jeremy Howard at the San Francisco University, currently free to follow as a MOOC on the [fast.ai](http://) website. One of the things he said and remained with me. He said: 'Start a blog about the things you learn even if you think you are not quite there yet, it doesnt matter. It will be of great help to understand the study material better, and it is a great exercise.'
So this is one thing which motivated me to start a blog and not just have a prifile page. I gave myselt three days time to get this blog started. Started last Friday morning and by Friday midday I already spent two hours looking at different fonts. It means it took me two hours max to get the template uploaded and working! It is so fast to get going and I will explain how in this tutorial.
I am working on a macBook with High Sierra and I use a terminal. Windows users might need a different approach or they can try to download [git bash](https://gitforwindows.org) for windows 

Why Jekyll? I wanted a blog which is customisable, and quick to get started. And Jekyll is free. It has also support for syntax highlighting which is great for coders and a number of other advantages, like supporting markdown which I love. It is such a perfect markup language for writing on the web.
oh, another inspiration for this blog has been [daring fireball](http://), he invented markdown by the way... but lets get started! 

### step 1

You need to create an account with GitHub. Git is one essential tool for developers so if you dont have an account yet head over to [GitHub](http://) com and create an account.

step 2

Create an empty repository with the same name as your github profile handle.
ex, if .. then.. 
keep it on master. clone or download the repo to your mac or pc. It will be empty but with a hidden file .git which is the file keeping track of your versions.

step 3

Github natively support the [Jekyll](http://jekyllrb.com) plattform and will host one static website for you at no cost. Jekyll has templates and themes you can choose at ...

so you clone or download the theme to your computer. you copy all the files minus the .git hidden file to your previously downloaded repo.
if you cannot see the file do Shift - nn- jj

step 4
now it is the time to push the changes to your github account.
..
..
..
Go to your page and check the result. You should see the template with the default

step 5
troubleshoot. I choose the Hyde and Poole [Hyde and Poole](http://) theme because frankly I wanted something like the fastai website, and if this is good for them it will be good for me too.

This theme is already a few years old and doesnt work out of the box. No worries, only a few changes were necessary.
I will list them here. 
First edit your yml file and replace this with rouge. then delete or comment out the line with (to comment it our set a '#' at the beginning of the line )
then eventually you will notice that the the landing page works but the about me has no styling. you need to edit the CSS file and the head file as follows:



..

step 6
push the changes done locally on your github account. for this 
open your terminal and :


step 7 
check that the links are working. Look at the folders posts.
The Jekyll pages are auto generated from those files. There is a certain format you need to keep. The title has to start with the date, followed by the name like this:
2012-02-06-whats-jekyll.md
md is the markdown extension. You can read more about markdown here, but it is really easy to get started.
I would start to duplicate the file with command-d (on a mac) and edit it. You can use your favourite editor or use brackets [Brackets](http://jekyllrb.com), which is free. The first few lines enclosed in '---' have to be present. Especially 'layout: post', and change the title of course.

push the changes and see your first post on your new website!!


step 8 
This theme is customisable however the optional color schemes as described in the documentation  did not work for me. I think it is best to modify the CSS and add some HTML in the template. Fonts can be modified easily for instance I changed the font of the main title and the blog to the system fonts.  

step 9
Optional. You can set up a development environment for Jekyll on your computer. The necessary files and downloads are on their website, however expect to spend topo much time debugging various issues and bugs. I prefer to edit my post and push them to github an see the results there. 

step 10 a hint.
keep the draft of the post in the same folder, just add unpublished to the header above as follows:

..

they will be unvisible then.

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

Hyde is developed on and hosted with GitHub. Head to the <a href="https://github.com/poole/hyde">GitHub repository</a> for downloads, bug reports, and features requests.

Thanks!
