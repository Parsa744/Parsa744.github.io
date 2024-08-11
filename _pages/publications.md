---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if site.author.googlescholar %}
  <div class="wordwrap">You can also find my articles on <a href="{{site.author.googlescholar}}">my Google Scholar profile</a>.</div>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
[Magnetic casein aggregates as an innovative support platform for laccase immobilization and bioremoval of crystal violet](https://www.sciencedirect.com/science/article/pii/S014181302102729X?casa_token=UNvdFNLvbikAAAAA:zCtBivQmEuEGBftyYCTRaqMnt_lPEZ8vW7Fi2z8aQ9Bzfnqr2HmU3FEfCZ_aDHnfFfNEuFexyg)
