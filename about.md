---
layout: about
title: About
permalink: /about/
custom_js_external:
- "https://cdn.jsdelivr.net/npm/d3@7"
- "https://unpkg.com/topojson@3"
- "https://cdn.jsdelivr.net/gh/dmfrodrigues/globe@latest/js/globe.js"
---

My name is Diogo Rodrigues, and I am a 3rd year [Informatics Engineering](https://sigarra.up.pt/feup/en/cur_geral.cur_view?pv_curso_id=742) student at [FEUP](https://sigarra.up.pt/feup/en/WEB_PAGE.INICIAL). I live in [Maia](https://en.wikipedia.org/wiki/Maia,_Portugal), near the city of [Porto](https://en.wikipedia.org/wiki/Porto), in Portugal. I am not yet sure on what I want to work with in the future, although I have interest in algorithmics, critical systems/operating systems, cybersecurity and web development (in this order). I am also into competitive programming, and I regularly attend national and international competititions.

You can check on my full CV [in Portuguese](https://drive.google.com/uc?id=12vRqYdYs_r6E22g_MHJ5Fm8FdlEDVQVn) (CV in English is soon to come).

<div class="masonry-vertical">
<div markdown="1">

## Competitive programming

Competitive programming is a sport, involving several contestants trying to solve as many problems as possible in a given time limit, often using creative approaches to those problems. One of the things people benefit the most from competitive programming is algorithmic reasoning: to truly understand what algorithms do, so you can adapt them or invent new ones to solve problems.

Every year I go through approximately the same sequence of events: national competitition (MIUP), a faculty-level competition in the middle, then regional ICPC competition (SWERC), and then other competitions like Google Code Jam. I can say my results so far have not been too bad, but definitely not good either, as most of the times we end up in top 4 in Portugal and a third of the scoreboard from the top in SWERC. Of course I am constantly striving to improve on that, although it is not always easy given I still have a course to finish. Nevertheless, I am fascinated by algorithms, it is a very good hobby for your professional life as a developer (as it helps a lot in job interviews), and it helps in reasoning (aside from being the perfect excuse to travel not too far from home).

</div>
<div markdown="1">

## Travelling

<svg id="globe" class="globe center" viewBox="0 0 400 400"></svg>
<script>
window.addEventListener("load", async function(){
    let globe = new Globe("svg#globe", 400);
    globe.rotation = [0, -10, 0];
    await globe.initialize();

    globe.nativeCountry("Portugal");

    {% for country in site.data.locations_visited.countries %}
        globe.highlightCountry("{{country.country}}");
    {% endfor %}

    globe.enableDrag();

    globe.registerRotation(10, 0.002);
});
</script>

It is one of my favourite hobbies, and I like every part of the trip (even being closed in a flying metal box for hours is fascinating, if not for the views or whatever I have to entertain myself, then for the expectation). You can find more about my travels [here]({{ site.baseurl }}/travels), or by clicking in the globe.

</div>
<div markdown="1">

## Music

I love music. I think it goes well with any activity (especially studying, travelling, and sleeping) and is appropriate pretty much everytime. I can't really remember how much time Spotify Wrapped said I was listening to Spotify, but it was quite a lot (maybe above 100,000 minutes in 2019).

My favourite genre is metal (of any kind, but generally the heavier the better). I also like alternative/progressive rock, and my favourite band is [Muse](https://en.wikipedia.org/wiki/Muse_(band)), occasionally followed by [System of a Down](https://en.wikipedia.org/wiki/System_of_a_Down) although I usually prefer more artsy music. Some of the bands I also appretiate include [Paradise Lost](https://en.wikipedia.org/wiki/Paradise_Lost_(band)), [Trivium](https://en.wikipedia.org/wiki/Trivium_(band)) and [Dark Tranquility](https://en.wikipedia.org/wiki/Dark_Tranquillity).
 
My main music platform is Spotify (here is [my account](https://open.spotify.com/user/dmfrodrigues2000)). I occasionally use Youtube to search some songs that are otherwise not on Spotify (or to listen to nightcore songs of radios when I'm bored of what I've been listening). Here are the songs I have most listened to since I have Spotify (sorted by most times listened).

<iframe class="spotify" src="https://open.spotify.com/embed/playlist/6nzC0NHZW6Vh1Mt1rrjyim" height="380" frameborder="0" allowtransparency="true" allow="encrypted-media"></iframe>

</div>
</div>
