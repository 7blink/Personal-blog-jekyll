---
layout: post
title:  "Jekyll Feedback"
date:   2015-11-11 19:18:00
categories: html
permalink: Jekyll_Feedback
published: true
tags:
- html
- jekyll
comments: true
---
I am really excited about launching my completed Jekyll theme soon.  It is now complete, but I wanted to create an intro to show everything that it can do.  Once of the features that I wanted to add was a Feedback form.  This is a neat feature to have in a static website because it allows you to have the two way conversation that you would otherwise find in a dynamic website.  This could be used as a custom order form, a survey, or just a simple feedback form.  
Lets take a look in more detail.

<br>So the first thing is to have a google account.  Specifically, we will be using google drive.  Once you have that check out:
<br>http://www.google.com/forms/about/

Click on Create Form and it should pop up with a wysiwyg editor in a basic template.  You can change, add, or delete whatever you like.

When you are done, click on "Send Form." You can use this link if you wanted to email out a survey, but we want to embed the form.  So after clicking on send, click on embed.  That should give you some code that looks like:
{% highlight html %}
{% raw  %}
<iframe
  src="https://docs.google.com/forms/d/15nEuMOTohKk4QCsQDxct10s6f7pnledoJh8eFHfVf8I/viewform?embedded=true"
  width="760" height="800"
  frameborder="0" marginheight="0"
  marginwidth="0">Loading...
</iframe>
{% endraw %}
{% endhighlight %}

It should also give you options to set the height and width.  If it doesn't, you can just manually change the code where it says:
{% highlight html %}
  width="760" height="800"
{% endhighlight %}
You can just change that to whatever you want, but make sure the width is less than the content-width in your main.scss file.  Also, make sure it is large enough to load the entire form.  If the iframe isn't big enough, then your users will have to scroll through the iframe and that might be an inconvenience.

So now you just need to know how to load the information in a useful way.  Google forms default option is to display each response individually.  That is good, but we can do better.  So while still in the form, click on "Responses" on the menu bar.  Then click on "Change Response Destination."  This should give you a pop up to create a Google Drive spreadsheet.  Once this is complete, your form submissions will be displayed in the spreadsheet for easy viewing or analysis.



If you liked that, please leave me some feedback and if you want to, you can check out the code at https://github.com/7blink/7blink-theme
