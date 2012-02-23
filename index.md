---
layout: page
title: Frodo's Welt
---
{% include JB/setup %}

Mein Name ist Frodo und ich möchte hier mein digitales Tagebuch schreiben.
Dazu verwende ich natürlich nur cooles Hackerzeug. Neugierig?

Ok, ich schreibe diesen blog mit folgenden Tools: 
- Meine Dateien editiere ich mit dem coolen vim
- Das legendäre git sorgt für die Ordnung ;-)
- Dank github kann ich diesen Blog hier ganz leicht mit einem git push
  veröffentlichen.
- "And last but not least" benutze ich das geniale Jekyll für das Parsen des
  Quellcodes.

Wer sich für diese Art des Blog schreibens intressiert wird auf [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html) und
[Jekyll Bootstrap](http://jekyllbootstrap.com) weitere Infos finden. 

## Alle Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

This theme is still unfinished. If you'd like to be added as a contributor, [please fork](http://github.com/plusjade/jekyll-bootstrap)!
We need to clean up the themes, make theme usage guides with theme-specific markup examples.


