---
layout: about
title: About
permalink: /about
custom_js_external:
- "https://cdn.jsdelivr.net/npm/d3@7"
- "https://unpkg.com/topojson@3"
- "https://cdn.jsdelivr.net/gh/dmfrodrigues/globe@latest/js/globe.js"
---

My name is Diogo Rodrigues, and I am a 3rd year [Informatics Engineering](https://sigarra.up.pt/feup/en/cur_geral.cur_view?pv_curso_id=742) student at [FEUP](https://sigarra.up.pt/feup/en/WEB_PAGE.INICIAL). I live in [Maia](https://en.wikipedia.org/wiki/Maia,_Portugal), near the city of [Porto](https://en.wikipedia.org/wiki/Porto), in Portugal. I am not yet sure on what I want to work with in the future, although I have interest in algorithmics, critical systems/operating systems, cybersecurity and web development (in this order). I am also into competitive programming, and I regularly attend national and international competitions.

You can check on [my "short" CV]({{site.cv}}) (in English).

I usually go by the username **dmfrodrigues**. For some other purposes I tend to use **Nautilus** or something along those lines, hence the slightly coiled-shell-themed website.

<div class="masonry-vertical">
<div markdown="1">

{% assign p = site.pages | where: "title", "Projects" | first %}
## [{{p.emoji}} {{p.title}}]({{ p.url | relative_url }})

I have been involved in several projects, some related to university, others not no much. Check them out [here](/projects)!

<div class="projects-grid-container">
<div><a href="/projects"><img src="https://i.imgur.com/69YCcZ8m.png" alt="mandelbrot-detail"></a></div>
<div><a href="/projects"><img src="https://i.imgur.com/zAOwCGem.png" alt="graphviewercpp"></a></div>
<div><a href="/projects"><img src="https://i.imgur.com/PiqStSQm.jpg" alt="glaisher"></a></div>
<div><a href="/projects"><img src="https://i.imgur.com/Y7H4LZlm.png" alt="foreverhome"></a></div>
</div>

</div>
<div markdown="1">

{% assign p = site.pages | where: "title", "Competitive programming" | first %}
## [{{p.emoji}} {{p.title}}]({{ p.url | relative_url }})

Competitive programming is a sport, involving several contestants trying to solve as many problems as possible in a given time limit, often using creative approaches to those problems. One of the things people benefit the most from competitive programming is algorithmic reasoning: to truly understand what algorithms do, so you can adapt them or invent new ones to solve problems. Competitive programming is a very good hobby for your professional life for three main reasons: it helps potential developers with job interviews, it keeps you thinking about interesting problems and the languages you use to solve problems will always stay fresh.

Every year I go through approximately the same sequence of events: national competition (MIUP), a faculty-level competition in the middle, then regional ICPC competition (SWERC), and then other competitions like Google Code Jam. I can say my results so far have been reasonable, as most of the times we end up in top 4 in Portugal. 

</div>
<div markdown="1">

{% assign p = site.pages | where: "title", "Travels" | first %}
## [{{p.emoji}} {{p.title}}]({{ p.url | relative_url }})

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

It is one of my favourite hobbies, and I like every part of the trip (even being closed in a flying metal box for hours is fascinating, if not for the views or whatever I have to entertain myself, then for the expectation). You can find more about my travels [here](/travels).

</div>
<div markdown="1">

{% assign p = site.pages | where: "title", "Music" | first %}
## [{{p.emoji}} {{p.title}}]({{ p.url | relative_url }})

My favourite genre is metal, but I also like alternative/progressive rock. My favourite band is [Muse](https://en.wikipedia.org/wiki/Muse_(band)), occasionally followed by [System of a Down](https://en.wikipedia.org/wiki/System_of_a_Down) although I usually prefer more artsy music. My favorite album is [Origin of Symmetry](https://en.wikipedia.org/wiki/Origin_of_Symmetry) by Muse. More on my favorite songs [here](/music).

<div class="music-grid-container">
    <div><img src="https://i.imgur.com/r9WtLzut.jpg" alt="Origin of Symmetry (Muse)"></div>
    <div><img src="https://i.imgur.com/ltV9mEbt.jpg" alt="Homura Uta (MUCC)"></div>
    <div><img src="https://i.imgur.com/ePOeitUt.jpg" alt="Motherblood (Grave Pleasures)"></div>
    <div><img src="https://i.imgur.com/m6O9XK8t.gif" alt="O monstro precisa de amigos (Ornatos Violeta)"></div>
    <div><img src="https://i.imgur.com/PrMvcEqt.jpg" alt="The Observer (Artificial Language)"></div>
    <div><img src="https://i.imgur.com/3xyfXrEt.jpg" alt="Hypnotize (System of a Down)"></div>
</div>

</div>
</div>
