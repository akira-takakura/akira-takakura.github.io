---
permalink: /
title: "プロフィール"
author_profile: true
lang: ja
ref: about
---

慶應義塾大学 [野崎研究室](https://nozaki-lab.jp/) 理工学研究科 総合デザイン工学専攻のPh.D.です。指導教員は野崎貴裕教授です。

現在、Carnegie Mellon Universityの[Zackory Erickson](https://zackory.com/)教授（[RCHI Lab](https://rchi-lab.github.io/)）のもとに滞在し、ロボットによる着衣支援（robot-assisted dressing）に関する研究を行っています。

学部時代には、慶應義塾大学理工学部システムデザイン工学科の大森浩充先生の下で研究を行っていました。大森先生の研究室では、MRACS、非線形適応最適制御系に対する制御と同定の両立問題に取り組んでいました。

研究興味は、適応制御、システム同定、ロボティクス、ハプティクスです。


## お知らせ

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
