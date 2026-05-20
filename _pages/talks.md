---
layout: page
permalink: /talks/
title: talks
description: Conference talks, invited presentations, and posters. Slides linked where available.
nav: true
nav_order: 3
---

{% assign talks_sorted = site.data.talks | sort: "date" | reverse %}
{% assign by_year = talks_sorted | group_by_exp: "talk", "talk.date | date: '%Y'" %}

<div class="publications">
{% for year_group in by_year %}
  <h2 class="bibliography">{{ year_group.name }}</h2>
  <ol class="bibliography">
    {% for talk in year_group.items %}
      <li>
        <div class="row">
          {% if site.enable_publication_thumbnails %}
            <div class="col col-sm-2 abbr"></div>
          {% endif %}
          <div class="{% if site.enable_publication_thumbnails %}col-sm-8{% else %}col-sm-10{% endif %}">
            <div class="title">{{ talk.title }}</div>
            <div class="author"><em>{{ talk.venue }}</em></div>
            <div class="periodical">
              {% if talk.location %}{{ talk.location }}, {% endif %}{{ talk.date | date: "%b %Y" }}
            </div>
            {% if talk.abstract or talk.slides or talk.poster or talk.url %}
              <div class="links">
                {% if talk.abstract %}<a class="abstract btn btn-sm z-depth-0" role="button">Abs</a>{% endif %}
                {% if talk.slides %}<a href="{{ talk.slides }}" class="btn btn-sm z-depth-0" role="button" rel="external nofollow noopener" target="_blank">Slides</a>{% endif %}
                {% if talk.poster %}<a href="{{ talk.poster }}" class="btn btn-sm z-depth-0" role="button" rel="external nofollow noopener" target="_blank">Poster</a>{% endif %}
                {% if talk.url %}<a href="{{ talk.url }}" class="btn btn-sm z-depth-0" role="button" rel="external nofollow noopener" target="_blank">Event</a>{% endif %}
              </div>
              {% if talk.abstract %}
                <div class="abstract hidden">
                  <p>{{ talk.abstract }}</p>
                </div>
              {% endif %}
            {% endif %}
          </div>
        </div>
      </li>
    {% endfor %}
  </ol>
{% endfor %}
</div>
