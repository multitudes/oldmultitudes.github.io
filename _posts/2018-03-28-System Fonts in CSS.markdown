---
layout: post
title:  "System Fonts in CSS"
date:   2018-03-28 10:41:47 +0100
categories: fonts
---

There has been a new font-family in the works for the last 3 years and recently this has included in the CSS Font Module and made official.
This has been pointed out today in Daring Fireball with a link to [this great post](https://furbo.org/2018/03/28/system-fonts-in-css/) by Craig Hockenberry.

System UI fonts have zero latency and are a great alternative for websites.
San Francisco is the new Apple system font since El Capitan.
Google has been developing the Roboto font with great success. 
Erik Spiekermann created Fira Sans for Mozilla. 
Microsoft has been busy with a font named Segoe. 

To cover different browsers and older operating systems but this CSS should cover all eventualities:

    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
    "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans",
    "Droid Sans", "Helvetica Neue", sans-serif;
    
An explanation of the fonts above can be found [here](https://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/) 

* **-apple-system** targets San Francisco in Safari on Mac OS X and iOS, and it targets Neue Helvetica and Lucida Grande on older versions of Mac OS X. It properly selects between San Francisco Text and San Francisco Display depending on the text’s size.
* **BlinkMacSystemFont** is the equivalent for Chrome on Mac OS X.

The second grouping is for known system UI fonts:
* **Segoe** UI targets Windows and Windows Phone.
* **Roboto** targets Android and newer Chrome OS’. It is deliberately listed after Segoe UI so that if you’re an Android developer on Windows and have Roboto installed, Segoe UI will be used instead.
* **Oxygen** targets KDE, Ubuntu targets… well, you can guess, and Cantarell targets GNOME. This is beginning to feel futile because some Linux distributions have many of these fonts.
* **Fira Sans** targets Firefox OS.
* **Droid Sans** targets older versions of Android.

The third grouping is our fallback fonts:
* **Helvetica Neue** targets pre-El Capitan versions of Mac OS X. It is listed close to the end because it’s a popular font on other non-El Capitan computers.
* **sans-serif** is the default sans-serif fallback font.

Craig made a [page](http://furbo.org/stuff/systemfonts-new.html) which can be used for testing.


### What about macOS?
The last three versions of Mac OS X till El Capitan used three different system UI fonts: 
* Lucida Grande on Mac OS 10.9 (Mavericks); 
* A special version of Neue Helvetica on Mac OS 10.10 (Yosemite); 
* A special version of San Francisco on Mac OS 10.11 (El Capitan).
 
 
