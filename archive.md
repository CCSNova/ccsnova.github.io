---
layout: page
title: Archive
---

{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {%- for post in posts -%}
      {%- if post.tag = tag -%}
        <li><a href="{{ post.url }}">{{ post.title }} - {{ post.date | date: "%m/%d/%Y" }}</a></li>
      {%- endif -%}
    {%- endfor -%}
  </ul>
{% endfor %}