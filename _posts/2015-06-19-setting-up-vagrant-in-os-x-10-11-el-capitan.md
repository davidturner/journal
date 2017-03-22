---
layout: post
title:  "Setting Up Vagrant in OS X 10.11 El Capitan"
date:   "2015-06-19 20:45"
categories: posts
author: David Turner
twitter:
---
With Apple having made OS X 10.11’s first Developer Preview available to developers, and my addiction to using new and shiny things, I’ve just finished setting up a new partition using the Developer Preview. Getting it set up was pretty simple. With the exception of Vagrant.

## OS X Security - Rootless

Apple’s rolled out a few new security features to try and limit the damage that malicious code can do to the operating system. Part of this includes locking down the ability to access/edit certain folders. One of those folders seems to be `/usr/bin`, one of several folders that Terminal programs include in their `$PATH` for use by us as users. Vagrant’s installer currently symlinks a a reference to their vagrant command in this folder and, in 10.11… that no longer works. Everything gets installed, but the command itself isn’t made available to the terminal because the symlink silently fails to be created.

Fortunately, it’s not a terribly difficult thing to work around, once you know what’s going on. The folder `/usr/local/bin` _isn’t_ restricted in the same way as `/usr/bin` and it’s another folder that should be included in your `$PATH`. The relevant command we want is installed into the `/opt/vagrant/bin/` folder. We can use the following command to create a symlink for the vagrant command:

```
ln -s /opt/vagrant/bin/vagrant /usr/local/bin/vagrant
```

A quick restart of terminal and voila, Vagrant should be working once more!