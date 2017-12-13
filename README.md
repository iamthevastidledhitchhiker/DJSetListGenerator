# Bergiza Bot

DJ setlist generator using Spotify audio features data

Link to setlists: https://soundcloud.com/bergizabot/sets

## Installation
`pip install -r requirements.txt`


## Generating set lists

### Spotify API

The `SetListGenerator_Spotify` class is the primary component to drive
track generation. It can be found within 'SetlistGenerator_SpotifyAPI.ipynb'

```python
d = SetlistGenerator_Spotify(seed_tracks=[list_of_track_ids],
                             seed_genres=[list_of_genres],
                             seed_artists=[list_of_artist_ids])
```

When running the script for the first time, a webpage will be opened
under the localhost domain. Copy and paste the URL into the prompt to
authenticate with the Spotify API

#### Ex. 1 Generate a 10-track set from Aphex Twin's track 'Donkey Rhubarb'

```python
d = SetlistGenerator_Spotify(seed_tracks=['0c0PhGTdl4K1SRWu0kYkBh'],
                             seed_genres=['minimal-techno', 'techno'])

while len(d.set_list) < 10:
   d.getNextTrack()
   d.changeSeedTracks()
   d.expandTrackPool()

d.set_list
```

### Other methods
As of V_0_0_9, the generator does not utilize mass data scraped from MixesDB,
Discogs, or Spotify. The additional .ipynb files are included for posterity's sake.
