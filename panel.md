---
layout: concertina
title: Panels
description: Screen areas
---

# {{ page.title }}

Description...

## Listing

blurb...

| Panel | Description |
| :---  | :---        |
{% for p in site.panel %}| **[{{ p.title }}]({{ site.baseurl }}{{ p.url }})** | {{ p.description }} |
{% endfor %}

