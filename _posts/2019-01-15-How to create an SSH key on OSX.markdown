---
layout: post
title:  "How to create an SSH key to connect to a remote server"
date:   2019-01-15 10:41:47 +0100
categories: OSX, Linux, SSH
---
<div class="message">
Once you set up a shell user and try to log in via SSH, you'll find you must enter your password each time. If you’d like to avoid entering your password every time, you can set up Passwordless Login. This way, you'll be able to automatically login each time immediately without needing to enter your password. 
</div>

On your mac open the Terminal. 


{% highlight bash %}
$ cd ~/.ssh/              #Go to your local ssh folder (hidden)
$ sudo ssh-keygen -t rsa  #generate a RSA private/public key pair

#then enter the name of the file in which you wish to save the key and
#enter a password for the key
{% endhighlight %}

## Copy the key to the server using ssh-copy-id
Copy the public key on your local computer to the server by running the following command on your Linux machine.

{% highlight bash %}
$ cat ~/.ssh/ubuntu.pub | ssh ubuntu@10.101.21.202 "cat >> ~/.ssh/authorized_keys"
{% endhighlight %}

## Check the connection 
Enter this line in terminal for a passwordless login
{% highlight bash %}
ssh ubuntu@10.101.21.202 
{% endhighlight %}

## Confirm the identity being used

You can confirm the identity (private key) you're using if you add the -v flag vor verbose.
{% highlight bash %}
ssh -v ubuntu@10.101.21.202 
{% endhighlight %}

## Finally there is another shortcut

If the Linux server on our network has a known static IP which is not changing, we can edit the SSH config file in `~/.ssh/config` 
First I open the file in my editor:
{% highlight bash %}
nano ~/.ssh/config
{% endhighlight %}
then I add the following:
{% highlight bash %}
Host ub     # this is the alias for my password less login
Hostname 10.101.21.24   # The static IP of the server 
user ubuntu      # username as would I use loggin in 
{% endhighlight %}
Now lets login again but this time it is even quicker using the alias we inserted in the config file:
{% highlight bash %}
ssh ub
{% endhighlight %}
