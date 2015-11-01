---
layout: page
title: Store
permalink: /store/
---

{% if site.navbar.store == true %}

<div class="post">
  <ul class="post-list">
    {% for post in site.posts %}
    {% if post.store != Null %}
      <li>

        <h3>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h3>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y %H:%m" }}</span>

		<div class="content">
      {% if post.image %} <a href="{{ post.url | prepend: site.baseurl }}" style="text-decoration: none;"> <img src="{{post.image}}" {% if post.img-width %}style="width:{{post.img-width}}px" {% endif %}alt="{{ post.title }}"> </a>{% endif %}
      {% if post.yt %}<a href="{{ post.url | prepend: site.baseurl }}" style="text-decoration: none;"> <img src="https://i.ytimg.com/vi/{{ post.yt }}/hqdefault.jpg" {% if post.img-width %}style="width:{{post.img-width}}px" {% endif %}alt="{{ post.title }}"> </a><br>{% endif %}
      {% if post.gallery.size != 0 %}
        <div class="image-gallery">
          {% for item in post.gallery %}
            <img
                width="{{ post.gallery-width }}"
                onclick="this.width=this.naturalWidth"
                ondblclick="this.width={{ post.gallery-width }}"
                alt="RESIZE IMAGE"
                src="{{ item }}"
             />
          {% endfor %}
        </div>
        <div class="clear"></div>
      {% endif %}

		{{ post.excerpt }}
    <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">Read More</a>
    <br>
    <br>
    <hr id="line">
        </div>
		<br>
      </li>
      <br>
      {% endif %}
    {% endfor %}
  </ul>
</div>


{% endif %}
