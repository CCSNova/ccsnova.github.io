---
layout: page
title: Guides
titletop: Guides
permalink: /guides/
---

<h3>Guides</h3>
<ul>
    {%- for post in site.posts -%}
      {%- if post.cat == "Guide" -%}
        <li><a href="{{ post.url }}">{{ post.title }} - {{ post.date | date: "%d/%m/%Y" }}</a></li>
      {%- endif -%}
    {%- endfor -%}
</ul>