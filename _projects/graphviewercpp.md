---
layout: project
title: "GraphViewerCpp"
permalink: /projects/graphviewercpp/
github: https://github.com/dmfrodrigues/GraphViewerCpp
---

<div class="scroll" markdown="1">
![earth](https://i.imgur.com/WgBv1SM.png)
![scandinavia](https://i.imgur.com/1O18gZ7.png)
![random graph](https://raw.githubusercontent.com/dmfrodrigues/GraphViewerCpp/master/example/resources/graphs/random/preview.png)
![star graph](https://raw.githubusercontent.com/dmfrodrigues/GraphViewerCpp/master/example/resources/graphs/star/preview.png)
![rainbow graph](https://raw.githubusercontent.com/dmfrodrigues/GraphViewerCpp/master/example/resources/graphs/rainbow/preview.png)
</div>

A tool for graph visualization using the SFML library. I initially developed it in Jan-Mar 2021 to overcome some of the problems of [GraphViewer](https://github.com/STEMS-group/GraphViewer) that I used in project [PortoCityTransfers]({{ site.baseurl }}//projects/porto-city-transfers/).

- **Environment:** Console
- **Tools:** C++, [SFML](https://www.sfml-dev.org/)

Since I was a Teaching Assistant of the subject [Algorithm Design and Analysis](https://sigarra.up.pt/feup/en/UCURR_GERAL.FICHA_UC_VIEW?pv_ocorrencia_id=436441) (CAL) for the second semester of 2021, I suggested to the lecturers that students could use GraphViewerCpp instead of GraphViewer, which the teachers agreed on. Given the success of GraphViewerCpp in replacing GraphViewer, the repository will remain in the public domain and be maintained by the Teaching Assistants of that subject over the following years.

Most of the project was developed while I was on inter-semester vacations and did not yet have a formal arrangement with the University of Porto (as Teaching Assistant of CAL), meaning this project is not covered by that usual contract term stating that *intellectual property developed during the time the contract is valid is property of the University*. As such, the license on the GitHub repository is valid and decided by me as the main holder of intellectual property, making this project public and not-for-profit.

## Why use GraphViewerCpp

This library has significant advantages relative to the old GraphViewer:
- **Similar interface:** its interface allows it to do pretty much the same things that could be done with GraphViewer without adding much complexity on the user side.
- **Written in C++:** this is also the language used in CAL, meaning the library is 100% programmed in the same language the students will be using, and the language the lecturers are most used to (as opposed to GraphViewer, which was mostly written in Java and had a C++ interface that only sent requests over a pipe to the Java process).
- **Better performance:** 2x performance improvement in regular use cases, x100 performance improvement if nodes are omitted and edges are zipped.
- **More flexibility:** because everything is programmed in C++, and since SFML is a very flexible library, it allows maintainers to easily add new features when requested by students.
- **More reliable:** as it involves less mechanisms (does not use the Java virtual machine nor pipes), the only failure points are bugs in the GraphViewerCpp code (presumably not in SFML, as it is widely used and almost completely bullet-proof).
