---
layout: post
title:  "First steps to become an iOS developer"
date:   2010-04-09
categories: iOS, developer
comments: true
published: true
---

next is 
https://wiki.genexus.com/commwiki/servlet/wiki?34616,HowTo%3A+Create+an+.ipa+file+from+XCode

this one is 
https://medium.com/@abhimuralidharan/what-is-a-provisioning-profile-in-ios-77987a7c54c2
<div class="message">
"Stop thinking about art works as objects, and start thinking about them as triggers for experiences" 
<br><cite>Brian Eno</cite>
</div>

![image](/assets/img/idalab-meetup.jpg)

### Creating a free Apple ID for Xcode

If you are starting out developing your apps, trying out a few things and you are not yet ready to commit to the fee of 99 USD a year for an Apple developer account, then you need only to create an Apple ID to activate Xcode and create a provisioning profile to run your apps on your devices.



#### Adding your Apple ID to Xcode

Before we can build to a device, we need to set up an Apple ID and add it to Xcode.

If you don’t yet have an Apple ID, obtain one from the [Apple ID site](http://appleid.apple.com/).

Once you have obtained an Apple ID, you must add it to Xcode.

Use Accounts preferences in Xcode to add your Apple ID, remote source code repositories, and Xcode Servers and to manage your developer account signing assets.
To open Accounts preferences, choose Xcode > Preferences and click Accounts.

![image](/assets/img/ap_accounts_preferences.png)


From the menu bar at the top of the screen choose Xcode > Preferences. This will open the Preferences window.
Choose Accounts at the top of the window to display information about the Apple IDs that have been added to Xcode.
To add your Apple ID, click the plus sign at the bottom left corner and choose Add Apple ID.

### What is a provisioning profile in iOS?

You can’t install any app on an iOS device. It has to be signed by Apple first. However, when you’re developing an app, you probably want to test it before sending it to Apple for approval. Provisioning profile act as a link between the device and the developer account. During development, you choose which devices can run your app and which app services your app can access. A provisioning profile is downloaded from your developer account and embedded in the app bundle, and the entire bundle is code-signed. A Development Provisioning Profile must be installed on each device on which you wish to run your application code. If the information in the provisioning profile doesn’t match certain criteria, your app won’t launch.

### Code signing in iOS

###


### UDID

https://medium.com/@abhimuralidharan/what-is-a-provisioning-profile-in-ios-77987a7c54c2

https://www.innerfence.com/howto/find-iphone-unique-device-identifier-udid
Finding Your iPhone’s Unique Identifier (UDID)

Developers, want to link to this page? No problem! Customize it …
What is the UDID?

Each iPhone or iPod Touch has a Unique Device Identifier (UDID), which is a sequence of 40 letters and numbers that is specific to your device. It’s like a serial number but much harder to guess. It will look something like this: 2b6f0cc904d137be2e1730235f5664094b831186.

Why do we need the UDID?

Your iPhone can only install programs that are approved by Apple. Applications in the App Store have been approved by Apple for general distribution, but beta customers get to try the app before it’s in the store. We register your UDID with Apple so they can approve our application especially for your iPhone.

How do I get my UDID?

To get your UDID, you have to plug your phone into a computer and copy it out of iTunes.

Copy/Paste from iTunes

Apple updates their UI pretty often, so the screenshots may not match up exactly, but the core idea here of going to the device page and clicking on the serial number remains the same.

Launch iTunes and connect your iPhone.
In the right pane, locate the information about your iPhone, including its name, capacity, software version, serial number, and phone number.

### Sources:

[](https://help.apple.com/xcode/mac/current/#/devc6700ab7d)

<hr>
