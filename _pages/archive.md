---
layout: archive
permalink: /archive.html
title: "Archive"
author_profile: false
toc: true
toc_label: "Table des matières"
toc_sticky: true
---
## Chronologique

<section class="archive-post-list">
   {% for post in site.posts %}
       {% assign currentDate = post.date | date: "%Y" %}
       {% if currentDate != myDate %}
           {% unless forloop.first %}</ul>{% endunless %}
            <h3> {{ currentDate }} </h3>
           <ul>
           {% assign myDate = currentDate %}
       {% endif %}
       <li><a href="{{ post.url }}">{{ post.title }}<span style="color:blue;font-size:10px"> {{ post.date | date: "%B %-d" }}</span></a></li>
       {% if forloop.last %}</ul>{% endif %}
   {% endfor %}
</section>

## Par catégorie

{% include group-by-array collection=site.posts field="categories" %}

{% for category in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ category | slugify }}" class="archive__subtitle">{{ category }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
