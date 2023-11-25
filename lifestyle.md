---
layout: default
---

<section>
  {% assign lifestyle_posts = site.lifestyle | where: "category", "lifestyle" %}
  {% if lifestyle_posts.size > 0 %}
    <h3>Lifestyle</h3>
    <ul>
      {% for post in lifestyle_posts %}
        <li>
          <time>{{ post.date | date: "%d %b" }} - </time>
          <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">
            {{ post.title }}
          </a>
        </li>
      {% endfor %}
    </ul>
  {% endif %}
</section>
