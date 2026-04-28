---
layout: page
title: News
---

<ul class="news-list">
  {% for item in site.data.news %}
    <li class="news-item">
      <span class="news-date">{{ item.date }}</span>
      <span class="news-text">{{ item.text }}</span>
    </li>
  {% endfor %}
</ul>
