---
title: Liquid Tips - Listing Blog Posts 
---

When you list Blog Posts using liquid, [pagination](https://jekyllrb.com/docs/pagination/) should be considered.

## Detail

The liquid code which did not work for Project page.

{% raw %}
```
<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>
```
{% endraw %}

The URL pointed to `https://aikige.github.io/YYYY/MM/DD/title.html`.

Followin code worked.

{% raw %}
```
{% if site.paginate %}
    {% assign posts = paginator.posts %}
{% else %}
    {% assign posts = site.posts %}
{% endif %}

<ul>
  {% for post in posts %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>
```
{% endraw %}

## Output

<!-- to retrieve URL for blog posts, need to consider paginate -->
{% if site.paginate %}
    {% assign posts = paginator.posts %}
{% else %}
    {% assign posts = site.posts %}
{% endif %}

<!-- list blogs -->
<ul>
  {% for post in posts %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>

## Reference

* jekyll/minima > [home.html](https://github.com/jekyll/minima/blob/master/_layouts/home.html)
* [How to escape liquid template tags?](https://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags)
    * To write this article, I needed to learn how to escape liquid tags.
