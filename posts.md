---
layout: page
title: posts | mittens
---

<section>
  {% if site.posts[0] %}

    {% capture currentyear %}{{ 'now' | date: "%Y" }}{% endcapture %}
    {% capture firstpostyear %}{{ site.posts[0].date | date: '%Y' }}{% endcapture %}
    {% if currentyear == firstpostyear %}
        <h3>This year's posts</h3>
    {% else %}
        <h3>{{ firstpostyear }}</h3>
    {% endif %}

    {%for post in site.posts %}
      {% unless post.next %}
        <ul>
      {% else %}
        {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
          </ul>
          <h3>{{ post.date | date: '%Y' }}</h3>
          <ul>
        {% endif %}
      {% endunless %}
        <li><time>{{ post.date | date:"%d %b" }} - </time>
          <a href="{{ post.url | prepend: site.baseurl | replace: '//', '/' }}">
            {{ post.title }}
          </a>
        </li>
    {% endfor %}
    </ul>

  {% endif %}

  <!-- Add a new loop for lifestyle posts -->
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
    </ul>
  {% endif %}
</section>
