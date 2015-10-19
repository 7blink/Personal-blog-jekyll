---
layout: post
title:  "Hello World"
date:   2015-09-21 15:05:00
categories: Python HTML
permalink: Hello_World
published: true
tags:
- python
- intro
---
![logo](/images/logo.png) Hello and Welcome to my site.  I will be updating with my current projects in the next couple of days.  In the mean time, I have a quick python script for you.

It is a magic eight-ball program.  If you don't remember the magic eight-ball, it was a fortune teller toy where you would ask it a question and it will give you a prediction.  Check it out.

{% highlight python %}
import random
def compute():
    messages	=	['It	is	certain',
				'It is decidedly so',
				'Yes	definitely',
				'Reply	hazy	try	again',
				'Ask	again	later',
				'Concentrate	and	ask	again',
				'My	reply	is	no',
				'Outlook	not	so	good',
				'Very	doubtful']
    return (messages[random.randint(0, len(messages)-1)])


if __name__ == "__main__":
	print(compute())
#=> prints a random prediction to terminal.
{% endhighlight %}
