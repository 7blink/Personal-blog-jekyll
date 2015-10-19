---
layout: post
title:  "Linux Shutdown Command"
date:   2015-09-22 19:18:00
categories: Shell
permalink: Linux_Shutdown
published: true
tags:
- shell
- bash
- command line
- Linux
- update
---

{% highlight sh %}
Begining Shutdown Process
Updating the system
System will shutdown in 1 minute
{% endhighlight %}
Which is better, Windows or Linux?  I know it seems like a troll question, but each operating system has it's benefits.  One of my favorite features on Windows is it's automatic update during shutdown.

There is something so effortless about it.  You are in Windows and you click shutdown.  Then up pops the automatic update.  Ussually I just turn off the monitor and leave it.  When it is done, the computer will turn itself off.  It wasn't always like that though.  

I remember when automatic updates first started on Windows.  Back then, it would start the automatic update about 5 minutes after you turned on your computer.  I would always wonder why my computer would suddenly get slow for a few minutes.  Then I figured out how to turn off automatic updates to prevent the sudden slow downs.  It wasn't until the moved the automatic updates to the shutdown process that I started using it again.

Now that I am on Linux, I think back about how simple it should be.  On Linux, you are expected to manually update your computer on a regular basis to maintain a secure system.  But wouldn't it be so much simpler if the computer automatically updated on shutdown?  That is what I thought, so I made a simple shell script that will update the system and then shut it down.

{% highlight sh %}
#!/bin/bash

echo "Begining Shutdown Process"
echo "Updating the system"
sudo sh -c "apt-get update && apt-get upgrade -y && shutdown -h 1"
{% endhighlight %}

Get the code on github [https://github.com/7blink/shutdown](https://github.com/7blink/shutdown)

As you can see, it will just simply run update, the upgrade (with -y to force yes for all prompts), and then shutdown.  You can save this into a .sh file and keep it on your desktop.  

Make sure to add execution privileges
{% highlight sh %}
chmod +x "filename"
{% endhighlight %}

Then when you are ready to shutdown, just click on the file, click on run in terminal, type your root password, and it will install all the updates and then shutdown the computer when it is done.
