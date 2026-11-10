---
layout: archive
title: "Presentations"
permalink: /talks/
author_profile: true
---

  {% for post in site.talks reversed %} 
    {% if post.type == 'Talk' %} 
      {% include archive-single-talks.html %}
    {% endif %}
  {% endfor %}

