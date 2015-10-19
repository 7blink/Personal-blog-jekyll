---
layout: post
title:  "Test Post"
date:   2015-09-20 18:05:00
categories: Javascript
permalink: Test
published: false
---
![logo](/images/logo.png) You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

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
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
