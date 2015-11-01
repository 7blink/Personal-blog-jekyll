---
layout: post
title:  "Linux Desktop Icon"
date:   2015-11-02 19:18:00
categories: Shell
permalink: Linux_Desktop_Icon
published: true
tags:
- shell
- bash
- command line
- linux
- update
image: /images/2015Nov/Shutdown.png
---
A lot of you have liked my Linux update and shutdown script.  It is convenient to know that all you have to do is run the script, and Linux will update everything and then shutdown when it is finished.  It is very similar to Window's auto update feature.  But I have been getting asked how to make it into a desktop icon, or a start menu icon?  
Let's take a look...

In case you haven't seen the update and shutdown script, check it out at [Linux Shutdown](/Linux_Shutdown)

So now we want to add a Desktop icon for easy access.  Well, first we need an icon image.

I like this one:

![Shutdown.ico](/images/2015Nov/Shutdown.ico)

That I got from:

 http://www.iconarchive.com/show/windows-8-metro-icons-by-dakirby309/Other-Power-Restart-Metro-icon.html

You should totally got check out their site.  They have a ton of cool icons for everything.  In fact, the artist [dakirby309](http://dakirby309.deviantart.com/) didn't even make that icon for Linux, he made it for Windows Metro.  But I thought it was a cool icon and fit well into the Linux Mint color scheme, so I used it.  It is licensed under [CC Attribution-Noncommercial 4.0](https://creativecommons.org/licenses/by-nc/4.0/).

Now that we have the icon and the script we want to run, we just need to create a .desktop file.  So create a Shutdown.desktop file and then add this:
{% highlight sh %}
{% raw  %}
[Desktop Entry]
Name=Shutdown
Comment=Update and Shutdown
Exec=/home/{{user name}}/{{path to}}/Shutdown.sh
Terminal=true
Type=Application
Icon=/home/{{user name}}/{{path to}}/Shutdown.ico
{% endraw %}
{% endhighlight %}

Then replace the username and path with your information.

Make sure to add execution privileges
{% highlight sh %}
chmod +x "filename"
{% endhighlight %}

Then when you are ready to shutdown, just click on the file, type your root password, and it will install all the updates and then shutdown the computer when it is done.  You can walk away knowing that everything will happen automatically.

If you want to, you can check out the code at https://github.com/7blink/shutdown
