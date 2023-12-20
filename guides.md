---
layout: page
title: Guides
titletop: Guides
permalink: /guides/
---

<ul>
    {%- for post in site.posts -%}
      {%- if post.categories[0] == "Guide" -%}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {%- endif -%}
    {%- endfor -%}
</ul>