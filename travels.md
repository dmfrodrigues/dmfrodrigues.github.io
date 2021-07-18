---
layout: page
title: Travels
permalink: /travels/
custom_js_external:
- "https://cdn.jsdelivr.net/npm/d3@7"
- "https://unpkg.com/topojson@3"
- "https://cdn.jsdelivr.net/gh/dmfrodrigues/globe@latest/js/globe.js"
---

One of my favourite activities is travelling. Although most travels have nothing to do with my trade (and even if they do, I focused on the parts that may interest to a larger audience), I thought it was a good idea to leave here some thoughts and experiences of my stays abroad, almost like a diary. I mostly reflect on what's aesthetic (places to visit) and what makes up its people (language, history, culture, reasoning and attitudes).

<svg id="globe" class="globe" viewBox="0 0 800 800"></svg>
<script>
window.addEventListener("load", async function(){
    const marker = await fetch("{{ site.baseurl }}/assets/marker.svg").then(r => r.text());

    let globe = new Globe("svg#globe", 800, marker);
    globe.rotation = [0, -10, 0];
    await globe.initialize();
    globe.setMarker(marker, 7.025, 21.7833);

    globe.nativeCountry("Portugal");
    globe.addLocation([-8.6291, 41.1579], "Porto", "native");

    {% for country in site.data.locations_visited.countries %}
        globe.highlightCountry("{{country.country}}");
    {% endfor %}

    {% for country in site.data.locations_visited.countries %}
        {% for city in country.cities %}
            globe.addLocation({{city.coordinates | jsonify}}, "{{city.city}}", "highlight");
        {% endfor %}
    {% endfor %}

    globe.enableDrag();
    globe.enableZoom();

    globe.registerRotation(10, 0.002);
});
</script>

Here are the places I have visited so far:

- 🇪🇸 **Spain**: Tordesillas (Jun 2014), Sevilla (Jul 2017)
- 🇩🇰 **Denmark**: Esbjerg, Ribe (Feb 2015), Copenhagen (May 2017)
- 🇩🇪 **Germany**: Flensburg (Feb 2015)
- 🇫🇷 **France**: Lyon (Jul 2016), Paris (Dec 2018, Jan 2020)
- 🇮🇪 **Ireland**: Dublin (Jul 2018)
- 🇯🇵 **Japan**: Tokyo, Tsukuba (Sep 2018)
- 🇫🇮 **Finland**: Helsinki (Sep 2018)
- 🏴󠁧󠁢󠁥󠁮󠁧󠁿 **England**: London, Oxford, Cambridge (Jul-Aug 2019)


I have written posts only for the most memorable ones, or the ones that triggered the most remarks.

<ul class="post-list">
    {% assign travel_sorted = site.travels | sort: 'date' | reverse %}
    {% for travel in travel_sorted %}
        <li>
            <span class="post-meta">{{ travel.when }}</span>
            <h3><a class="post-link" href="{{ travel.url }}">{{ travel.country_flag_emoji }} {{ travel.country }} ({{ travel.where }})</a></h3>
        </li>
    {% endfor %}
</ul>
