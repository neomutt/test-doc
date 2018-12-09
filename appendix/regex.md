---
layout: concertina
title: Regular expressions 
description: Regular expressions
---

# {{ page.title }}

Regular expressions

## Overview

## Examples

### Internet

	"[-a-z_0-9.+]+@[-a-z_0-9.]+"				# E-Mail
	"((ftp|http|https)://|news:)[^ >)\"\t]+"	# URL

### Markup / Markdown

	"^==+[[:print:]]+$"							# Heading
	"(^| )_[[:print:]]+_[ \n]"					# Underscore

### Miscellaneous

	"\\[[0-9]+\\]"								# Number [x]
	"\\[\\.\\.\\.?\\]"							# [...]
	"[;:]-*[)oO>(<D]"							# Smileys


