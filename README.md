# SVG Simple Images

This project is used to publish SVG images that I creted for myself, but might be useful for others.
Most of imaes are created using [Inkscape](https://inkscape.org/).

Since I believe SVG is a kind of code, [MIT License](LICENSE) is applied to all contents in this page.

## List of SVG

|Image|Title|
|:----|:----------|
|![](Arrow/Rotate_90.svg)|Rotate 90|
|![](Arrow/Rotate_90x2.svg)|Rotate 90x2|

## Other Useful Links

---

## Test for Local Pages

* [Test](docs/test.html) - other markdown file seems to be converted automtically.

## Blog Posts

{% if site.paginate %}
    {% assign posts = paginator.posts %}
{% else %}
    {% assign posts = site.posts %}
{% endif %}

<ul>
  {% for post in posts %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a><br />
    {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
