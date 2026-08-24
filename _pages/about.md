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

I am a Ph.D. student at [Nozaki Laboratory](https://nozaki-lab.jp/), Graduate School of Integrated Design Engineering, Keio University, advised by Prof. Takahiro Nozaki.

I am currently staying at Carnegie Mellon University under Prof. [Zackory Erickson](https://zackory.com/) ([RCHI Lab](https://rchi-lab.github.io/)), working on robot-assisted dressing.

As an undergraduate, I conducted research under Prof. Hiromitsu Omori in the Department of System Design Engineering, Faculty of Science and Technology, Keio University. In Prof. Omori's laboratory, I worked on MRACS (model reference adaptive control systems) and the problem of simultaneously achieving control and identification for nonlinear adaptive optimal control systems.

My research interests include adaptive control, system identification, robotics, and haptics.


## News

{% assign lang_posts = site.posts | where: "lang", page.lang | sort: "date" | reverse %}
{% assign items_per_page = 5 %}
{% assign total_pages = lang_posts.size | minus: 1 | divided_by: items_per_page | plus: 1 %}

<div id="home-news-archive">
{% for post in lang_posts %}
  {% assign idx0 = forloop.index0 %}
  {% assign in_page_pos = idx0 | modulo: items_per_page %}
  {% assign page_num = idx0 | divided_by: items_per_page | plus: 1 %}
  {% if in_page_pos == 0 %}
  <ul class="news-page" data-page="{{ page_num }}"{% unless page_num == 1 %} style="display:none;"{% endunless %}>
  {% endif %}
    <li>
      <span>{{ post.date | date: "%Y-%m-%d" }}</span>
      <span>{{ post.title }}</span>
    </li>
  {% assign next_idx = idx0 | plus: 1 %}
  {% assign next_in_page_pos = next_idx | modulo: items_per_page %}
  {% if forloop.last or next_in_page_pos == 0 %}
  </ul>
  {% endif %}
{% endfor %}
</div>

{% if total_pages > 1 %}
<nav class="pagination" id="home-news-pagination">
  <ul>
    {% for i in (1..total_pages) %}
    <li><a href="#" class="news-page-btn{% if i == 1 %} current{% endif %}" data-page="{{ i }}">{{ i }}</a></li>
    {% endfor %}
  </ul>
</nav>
{% endif %}

<script>
document.addEventListener('DOMContentLoaded', function () {
  var buttons = document.querySelectorAll('#home-news-pagination .news-page-btn');
  var pages = document.querySelectorAll('#home-news-archive .news-page');
  buttons.forEach(function (btn) {
    btn.addEventListener('click', function (e) {
      e.preventDefault();
      var target = btn.getAttribute('data-page');
      pages.forEach(function (p) {
        p.style.display = (p.getAttribute('data-page') === target) ? '' : 'none';
      });
      buttons.forEach(function (b) { b.classList.remove('current'); });
      btn.classList.add('current');
    });
  });
});
</script>
