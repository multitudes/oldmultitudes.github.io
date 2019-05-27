---
layout: post
title:  "Customize your macOs Terminal with iTerm, ZSH and Prezto"
date:   2019-05-23
categories: iOS, developer
comments: true
published: false
---


<div class="message">
"" 
<br><cite></cite>
</div>

<a rel="ar" href="/assets/img/AR-QL-Pictures/retrotv.usdz">
    <img src="/assets/img/AR-QL-Pictures/Screenshot5.jpg">
</a>

### iTerm

You can install iTerm2 from their website, or if you have homebrew and cask installed you can install it this way too:

brew cask install iterm2

### Adopt ZSH
ZSH adds a ton of sophistication while still being wholly compatible with the world of BASH

To easily switch OSX you simply need to:
Go to System Preferences
Go to Users and Groups
Unlock via the lock icon
Right-click (or dual-click) on your user and go to ‘Advanced Options’
Change your shell from /bin/bash to /bin/zsh

(Note: Many people also install a more maintained version of ZSH from homebrew - I’ve never needed my zsh to be overly current, but your mileage may vary.)
Once you do this your default and iterm terminals will open new tabs in ZSH instead of BASH. Now you need to care about .zprofile and .zshrc instead of .bash_profile and .bashrc.

### Installing Prezto

See the GitHub repo to install Prezto:
[https://github.com/sorin-ionescu/prezto](https://github.com/sorin-ionescu/prezto)


### Sources:

[Download iTerm - www.iterm2.com](https://www.iterm2.com)
[Customize iTerm - github repo](https://github.com/mbadolato/iTerm2-Color-Schemes)
[blog](https://realjenius.com/2017/08/28/prezto/)
<hr>

[^1]: 