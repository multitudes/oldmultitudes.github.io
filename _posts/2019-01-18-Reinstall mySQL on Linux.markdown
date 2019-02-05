---
layout: post
title:  "Reinstall mySQL on Linux"
date:   2019-01-18 10:41:47 +0100
categories: OSX, Linux, mySQL
---

First, remove MySQL:

{% highlight bash %}
sudo apt purge mysql-server mysql-client mysql-common
sudo apt autoremove
sudo rm -rf /var/lib/mysql*
{% endhighlight %}

{% highlight bash %}
sudo apt update
sudo apt install mysql-server
sudo mysql_secure_installation  # this will make your mySQL more secure

# On the Linux server 
sudo mysql  #login as root
# when the root is login as "auth_socket" then need to use sudo login
mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;

# I can change that if I want to login as root with a password
# to login as user need to grant user privileges. change user and password
mysql>CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
mysql>GRANT ALL PRIVILEGES ON *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
# exit the MySQL shell:
mysql> exit

{% endhighlight %}

testing mySQL:

{% highlight bash %}
systemctl status mysql.service
{% endhighlight %}

If MySQL isn't running, you can start it with 
{% highlight bash %}
sudo systemctl start mysql
{% endhighlight %}

You can try connecting to the database using the mysqladmin tool, which is a client that lets you run administrative commands.
{% highlight bash %}
sudo mysqladmin -p -u root version
{% endhighlight %}

