# Multipli.city

> Jekyll code for the Sonic Multiplicities deep-learning music project.

## Functionality

For each new `post`, the following are generated:

* New post on the website
* New episode in the podcast

### /_posts/

This is where new music releases get added.

Each post provides cover art and analyzes the art's colors (using Vibrant) to
draw unique visualizations on both the Wavesurfer waveform, as well as the canvas
background.

#### `post` metadata

Unique `post` metadata is as follows:

```
---
author: # In this case, author = musician
instrument: # Instrument played by the musician
season: # Podcast season, for iTunes podcast network
episode: # Podcast episode, for iTunes podcast network
sidecar: # Sidecar file provides human-readable album metadata in JSON format
# Other homes for this release on the web
apple_music:
bandcamp:
soundcloud:
spotify:
cover: # Square cover art for the release
stream_url: # Streamable remote URL where the release lives
duration: # Duration of the complete release, in seconds
excerpt: # Put the catalog number for the release here, if relevant.
abstract: # Optional front matter to put on the page as the release's "subtitle"
---
```

#### layout: post

Creates a new webpage & podcast item entry for a single track.

Posts may be of type `Composition` or `Reflection`.

#### layout: playlist

Creates a new webpage & podcast item entry for a collection of tracks.

Playlists expect there to be a `post.stream_url` containing a remote URL to all
of the tracks in the playlist, concatenated in the proper order. It also expects
a `post.sidecar` containing a remote URL to a JSON sidecar file with playlist
metadata provided to assist with the Wavesurfer region construction process.

Playlists may be of type `Composition` or `Album`.

### `pages/`

Inside the `pages` directory you may place pages that aren't related directly to publishing music releases. This is where you can add performer bio pages, contact information, etc.

### /podcast.xml

XML template for podcast. Publishes to `/podcast.xml` when jekyll code is built.

## Building

Do `jekyll build -d docs` to re-build your jekyll site into the `docs` directory.

This approach enables your page to be 100% compatible with GitHub Pages, making publishing updates free, reliable, and easy.

## Acknowledgements

Many thanks to [akiritsu](https://github.com/akiritsu) for their outstanding
[pRoJEct-NeGYa](https://github.com/akiritsu/pRoJEct-NeGYa) jekyll template.
Without it, I'd just be another backend nix guy struggling with CSS and JS.
