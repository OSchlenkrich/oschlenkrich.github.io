---
layout: archive
#title: "Publications"
permalink: /cvtest/
author_profile: true

template: svm-latex-cv.tex
geometry: margin=1in

title: "CV"
author: Oliver Schlenkrich

jobtitle: "Postdoctoral Research Fellow"
address: "Berlin, Germany"
fontawesome: yes
email: oliver.schlenkrich@outlook.de
# github: svmiller
# phone: "+353 1 408 4800"
web: oschlenkrich.github.io
updated: no

keywords: R Markdown, academic CV, template

fontfamily: mathpazo
fontfamilyoptions: sc, osf
fontsize: 11pt
linkcolor: blue
urlcolor: blue
---


# Emplyoment 


# Education


# Presentations



# Publications

{% include base_path %}

{% for post in site.publications reversed %}
  {% if post.venue contains 'peer-reviewed' %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}
