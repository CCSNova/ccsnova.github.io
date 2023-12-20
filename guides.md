---
layout: page
title: Guides
titletop: Guides
permalink: /guides/
---

<ul>
    {%- for post in site.guides -%}
      {%- if post.cat == "Guide" -%}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {%- endif -%}
    {%- endfor -%}
</ul>