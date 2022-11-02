---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---


{% for heading in site.headings %}
<h2>{{ heading.title}}</h2>
{% assign pages = site.pages | where_exp:"fixture", "fixture.tags == heading.tag" %}
<ul>
{% for page in pages %}
    <li><a href="{{page.url |absolute_url}}">{{page.title}}</a></li>
{% endfor %}
</ul>
{% endfor %}
