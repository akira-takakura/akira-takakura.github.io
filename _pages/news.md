---
layout: archive
title: "News Archive"
permalink: /news/
author_profile: true
lang: en
ref: news
---

{% assign lang_posts = site.posts | where: "lang", page.lang | sort: "date" | reverse %}
{% assign items_per_page = 5 %}
{% assign total_pages = lang_posts.size | minus: 1 | divided_by: items_per_page | plus: 1 %}

<div id="news-archive">
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
<nav class="pagination" id="news-pagination">
  <ul>
    {% for i in (1..total_pages) %}
    <li><a href="#" class="news-page-btn{% if i == 1 %} current{% endif %}" data-page="{{ i }}">{{ i }}</a></li>
    {% endfor %}
  </ul>
</nav>
{% endif %}

<script>
document.addEventListener('DOMContentLoaded', function () {
  var buttons = document.querySelectorAll('#news-pagination .news-page-btn');
  var pages = document.querySelectorAll('#news-archive .news-page');
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
