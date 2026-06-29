---
layout: page
title: blog
permalink: /blog/
description: Notes on databases, SQL Server performance, data architecture, and AI.
nav: true
nav_order: 2
pagination:
  enabled: true
---

<div class="post">

  <ul class="post-list">
    {%- assign date_format = site.minima.date_format | default: "%B %-d, %Y" -%}
    {%- for post in paginator.posts -%}
    <li>
      {%- assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 -%}
      {%- assign today = 'now' | date: "%Y" -%}
      {%- assign date_year = post.date | date: "%Y" -%}

      <h3>
        {% if post.external_url %}
          <a class="post-link" href="{{ post.external_url }}" target="_blank" rel="noopener">{{ post.title }}</a>
        {% else %}
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title }}</a>
        {% endif %}
      </h3>
      <p class="post-meta">
        {{ post.date | date: site.minima.date_format | default: "%B %-d, %Y" }}
        &nbsp;&middot;&nbsp;
        <i class="fa-solid fa-clock"></i> {{ read_time }} min read
      </p>
      {% if post.excerpt %}
        <p>{{ post.excerpt | strip_html | truncate: 200 }}</p>
      {% endif %}
    </li>
    {%- endfor -%}
  </ul>

  {% include pagination.liquid %}

</div>
