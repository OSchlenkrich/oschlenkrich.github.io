---
layout: archive
title: "Curriculum Vitae"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

<style>
h1 {
  margin-top: 20px;
  font-size: 20px;
}
h3 {
  margin-top: 0px;
  font-size: 16px;
}
ul li {
   font-size: 16px;
   margin-bottom: 8px;
}
p {
   font-size: 16px;
   margin: 0px;
} 
.archive__item-title {
  font-weight:normal;
}
</style>

{% include base_path %}


Education
======
* Ph.D in Comparative Political Science, University of Wuerzburg, 2021
* Teacher Education for Secondary Education (Gymnasium) German/Social Studies/Philosophy (1. State Examination), 2013


Work experience
======
* 01.05.2021 - 30.09.2021: Research Assistant

  Empirical Social Research, TU Kaiserslautern

  Supervisor: Prof. Dr. Best


* 01.04.2018 - 30.06.2021: Research Assistant

  Project "Causes of Quality Types and Democracy Profiles" funded by the German Research Foundation (DFG)


* 01.04.2016 - 31.03.2018: Research Assistant

  Project "Democracy Matrix" funded by the German Research Foundation (DFG)


* 01.10.2013 - 30.06.2021: Research Assistant

  Chair of Comparative Politics and German Government, University of Wuerzburg

  Supervisor: Prof. Dr. Lauth


Key Research Areas
======
* Quality of Democracy & Democratization
* Populism 
* Statehood 
* Political Culture
* Time-Series Cross-Sectional Analysis 
* Multilevel Analysis 
* Bayesian Analysis
* Cluster Analysis


Publications
======
Peer-Reviewed Articles
<ul>{% for post in site.publications reversed %}
  {% if post.venue contains 'peer-reviewed' %}
    {% include archive-single-cv.html %}
  {% endif %} {% endfor %}</ul>

Books and Monographs
<ul>{% for post in site.publications reversed %}
  {% if post.venue contains 'books' %}
    {% include archive-single-cv.html %}
  {% endif %} {% endfor %}</ul>

Book Chapters
<ul>{% for post in site.publications reversed %}
  {% if post.venue contains 'bookchapter' %}
    {% include archive-single-cv.html %}
  {% endif %} {% endfor %}</ul>

Other Articles
<ul>{% for post in site.publications reversed %}
  {% if post.venue contains 'other' %}
    {% include archive-single-cv.html %}
  {% endif %} {% endfor %}</ul>


Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk_cv.html %}
  {% endfor %}</ul>


Method Schools
======
* Bayesian Multilevel Modelling

  48th GESIS Spring Seminar, Cologne
  
  25.03.2019 – 29.03.2019
  

* Bayesian Structural Equation Modelling

  48th GESIS Spring Seminar, Cologne
  
  18.03.2019 – 22.03.2019
  
  
* Gentle Introduction to Machine Learning for the SocialSciences

  12th ECPR Summer School in Methods and Techniques, Budapest
  
  07.08.2017 – 11.08.2017 
  
  
* Time Series Analysis

  12th ECPR Summer School in Methods and Techniques, Budapest
  
  31.07.2017 – 04.08.2017
  
  
* Multilevel Analysis

  ECPR Winter School, Bamberg
  
  13.02.2015 – 20.02.2015


Language Skills
======
* German (Mother Tongue)
* English (C2)
* French (A1)
* Arabic (Reading A1)


Digital Skills
======
* Statistical Software: R and RStudio, Python, Mplus, R shiny, IBM SPSS
* Bayesian Statistical Software: Stan (Bayesian Statistical Modeling), Jags (Bayesian Statistical Modeling)
  
