---
layout: default
title: Categories
permalink: /categories/
---
{% for category in site.categories %}
  <ul class="m-b">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>
    
    <h3 class="category-head">{{ category_name }}</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <li class="nolist border-b">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a> : {{ post.date | date: "%B %d, %Y" }}</h4>
    </li>
    {% endfor %}
  </ul>
{% endfor %}