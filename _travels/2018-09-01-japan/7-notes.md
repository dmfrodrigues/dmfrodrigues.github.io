## Curiosities

The famous urban legend ["Man from Taured"](https://www.ancient-origins.net/unexplained-phenomena/mysterious-tale-man-taured-evidence-parallel-universes-or-embellishment-005788) is set in Japan. On a hot day in July 1954, a man arrived at [Tokyo International Airport](https://en.wikipedia.org/wiki/Haneda_Airport). He was caucasian and had a beard, and could speak at least French and Japanese. As he was passing through customs he reported he was from the country of 'Taured'. As airport officials had never heard of such country, they asked for his documents, all of which looked authentic, although they were issued by the country of Taured. They asked the man where Taured was, to which the man answered it was between Spain and France, and that it had existed for a thousand years. When asked to point at Taured in a map, the man became very angry as his country was labelled 'Andorra'. Fearing the man was a criminal, he was detained and brought to a local hotel while investigations were underway. To prevent him from escaping, two guards were placed at the door, but as they checked on the man in the morning he had simply vanished, as well as all his personal documents. There were no traces of an escape. This urban legend is also mentioned in a song I appreciate very much, [*Dose* by Avenged Sevenfold](www.youtube.com/watch?v=mlG2EK2I9zM).

### Music

Because music is a very important part of a country's culture (and probably the one that more easily reaches a broader audience), here are some Japanese songs I like. They're obviously alternative rock or metal.

As I discover new music mostly via Spotify, there are two things I must mention:
1. I have never seen the videoclips, so there is a good chance they are quite strange. It never really bothered me, as music is good for what it's worth, not just because it has a cool videoclip.
2. For about half of these songs I have never seen the lyrics and its translation. To be honest, I like most of these songs because of the melody, not the lyrics, so I end up saving songs based pretty much on the melody only. That means I have no idea what half of these songs are about 😅.

(Strangely, Girugamesh have been removing their songs from Spotify)

<iframe class="spotify" src="https://open.spotify.com/embed/playlist/6GAkfp0JbAEoqcRkaoH6qt" height="280" allow="encrypted-media"></iframe>

<div class="responsive_row">
	<div class="column">
		{% for band in site.data.music_japan.bands_left %}
		<div class="band">
			<div class="band-name"><img class="inline" src="https://upload.wikimedia.org/wikipedia/commons/7/75/Vinyl_record.svg"> <a href="{{ band.link }}">{{ band.name }}</a></div>
			{% for song in band.songs %}
			<div class="song"><a href="{{ song.link }}">{{ song.name }}</a> <span style="float: right;">({{ song.year }})</span></div>
			{% endfor %}
		</div>
		{% endfor %}
	</div>
	<div class="column">
		{% for band in site.data.music_japan.bands_right %}
		<div class="band">
			<div class="band-name"><img class="inline" src="https://upload.wikimedia.org/wikipedia/commons/7/75/Vinyl_record.svg"> <a href="{{ band.link }}">{{ band.name }}</a></div>
			{% for song in band.songs %}
			<div class="song"><a href="{{ song.link }}">{{ song.name }}</a> <span style="float: right;">({{ song.year }})</span></div>
			{% endfor %}
		</div>
		{% endfor %}
	</div>
</div>
