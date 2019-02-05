---
layout: post
title:  "How to create an SSH key on OSX"
date:   2019-01-15 10:41:47 +0100
categories: OSX, Linux, SSH
---


# How to create an SSH key on macOS High Sierra to use to connect to a remote server

Once you set up a shell user and try to log in via SSH, you'll find you must enter your password each time. If you’d like to avoid entering your password every time, you can set up Passwordless Login. This way, you'll be able to automatically login each time immediately without needing to enter your password. On your mac open the Terminal. 

{% highlight bash %}
$ cd ~/.ssh/              #Go to your local ssh folder (hidden)
$ sudo ssh-keygen -t rsa  #generate a RSA private/public key pair

#then enter the name of the file in which you wish to save the key and
#enter a password for the key
{% endhighlight %}

## Step 2 - copy the key to the server using ssh-copy-id
Copy the public key on your local computer to DreamHost's server by running the following command on your Linux machine.

{% highlight bash %}
$ ssh-copy-id -i ~/.ssh/ubuntu_rsa.pub ubuntu@10.21.201.203
{% endhighlight %}
