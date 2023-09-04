---
layout: 
title: 
permalink: /calendar-data/
---

{% assign all_assignment_dues = site.assignments | map: "due_event" %}

{% assign all_events = site.events | concat: site.lectures %}
{% assign all_events = all_events | concat: site.assignments %}
{% assign all_events = all_events | concat: all_assignment_dues %}
{% assign all_events_sorted = all_events | sort: 'date' %}

[
{% for event in all_events_sorted %}
    {
		"title": "{{event.title}} - Section {{event.section}}",
		"start": "{{event.date}}",
		"allDay": true
	}
	{%unless forloop.last %},{%endunless%}
{% endfor %}
]
