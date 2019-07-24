---
layout: page
permalink: /categories/
title: Categories
---

<section>
  {% for category in site.categories %}
    
    {% capture category_name %}{{ category | first }}{% endcapture %}

      <h3 class="category-head">{{ category_name }}</h3>
      <a name="{{ category_name | slugize }}"></a>
      <ul>
        {% for post in site.categories[category_name] %}
          <li>{{ post.order }}
            <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">
              {{ post.title }}
            </a>
          </li>
        {% endfor %}
      </ul>

    {% endfor %}
</section>