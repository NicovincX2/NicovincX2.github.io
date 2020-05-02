---
layout: default
---

## Welcome

<!-- liste tous les posts présents dans le dossier _posts/ -->
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <!-- extrait du post, tout texte avant le séparateur configuré dans _config.yml -->
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>

[back](./)
