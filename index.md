---
layout: default
title: Home
---
{% assign date = '2025-08-21T10:20:00Z' %}

<div class="home-intro">
  <h1>{{ site.title }}</h1>
  <p class="lead">{{ site.description }}</p>
</div>

{% assign posts = paginator.posts | default: site.posts %}

{% if posts == empty %}

<p>No posts found yet. Check back soon.</p>

{% else %}

<ul class="post-list">
  {% for post in posts %}
  <li class="post">
    <article>
      <h2 class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      <p class="post-meta">{{ post.date | date: "%B %-d, %Y" }}{% if post.categories and post.categories != empty %} • {{ post.categories | array_to_sentence_string }}{% endif %}</p>
      <div class="post-excerpt">{{ post.excerpt | strip_html | truncate: 250 }}</div>
      <p><a class="read-more" href="{{ post.url | relative_url }}">Read more →</a></p>
    </article>
  </li>
  {% endfor %}
</ul>

{% if paginator and paginator.total_pages > 1 %}
<nav class="pagination">
  {% if paginator.previous_page %}
    <a class="prev" href="{{ paginator.previous_page_path | relative_url }}">&laquo; Prev</a>
  {% endif %}

  <span class="page-info">Page {{ paginator.page }} of {{ paginator.total_pages }}</span>

  {% if paginator.next_page %}
    <a class="next" href="{{ paginator.next_page_path | relative_url }}">Next &raquo;</a>
  {% endif %}
</nav>
{% endif %}

{% endif %}


Copyright