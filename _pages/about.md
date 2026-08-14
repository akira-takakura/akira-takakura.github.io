---
permalink: /
title: "About Me"
author_profile: true
lang: en
ref: about
redirect_from: 
  - /about/
  - /about.html
---

I’m a master’s student at [Nozaki Laboratory](https://nozaki-lab.jp/), Keio University.  

I am currently seeking a PhD position starting spring 2026. 


## News

<ul>
  {% assign lang_posts = site.posts | where: "lang", page.lang %}
  {% for post in lang_posts limit:5 %}
    <li>
      <span>{{ post.date | date: "%Y-%m-%d" }}</span>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

[View all news →]({{ "/news/" | relative_url }})
