---
title: About
permalink: /about/
layout: outer 
---

<div class="container">
  <div class="row">
    <div class="col">
      <h1 class="display-4 text-center">Team Phone Box</h1>
    </div>
  </div>
  {% assign people = site.data.people | sort: "name" %}
  {% for person in people %}
  <div class="row mb-4">
    <div class="col-7">
      <div class="float-left mr-4" style="width:40%;">
        <img src="{{ person.headshot }}" class="img-fluid" width="100%" class="team-headshot">
      </div>
      <h2 class="display-4">{{ person.name }}<br><small>{{ person.role }}</small></h2>
      <p>{{ person.bio | markdownify }}</p>
    </div>
    <div class="col-5 mt-5 pt-4">
      <h3><strong>Reviews of {{ person.name | truncatewords: 1, "" }}'s other work</strong></h3>
      {% for show in person.shows %}
        <h4>{{ show.first.first }}</h4>
        {% for review in show %}
          {% for item in review offset:1 %}
            {% for node in item %}
              <p>"{{ node.quote }}" <br><span class="ml-4">&mdash; <a href="{{ node.link }}">{{ node.author }}</a></span></p>
            {% endfor %}
          {% endfor %}
        {% endfor %}
        <hr>
      {% endfor %}
    </div>
  </div>
  {% endfor %} 
</div>