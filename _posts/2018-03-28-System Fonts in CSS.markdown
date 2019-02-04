---
layout: post
title:  "System Fonts in CSS"
date:   2018-03-28 10:41:47 +0100
categories: fonts
---

There has been a new font-family in the works for the last 3 years and recently this has included in the CSS Font Module and made official.
This has been pointed out today in Daring Fireball with a link to [this great post](https://furbo.org/2018/03/28/system-fonts-in-css/) by Craig Hockenberry .

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
Let's see what we have inside.
    
Looking at the source code:

    <!DOCTYPE html>
    <head>
    	<title>System Font Test</title>
    	<style>
    		body {
    			font-size: 2em;
    		}
    		
    		h1 {
    			font-family: "Gill Sans", sans-serif;
    			font-weight: 700;
    			font-size: 1.5em;
    			margin: 20px 10px;
    		}
    		
    		p {
    			font-family: "Gill Sans", sans-serif;
    			font-weight: 100;
    		}
    		p.sample {
    			font-weight: 800;
    			margin: 20px 0;
    			padding: 5px;
    		}
    		
    		p.sample span {
    			display: block;
    			width: 100%;
    			text-align: right;
       			border-bottom: 2px solid #ddd;		
    			font-weight: 600;
    			font-size: 0.75em;
    			padding: 2px 5px;
    			box-sizing: border-box;
    			color: #aaa;
    		}
    		
    		/*
    		The CSS WG recommendation: 
    		https://drafts.csswg.org/css-fonts-4/#system-ui-def
    		There is already wide support for this font-family: 
    		https://caniuse.com/#search=system-ui
    		*/
    		p.systemui {
    			font-family: system-ui;
    			color: red;
    		}
    		
    		/*
    		The following are font-families for specific platforms. 
    		They can be used for older browsers or ones that haven't 
    		been updated to use system-ui.
    		*/
    		p.applesystem { /* San Francisco in older Safari on iOS and macOS */
    			font-family: -apple-system;
    			color: orange;
    		}
    		p.blinkmacsystem { /* San Francisco in older Chrome on macOS */
    			font-family: BlinkMacSystemFont;
    			color: gold;
    		}
    		p.windows { /* Windows & Windows Mobile */
    			font-family: "Segoe UI";
    			color: limegreen;
    		}
    		p.android { /* Android & Chrome OS, older versions of Android */
    			font-family: "Roboto", "Droid Sans";
    			color: mediumblue;
    		}
    		p.linux { /* KDE, Ubuntu, GNOME, Firefox OS */
    			font-family: "Oxygen", "Ubuntu", "Cantarell", "Fira Sans";
    			color: darkviolet;
    		}
    		
    		/*
    		Combining all of the above gets you a font-family that 
    		works across all platforms and devices.
    		For more information see Marcin Wichary's article for 
    		Smashing Magazine:
    		https://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide
    		*/
    		p.combined {
    			font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
    			color: black;
    		}
    		
    		p.note {
    			color: #aaa;
    			font-size: 0.75em;
    			margin: 20px 10px;
    		}
    
    	</style>
    </head>
    <body>
    	<h1>System Fonts in CSS</h1>
    
    	<p class="sample systemui"><span>system-ui</span> The quick brown fox jumps over the lazy dog</p>
    	<p class="sample applesystem"><span>Safari on iOS & macOS</span>The quick brown fox jumps over the lazy dog</p>
    	<p class="sample blinkmacsystem"><span>Chrome on macOS</span>The quick brown fox jumps over the lazy dog</p>
    	<p class="sample windows"><span>Windows</span>The quick brown fox jumps over the lazy dog</p>
    	<p class="sample android"><span>Android</span>The quick brown fox jumps over the lazy dog</p>
    	<p class="sample linux"><span>Linux</span>The quick brown fox jumps over the lazy dog</p>
    
    	<p class="sample combined"><span>All Platforms</span>The quick brown fox jumps over the lazy dog</p>
    	
    	<p class="note">View this page's source to see the <code>font-family</code> for each sample.</p></body>
    

### What about macOS?
The last three versions of Mac OS X use three different system UI fonts: 
* Lucida Grande on Mac OS 10.9 (Mavericks); 
* A special version of Neue Helvetica on Mac OS 10.10 (Yosemite); 
* A special version of San Francisco on Mac OS 10.11 (El Capitan).
 
 
