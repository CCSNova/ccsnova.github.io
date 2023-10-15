---
layout: page
title: Archive
titletop: Archive
---

{% for tag in site.catagoreys %}
  <h3>{{ tag | escape }}</h3>
  <ul>
    {%- for post in site.posts -%}
      {%- if post.cat == tag -%}
        <li><a href="{{ post.url }}">{{ post.title }} - {{ post.date | date: "%m/%d/%Y" }}</a></li>
      {%- endif -%}
    {%- endfor -%}
  </ul>
{% endfor %}