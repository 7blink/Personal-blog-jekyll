---
layout: post
title:  "Jekyll - Tags without plugins"
date:   2015-10-15 17:31:00
categories: HTML Javascript
permalink: Jekyll_tags
published: true
tags:
- jekyll
- tags
- html
- javascript
comments: true
---
I wanted to write a quick post to everyone about how to add tags to your jekyll blog.  A longer post will be coming as soon as the whole template is complete, but for now I will just give a quick explanation as to what Jekyll is.  In short, Jekyll is a blogging platform that creates static HTML files from simple Markdown text files.  Similar to other blogging platforms such as Wordpress, but different in that all the pages are static HTML instead of a dynamic PHP like Wordpress.  With static webpages, you don't need as powerful of a server to host your website.  In fact, some places will even host it for free up to a certain size limit.  Did you know that this blog is being hosted for free on github?  It is.  Checkitout at [github.com](https://github.com/7blink/blog)

I wrote a little javascript that will allow you to add tags to your webpage without having to use a plug in.  This is useful if you can't install a plug in (such as if you are using github to generate the pages) or if you just don't want to install another program on your computer (keep it simple).  

Most of the function happens on the tags page.  If you haven't already, create a tags.html page and then add:

{% highlight javascript %}
{% raw  %}


<script type="text/javascript">
// take the url #div and make that display visable
window.onload = function() {
  var url_arr = document.URL.split('#');
      page    = url_arr[url_arr.length - 1];
      console.log(page);
        document.getElementById(page).style.display="block";
}

// on click, switch that div between visiable and invisiable
function toggle_visibility(id) {
  var tags = document.getElementById('tags_options').children;
  var i = 1;
  for (i; i < tags.length; i++) {
    console.log(tags[i]);
    tags[i].style.display="none";
  }
   var tag = document.getElementById(id);
   if(tag.style.display == 'block')
      tag.style.display = 'none';
   else
      tag.style.display = 'block';
}
</script>

<!-- Create a list of all the tags and loop through one at a time -->
<div class="tags_page"><p>
{% capture tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign tag = tags | split:',' ' ' | sort %}
{% for item in (0..site.tags.size) %}{% unless forloop.last %}
{% capture word %}{{ tag[item] | strip_newlines  }}{% endcapture %}

<!-- For each tag, create a link with and add onclick. -->
<a href="#{{ word }}" onclick="toggle_visibility('{{ word }}');">{{ word }}</a>

{% endunless %}{% endfor %}
</p>
</div>
<hr id="line"> <br />
<div class="tags_page"><p>
  <div id="tags_options">
{% capture tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign tag = tags | split:',' ' ' | sort %}
{% for item in (0..site.tags.size) %}{% unless forloop.last %}
{% capture word %}{{ tag[item] | strip_newlines  }}{% endcapture %}

<!-- For each tag, create an invisiable div with each tag's posts.  Also add onclick toggle. -->
<div id="{{ word }}" style="display:none">
<ul>
{% for post in site.tags[word] %}{% if post.title != null %}
<li><span>{{ post.date | date: "%b %d" }}</span>» <a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
<hr id="line">
{% endif %}{% endfor %}
</ul>
</div>
{% endunless %}{% endfor %}
</div>
</p>
</div>
{% endraw %}
{% endhighlight %}

So to quickly go over it.  The first function takes the url and looks for a #div.  If it finds one, it will make that div visable.  The second function is an onclick that when the tag is clicked, it will make that tag's div visiable/invisiable.

The next two sections are jekyll code.  The first one takes all the tags and sorts them and then starts a for loop.  The for loop takes each tag and creates a link to that tags #div url.  It also adds the javascript onclick function to the link.  Then it creates an invisiable div that lists each post for that tag.  The div will become visiable if the tag's link is clicked or if the url has a #div for that div.

Almost done.  Now we just need to add something to the post's layout.  What we will add will simply be a link to the /tags/#div for the tag.  The link will take the user to the tags page with the #div in the url that the javascript will recognize and make that div visiable.

{% highlight javascript %}
{% raw %}
<br> <br>
<hr id="line">
<p>tags:
{% for tag in page.tags %}
    <a href="/tags/#{{ tag }}">{{ tag }}</a>
{% endfor %}
</p>
{% endraw %}
{% endhighlight %}
