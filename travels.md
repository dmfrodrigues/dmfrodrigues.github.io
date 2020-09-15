---
layout: page
title: Travels
permalink: /travels/
---

<ul class="post-list">
    {% for travel in site.travels %}
        <li>
            <span class="post-meta">{{ travel.when }}</span>
            <h3><a class="post-link" href="{{ travel.url }}">{{ travel.country }} ({{ travel.where }})</a></h3>
        </li>
    {% endfor %}
</ul>
