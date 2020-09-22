---
layout: page
title: Travels
permalink: /travels/
---

One of my favourite activities is travelling. Although most travels have nothing to do with my trade (and even if they do, I focused on the parts that may interest to a larger audience), I thought it was a good idea to leave here some thoughts and experiences of my stays abroad, almost like a diary. I mostly reflect on what's aesthetic (places to visit) and what makes up its people (language, history, culture, reasoning and attitudes).

<ul class="post-list">
    {% assign travel_sorted = site.travels | sort: 'date' | reverse %}
    {% for travel in travel_sorted %}
        <li>
            <span class="post-meta">{{ travel.when }}</span>
            <h3><a class="post-link" href="{{ travel.url }}">{{ travel.country_flag_emoji }} {{ travel.country }} ({{ travel.where }})</a></h3>
        </li>
    {% endfor %}
</ul>
