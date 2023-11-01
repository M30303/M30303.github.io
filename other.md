---
layout: page
title: other | M30303
---

<section>
  {% if site.other[0] %}

    {% capture currentyear %}{{ 'now' | date: "%Y" }}{% endcapture %}
    {% capture firstpostyear %}{{ site.other[0].date | date: '%Y' }}{% endcapture %}
    {% if currentyear == firstotheryear %}
        <h3>Lifestyle</h3>
    {% else %}
        <h3>{{ firstotheryear }}</h3>
    {% endif %}

    {%for other in site.other %}
      {% unless other.next %}
        <ul>
      {% else %}
        {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
          </ul>
          <h3>{{ other.date | date: '%Y' }}</h3>
          <ul>
        {% endif %}
      {% endunless %}
        <li><time>{{ other.date | date:"%d %b" }} - </time>
          <a href="{{ other.url | prepend: site.baseurl | replace: '//', '/' }}">
            {{ other.title }}
          </a>
        </li>
    {% endfor %}
    </ul>

  {% endif %}
</section>
