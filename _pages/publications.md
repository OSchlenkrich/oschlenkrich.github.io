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

Peer
====
{% for post in site.publications.pubpeer reversed %}
  {% include archive-single.html %}
{% endfor %}

other
====
{% for post in site.publications.pubother reversed %}
  {% include archive-single.html %}
{% endfor %}
