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

<div id="home-news-archive">
  <ul class="news-list">
  {% for post in lang_posts %}
    <li><span class="news-date">{{ post.date | date: "%Y-%m-%d" }}</span><span class="news-body">{{ post.title }}</span></li>
  {% endfor %}
  </ul>
</div>

<style>
#home-news-archive {
  max-height: 22em;
  overflow-y: auto;
  border: 1px solid var(--global-border-color);
  border-radius: 6px;
  padding: 0.75em 1em;
}

#home-news-archive .news-list {
  list-style: none;
  margin: 0;
  padding: 0;
}

#home-news-archive .news-list li {
  display: flex;
  align-items: baseline;
  gap: 1em;
  padding: 0.35em 0;
}

#home-news-archive .news-list li + li {
  border-top: 1px solid var(--global-border-color);
}

#home-news-archive .news-date {
  flex: 0 0 6.5em;
  font-variant-numeric: tabular-nums;
  color: var(--global-text-color-light);
  font-size: 0.9em;
}

#home-news-archive .news-body {
  flex: 1 1 auto;
  min-width: 0;
}
</style>
