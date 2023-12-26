---
layout: page
title: Archive
titletop: Archive
permalink: /archive/
---

{% for tag in site.catagoreys %}
{%- if tag != "guide" -%}
  <h3>{{ tag | escape | capitalize }}</h3>
  <ul>
    {%- for post in site.posts -%}
      {% capture author %}
        {% if post.author %}
          {{ post.author }}
        {% else %}
          {{ site.author }}
        {% endif %}
      {% endcapture %}
      {%- if post.categories[0] == tag -%}
      {%- if post.categories[0] != "guide" -%}
        <li><a href="{{ post.url }}">{{ post.title }} - {{ post.date | date: "%d/%m/%Y" }} - {{ author }}</a></li>
      {%- endif -%}
      {%- endif -%}
    {%- endfor -%}
  </ul>
{%- endif -%}
{% endfor %}