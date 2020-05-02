---
layout: default
---

## Welcome

<!-- liste tous les posts présents dans le dossier _posts/ -->
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

[back](./)
