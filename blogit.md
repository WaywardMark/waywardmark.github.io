---
layout: blog
title: Mark's Blog
subtitle: Curiosity Ignites the Quest


---

<div class="{% if page.full-width %} container-fluid {% else %} container-md {% endif %}">
  <div class="row">
    <div class="{% if page.full-width %} col {% else %} col-xl-8 offset-xl-2 col-lg-10 offset-lg-1 {% endif %}">
      
      <h1>{{ page.title }}</h1>
  {% assign postCount = 0 %}
  {% for post in site.posts %}
    {% assign postCount = postCount | plus: 1 %}
    <h2>{{ post.title }}</h2>
    <p>{{ post.date | date_to_string }}</p>
    <p>{{ post.excerpt }}</p>
    <a href="{{ post.url }}">Read more</a>
    <hr>

    {% if postCount == 5 %}
      <a href="/blog/page/2" class="btn btn-primary">Next Page</a>
      {% break %}
    {% endif %}

  {% endfor %}

  <p>Total Posts: {{ postCount }}</p>

      
      
    </div>
  </div>
</div>


