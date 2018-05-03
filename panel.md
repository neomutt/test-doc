---
layout: concertina
title: Panels
description: Screen areas
---

# {{ page.title }}

Description...

## Listing

blurb...

<table summary="list of panels">
  <thead>
    <tr>
      <th>Panel</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    {% for p in site.panel %}
      <tr>
        <td><a href="{{ p.url }}">{{ p.title }}</a></td>
        <td>{{ p.description }}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>
