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


## Some html testing
Some text without html. <b>bold</b> is working?

---
## Standard stuff from Jekyll
Read [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

Complete usage and documentation available at: [Jekyll Bootstrap](http://jekyllbootstrap.com)

## Update Author Attributes

In `_config.yml` remember to specify your own data:
    
title : Frodo's Private Blog

	etest
	    
    author :
      name : Frodo
      email : frodo@bj-wunder.de
      github : frodo81
      twitter : frodi81

The theme should reference these variables whenever needed.
    
## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

This theme is still unfinished. If you'd like to be added as a contributor, [please fork](http://github.com/plusjade/jekyll-bootstrap)!
We need to clean up the themes, make theme usage guides with theme-specific markup examples.


