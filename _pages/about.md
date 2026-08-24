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
