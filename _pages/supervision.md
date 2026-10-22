---
layout: archive
title: "Supervision"
permalink: /supervision/
author_profile: true
---

{% capture students_text %}{% include_relative students.cvs %}{% endcapture %}
{% assign rows = students_text | strip | newline_to_br | strip_newlines | split: '<br />' %}
{% assign students = rows | slice: 1, rows.size | sort | reverse %}

<div class="container">
  <h2>Student supervision</h2>
  <p>
    I have had the pleasure of supervising the work of
    amazing students and junior researchers.
  </p>
  <ul id="student-list">
    {% for row in students %}
      {% assign line = row | strip %}
      {% if line != '' %}
        {% assign fields = line | split: ';' %}
        {% assign grade = fields[6] | default: '' | strip %}
        <li>
          <strong>{{ fields[1] | strip | escape }}</strong>
          ({{ fields[0] | strip | escape }})<br>
          <em>{{ fields[2] | strip | escape }}</em><br>
          {{ fields[3] | strip | escape }} ·
          {{ fields[4] | strip | escape }} ·
          {{ fields[5] | strip | escape }}
          {% if grade != '' %}
            <br>Grade: {{ grade | escape }}
          {% endif %}
        </li>
      {% endif %}
    {% endfor %}
  </ul>
</div>
