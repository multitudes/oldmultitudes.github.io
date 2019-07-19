---
layout: post
title:  "Installing a web server on Mojave for iOS development and testing"
date:   2019-06-14
categories: iOS, developer
comments: true
published: true
---

I did some tutorials about web API's, JSON decoding and URL sessions. I wanted to be able to test my app to be able to access JSON data on a local server.  
On my local network I will have access to videos for streaming, pictures and JSON files returning data.  

There are a few options to do this. 

# PHP built in server

PHP is shipped with macOS by default.
The easiest way to create a webserver on your machine for development, not for production(!),  is to create a folder with some files, open terminal, navigate to the folder and do
``` bash
cd ~/myWebFolder
php -S localhost:8000
```

Now open your browser and go to `localhost:8000`.  
You will see the files you have in the folder! Other devices on your local network will be able to see the same.
To access the folder you will just need to replace "localhost" with the IP address of your mac.
To see the IP address Option click on your wifi icon in the top right menu bar!

[https://www.php.net/manual/en/features.commandline.webserver.php](https://www.php.net/manual/en/features.commandline.webserver.php)  

<hr>

# Using the preinstalled Apache on Mojave

Apple released the macOS Mojave 10.14 on 24th September 2018 and it includes Apache and PHP pre-installed.   
This is maybe the easiest solution to get up and running quickly and painlessly. 
I discovered that Xampp can be sometimes a bit temperamental and if something does not work straight away then it takes a long time to get it right.
Apache is already preinstalled on Mojave. You only need to activate it!

First of all check the version of Apache in Terminal

```
httpd -v
```

The commands to start and stop Apache are:
```
sudo apachectl start
# to stop
sudo apachectl stop
# to restart
sudo apachectl restart
```
After starting Apache server go ahead and test it by opening a browser like Safari or Chrome and visit [http://localhost](http://localhost).
You will be greeted by a "It works!" message
On other computer on your local network you will access this folder with the ip address of your mac where apache is running.

In case you don't get to see the above output then run the following command to check the error.
```
sudo apachectl configtest
```

#### Document Root

This is the location in the computer file system from where the files are accessed when we visit the localhost in a browser.
Document Root is a directory where we put our website files.

On Mac we have two document root folders. One is at the system level and the other is at the user level.

The system level document root in macOS Mojave is located in the following directory: `/Library/WebServer/Documents/`
but it is not recommended to use it because it requires extra privileges. Better to install and use the other one at the user level.   
We create a directory called Sites in the user directory.


#### create a new Sites folder

in Terminal I will do 
```
# to switch to the user home directory.
cd 

# create dir
mkdir Sites

#this will open a new finder window
open . Sites

```
Create and edit a php file as
```
<?php
print("hello world");
?>
```
Go again to the localhost on your computer or look up the ip address of your mac (tip alt-click on the wifi icon on your mac), and use this on your mobile devices or other mac on the network. Using VPN is also no problem, the devices recognize them themselves even in different VPN countries :)
I dont know you but when it works it is a really nice feeling!

#### Creating username.conf file 
in Terminal check your username with `whoami`, then create a new conf file like this

```
whoami

cd /etc/apache2/users/

#replace myusername with the system answer to whoami
sudo touch myusername.conf

```
Edit that conf file with :
```
<Directory "/Users/YOUR_USER_NAME/Sites/">
AllowOverride All
Options Indexes MultiViews FollowSymLinks
Require all granted
</Directory>
```
I used nano with sudo to get the permission to write to the file. Using sudo will ask for your password.
Permission for the files are 644 or `-rw-r--r--   1 root  wheel`.
You can check doing `ls -al` in terminal



#### Configuring the httpd.conf file

Go to the apache2 folder:
`cd /etc/apache2/`

Make a backup of the httpd file with 
`sudo cp httpd.conf httpd.conf.backup`

Uncomment the following lines
```
LoadModule userdir_module libexec/apache2/mod_userdir.so
LoadModule include_module libexec/apache2/mod_include.so
LoadModule rewrite_module libexec/apache2/mod_rewrite.so

# Uncomment the following line for User home directories.
Include /private/etc/apache2/extra/httpd-userdir.conf

# now the document root
# omment out the older ones and add 
DocumentRoot "/Users/YOUR_USERNAME/Sites/"
<Directory "/Users/YOUR_USERNAME/Sites/">

# set the AllowOverride None to AllowOverride All

```

#### Configuring the httpd-userdir.conf file

Go to `cd /etc/apache2/extra/`

do a back up : `sudo cp httpd-userdir.conf httpd-userdir.conf.backup`
OPen the file `httpd-userdir.conf`
Uncomment : `Include /private/etc/apache2/users/*.conf`

Test in Terminal and ready!
`sudo apachectl configtest`

now going to the localhost will show nothing. We did not add anything yet!

#### PHP in Mojave

Check the version with `php -v`
go to ` cd /etc/apache2/`
edit the config file httpd.conf:  
`nano sudo nano httpd.conf`  
Then uncomment the `LoadModule php7_module libexec/apache2/libphp7.so` to use php 7.  


<hr>

# Using Xampp

I had installed on my machine and did not use it for a while. I could not start it again and I had this error message which is probably telling me something important but since I did not have any project installed at this time, I decided to reinstall the application and have a fresh start.

I drag the XAMPP folder in Application directory to the trash.
I do a search on my drive for other files.
```
sudo -s
[ Type your password ]
find / | grep -i xampp
```
and found some in `~/.bitnami/stackman/machines/xampp/`. I deleted the xampp directory in terminal

```
cd ..
rm -R xampp
```
The new version would have a uninstall script however this worked for me

#### Downloading XAMPP

Go to the [apachefriends.org](https://www.apachefriends.org/download.html) website and download the latest version 64 bit for mac os. I took the version 7.3.7 with PHP 7.3.7.
XAMPP for OS X is a native installer for OS X. It installs Apache, PHP and other XAMPP components directly on your OS X system, in the /Applications/XAMPP folder. It ships MariaDB instead of MySQL. The commands and tools are the same for both.

Install the app as usual and start in the control panel

![image](/assets/img/InstallingWebServer/1.png)

After a few seconds you will see the IP address of the server on the panel.

To test everything works type in the IP address in a web browser and you will see the dashboard :

![image](/assets/img/InstallingWebServer/2.png)

And under network enable port forwarding (port 80 of the stack to port 8080 of the host system) over SSH.

![image](/assets/img/InstallingWebServer/3.png)

then you will be able to type 
http://localhost:8080
and see the same welcome page

#### About Apache

Apache HTTP Server colloquially called Apache was named after a Native American Tribe Apache to respect its superior skills in warfare strategy. Build on C/C++ and XML it is cross-platform web server
Most commonly used on UNIX, Apache is available for wide variety of platforms including FreeBSD, Linux, Windows, Mac OS, Novel Netware etc. In 2009, Apache became the first server to serve more than 100 million websites.

#### Accessing the document root on the server

Mount the /opt/lampp directory from the "Volumes" tab of the stack manager and click the "Explore" button to open the file manager.
Particularly of interest for a quick start is the htdocs which stands for “HyperTextDocuments”.  
htdocs or www is the directory that the Apache web server looks for files to serve on your domain by default. This location can be changed to whatever value you want. All you have to do is point the Document Root to a different folder in your .conf file.

![image](/assets/img/InstallingWebServer/4.png)

Other important files: the htaccess. 
`htaccess` (or hypertext access) are the files that provide options for website owners to control the server environment variables and other parameters to enhance functionality of their websites. These files can reside in any and every directory in the directory tree of the website and provide features to the directory and the files and folders inside it.

![image](/assets/img/InstallingWebServer/5.png)

#### Creating a new folder in htdocs

When the server starts, it will look for the index.php file in the htdocs folder.
This file looks currently like this:
```
<?php
	if (!empty($_SERVER['HTTPS']) && ('on' == $_SERVER['HTTPS'])) {
		$uri = 'https://';
	} else {
		$uri = 'http://';
	}
	$uri .= $_SERVER['HTTP_HOST'];
	header('Location: '.$uri.'/dashboard/');
	exit;
?>
Something is wrong with the XAMPP installation :-(
```

`$_SERVER` is one of the superglobal variables in PHP which is used to access global variables from anywhere in the PHP script (also from within functions or methods).

In this case on the first line 'HTTPS' is set to a non-empty value if the script was queried through the HTTPS protocol, otherwise if empty it means the website has been queried through HTTP protocol.
If I input on the browser my server IP with `https://192.168.64.3` then the valus of ```$_SERVER['HTTPS']``` will be not NULL and `on`.
The value of the superglobal `$_SERVER['HTTP_HOST']` will be in this case `192.168.64.3`  
This line will add the two together: 
`$uri .= $_SERVER['HTTP_HOST'];`
so the `uri` will now be `https://192.168.64.3`
and then the query will be redirected to the dashboard folder and the system will again look for the index.php file there and output the dashboard page in the browser. The url will be:
`https://192.168.64.3/dashboard` or `http://192.168.64.3/dashboard` dependng of the original query.

So what I did now is changing the folder name in this line
`header('Location: '.$uri.'/myJSONfolder/');`  
and my server will be reached for testing at `http://192.168.64.3/myJSONfolder/` on my local network

in this new folder I create a new index.php file and put the following in my index.php.
```
print("hello world");
```
now going to `http://192.168.64.3/myJSONfolder/` will  output the 'hello world' line!

Of course I will use this address to output my json files later on and start developing on my machine


<hr>


