---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---


{% for heading in site.headings %}
<h2>{{ heading.title}}</h2>
{% for version in site.versions %}
{% assign pages = site.pages | where_exp:"fixture", "fixture.tags == heading.tag and fixture.version == version" | sort: "title" %}
{% if pages.size != 0%}
<h3>v{{ version }}</h3>
<ul>
{% for page in pages %}
    <li><a href="{{page.url |relative_url}}">{{page.title}}</a></li>
{% endfor %}
</ul>
{% endif %}
{% endfor %}
{% endfor %}
