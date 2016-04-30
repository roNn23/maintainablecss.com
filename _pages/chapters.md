---
layout: chapters
id: chapters
permalink: /kapitel/
title: "Kapitel"
---

{% assign prefaceChapters = site.chapters | where:'section', 'Vorwort' %}
{% assign backgroundChapters = site.chapters | where:'section', 'Hintergrund' %}
{% assign coreChapters = site.chapters | where:'section', 'Kern' %}
{% assign extraChapters = site.chapters | where:'section', 'Extras' %}

# Kapitel

## Vorwort

<ol>
  {% for chapter in prefaceChapters %}
    <li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
  {% endfor %}
</ol>

## Hintergrund

{% assign backgroundStart = prefaceChapters.size | plus: 1 %}

<ol start="{{backgroundStart}}">
  {% for chapter in backgroundChapters %}
    <li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
  {% endfor %}
</ol>

## Kern

{% assign coreStart = backgroundStart | plus: backgroundChapters.size %}

<ol start="{{coreStart}}">
	{% for chapter in coreChapters %}
		<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
	{% endfor %}
</ol>

## Extras

{% assign extrasStart = coreStart | plus: coreChapters.size %}

<ol start="{{extrasStart}}">
	{% for chapter in extraChapters %}
		<li><a href="{{ chapter.url }}">{{ chapter.title }}</a></li>
	{% endfor %}
</ol>