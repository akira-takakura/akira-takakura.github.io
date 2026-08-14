---
permalink: /
title: "プロフィール"
author_profile: true
lang: ja
ref: about
---

慶應義塾大学 [野崎研究室](https://nozaki-lab.jp/) 修士課程に在籍しています。

2026年春からのPhD進学先を探しています。


## お知らせ

<ul>
  {% assign lang_posts = site.posts | where: "lang", page.lang %}
  {% for post in lang_posts limit:5 %}
    <li>
      <span>{{ post.date | date: "%Y-%m-%d" }}</span>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
