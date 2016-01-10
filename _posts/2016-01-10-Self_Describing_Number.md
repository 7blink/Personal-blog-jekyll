---
layout: post
title:  "Self Describing Number"
date:   2016-01-10 7:52:00
categories: python
permalink: Number_Riddle
published: true
tags:
- python
comments: true
---

Recently, there was a new riddle posted to youtube on the Singing Banana (the guy from Numberphile) channel.  The riddle was to find a self describing number.  That is to say, find a number where the first digit tells how many zeros there are in the number.  The second digit tells how many ones are in the number.  The third tells how many threes there are.  And so on and so on.  For a better description, check out the original video at https://www.youtube.com/watch?v=K6Qc4oK_HqY

There are a couple of ways to solve this problem.  The most obvious way is to use mathmatical deductions.  Pretty much, I started with 9000000000 and then slowly made corrections until I got the right number.  It looked like this:

{% highlight sh %}
{% raw  %}
9000000000
9000000001
8100000010
7200000100
7210000100
6210001000
{% endraw %}
{% endhighlight %}

To get the ultimate solution of 6210001000.  That is one solution, but could there be others?  There is a way of using a mathmatical proof to prove there are no others, but I wasn't able to get that far.

Instead, I decided to create a computer program to check all 10 billion possible numbers.  That seemed like the best idea to get the most complete solution.  

For the mathatical proof, and the most effient program, check out the solution video at https://www.youtube.com/watch?v=1GKfEDvhWdY

and for my python script, the code is:
*note, code will take about 2 days to run*

{% highlight python %}
{% raw  %}
import time
start = time.time()
def compute():
    min = 1000000000
    max = 10000000000
    #Starting with a 1 in the "zeros" count because if it was lower then it would be zero, which would make the zero's count 1.
    for i in range(7000000000, 10000000000):
        number = i
        number_string = str(number)
        count = 0
        success = True
        for place in range(0,10):
            count = 0
            for digit in number_string:
                if str(place) == digit:
                    count += 1
            if number_string[place] == str(count):
                continue
            else:
                success = False
        if success == True:
            print("Number Found")
            print(number)

if __name__ == "__main__":
    compute()
    elapsed = time.time() - start
    print ("%d seconds" % (elapsed))
{% endraw %}
{% endhighlight %}


For the github, check out https://github.com/7blink/ProjectEuler/blob/master/Riddle01.py
