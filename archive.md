---
layout: page
title: Archive
titletop: Archive
permalink: /archive/
---

{% for tag in site.catagoreys %}
{%- if tag != "Guide" -%}
  <h3>{{ tag | escape | capitalize }}</h3>
  <ul>
    {%- for post in site.posts -%}
      {%- if post.categories[0] == tag -%}
      {%- if post.categories[0] != "guide" -%}
        <li><a href="{{ post.url }}">{{ post.title }} - {{ post.date | date: "%d/%m/%Y" }}</a></li>
      {%- endif -%}
      {%- endif -%}
    {%- endfor -%}
  </ul>
{%- endif -%}
{% endfor %}