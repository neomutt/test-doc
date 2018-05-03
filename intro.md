---
layout: concertina
title: Intro
description: Introduction
---

# {{ page.title }}

Description...

## Listing

blurb...

| Intro | Description |
| :---  | :---        |
{% for p in site.intro %}| **[{{ p.title }}]({{ site.baseurl }}{{ p.url }})** | {{ p.description }} |
{% endfor %}

