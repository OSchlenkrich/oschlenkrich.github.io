---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}


Peer-Reviewed Articles
{% for post in site.publications reversed %}
  {% if post.venue contains 'peer-reviewed' %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}


Books and Monographs
{% for post in site.publications reversed %}
  {% if post.venue contains 'books' %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}


Book Chapters
{% for post in site.publications reversed %}
  {% if post.venue contains 'bookchapter' %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}


Other Articles
{% for post in site.publications reversed %}
  {% if post.venue contains 'other' %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}
