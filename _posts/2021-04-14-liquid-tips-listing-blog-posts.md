---
title: Jekyll Tips - Listing Blog Posts 
---

Here is tips to list up your Blog Posts using Jekyll.

## Code which did not work

The liquid code which did not work for Project page.

{% raw %}
```liquid
<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>
```
{% endraw %}

Output:

<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>

The URL seems to point `/YYYY/MM/DD/title.html`.

## Code which worked

Following code worked.

The `relative_url` filter shall be used,
when yor blog is located on sub-directory of the site.

{% raw %}
```liquid
<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>
```
{% endraw %}

Output:

<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>

## Better code - pagination

It is better to consider pagination.

{% raw %}
```liquid
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

```
{% endraw %}

Output:

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
* Jekyll > [Liquid Filters](https://jekyllrb.com/docs/liquid/filters/)
* [How to escape liquid template tags?](https://stackoverflow.com/questions/3426182/how-to-escape-liquid-template-tags)
    * To write this article, I needed to learn how to escape liquid tags.
