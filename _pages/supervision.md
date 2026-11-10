---
layout: archive
title: "Supervision"
permalink: /supervision/
author_profile: true
---

<p>
  I have had the pleasure of supervising the work of
  amazing students and junior researchers.
</p>

{% assign levels = 'Master,Bachelor' | split: ',' %}

{% for level in levels %}
  {% if level == 'Master' %}
    {% capture students_text %}{% include_relative master.cvs %}{% endcapture %}
  {% else %}
    {% capture students_text %}{% include_relative bachelor.cvs %}{% endcapture %}
  {% endif %}

  {% assign rows = students_text | strip | newline_to_br | strip_newlines | split: '<br />' %}
  {% assign students = rows | slice: 1, rows.size | sort | reverse %}

  <div class="container">
    <h2>{{ level }}</h2>
    <ul id="student-list-{{ level | downcase }}">
      {% for row in students %}
        {% assign line = row | strip %}
        {% if line != '' %}
          {% assign fields = line | split: ';' %}
          {% assign grade = fields[6] | default: '' | strip %}

          <li>
            <strong>{{ fields[1] | strip | escape }}</strong>
            ({{ fields[0] | strip | escape }})
            {% if grade != '' %}
              · Grade: {{ grade | escape }}
            {% endif %}
            <br>
            <em>{{ fields[2] | strip | escape }}</em>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </div>
{% endfor %}
