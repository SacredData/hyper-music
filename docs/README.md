# jekyll-hypermusic
> A jekyll theme designed to maximize musical independence and enhance musical virtue.

`jekyll-hypermusic` is a jekyll template for the Sonic Multiplicities deep-learning music project's website. It is meant to serve as the project's "home base," while also linking prodigiously to all other places on the web where our music exists in some form or another.

* Aims to implement [OpenGraph](https://ogp.me/), [Schema.org](https://schema.org/), and other protocols for indexing.
* Allows for posting of individual tracks, albums, playlists, and/or videos.
* Provides an Apple-compatible podcast feed so fans can easily follow & download your new content.
* Special content encryption & decryption tools to incentivize patronage models such as Patreon.

## Functionality

For each new music release written to the `_posts` directory, this theme generates the following:

* New post on the website (with cool audio and visualization features!)
* New episode in the podcast (fully automated and compliant with Apple podcast directory)
* Every page has OpenGraph & Twitter metadata in the header (`og:audio`, `og:video`, `og:profile`, `og:music:song`, `og:music:album`, etc.)
* Schema.org data (implementation in-progress: `MusicComposition`, `MusicGroup`, `MusicRecording`, `MusicRelease`, etc.)

### /_posts/

<img src="https://raw.githubusercontent.com/SacredData/pRoJEct-NeGYa/master/assets/img/post_preview.jpg" width="540">

Directory where new music releases are published.

Each `post` or `playlist` in `./_posts/` provides cover art and analyzes the
art's colors (using Vibrant) to draw unique visualizations on both the
Wavesurfer waveform, as well as the canvas background.

#### layout: post

* Creates a new webpage & permalink.
* Creates podcast item entry.
* Generates Scheme.org, OpenGraph, and Twitter card metadata for the release.

#### `post` metadata

There are a lot of properties that can be set for each new `post`. Most are not
optional, so make sure you fill out all of the relevant details before you
publish your website's new front matter.

*For any new performers in a release, make sure you create an accompanying
performer profile page so that there's no 404 when you click on their name.*

##### General metadata

```
---
layout: # Layout to use (`post` for single item, `playlist` for multiple items)
home_btn: # Whether to include "home" button in header; default: true
btn_text: # Whether to include text labels for buttons; default: true
post_list: # "date" for ordering by `page.date`; "category" for `page.category`
sidecar: # Sidecar URL provides human-readable album metadata in JSON format
abstract: # Optional front matter to put on the page as the release's "subtitle"
```

##### Release metadata

```
category: # Type of release - Composition, Album, etc.
author: # In this case, author = musician name (Make a profile for them in `pages/`)
instrument: # Instrument played by the musician (Keep this string consistent)
cover: # Square cover art for the release
stream_url: # Streamable remote URL where the release lives
bin_url: # Optional: Streamable URL for the binaural mix
duration: # Duration of the complete release, in seconds
excerpt: # Put the catalog number for the release here, if relevant.
```

##### Podcast episode settings

If you don't fill out the season and episode for the podcast feed, it will not
be published to the podcast.

```
season: # Podcast season (release year), for iTunes podcast network
episode: # Podcast episode (count, starting from 1), for iTunes podcast network
explicit: # Optional: true/false
```

##### External services metadata for `post`

If the music is available elsewhere online, you can indicate that here. All of
these are optional.

```
# Other homes for this release on the web
apple_music:
bandcamp: # Can be album or single release
discogs:
soundcloud: # Can be playlist or single track
spotify:
vimeo:
youtube: # Can be playlist or video
---
```

##### Video metadata for `post`

When a video is to be included with the post, the following additional metadata
are available to provide:

```
---
video_url: # URI to primary video source (ideally, a DASH manifest.)
video_fallback: # URI to backup video source (ideally, an HLS manifest.)
video_mp4: # URI to an MP4 proxy of the video
video_mkv: # URI to an MKV master asset for the video
video_webm: # URI to WebM proxy of the video
---
```

#### layout: playlist

<img src="https://raw.githubusercontent.com/SacredData/pRoJEct-NeGYa/master/assets/img/playlist_preview1.jpg" width="540">

Creates a new webpage & podcast item entry for a collection of tracks.

Playlists expect there to be a `post.stream_url` containing a remote URL to all
of the tracks in the playlist, concatenated in the proper order. It also expects
a `post.sidecar` containing a remote URL to a JSON sidecar file with playlist
metadata provided to assist with the Wavesurfer region construction process.

Playlists may be of type `Composition` or `Album`.

#### Sidecar JSON file

<img src="https://raw.githubusercontent.com/SacredData/pRoJEct-NeGYa/master/assets/img/playlist_preview2.jpg" width="540">

Playlists require a sidecar file written in JSON describing the different regions
contained within the `post.stream_url`. Users may leverage the
[generateSidecar](https://github.com/SacredData/generateSidecar) script to aid
in the generation of these assets.

Formatting is as follows:

```json
{
  "regions": [
    {
    "id": "Track 1 Title",
    "duration": 100,
    "loop": false,
    "drag": false,
    "resize": false
    },
    {
    "id": "Track 2 Title",
    "duration": 330,
    "loop": false,
    "drag": false,
    "resize": false
    }
  ]
}
```

### `pages/`

Inside the `pages` directory you may place pages that aren't related directly to publishing music releases. This is where you can add performer bio pages, contact information, etc.

#### layout: profile

Profile pages should be created as markdown files inside `pages/`. The following
post metadata may be provided:

```
---
layout: profile
title: # Required; what you want to title the profile page, i.e., "First Last"
firstname: # Required; Person's first name
lastname: # Required; Person's last name
gender: # Optional; See https://ogp.me/#type_profile for more information
twitter: # Optional; twitter handle for the user
instrument: # Required; what instrument they play
image: # Optional; point to an image in `/assets/img/`
permalink: # Required; set it to "/First-Last/", i.e., "/Todd-Smith/"
---
```

### /podcast.xml

XML template for podcast. Publishes to `/podcast.xml` when jekyll code is built.

## Building

Do `jekyll build -d docs` to re-build your jekyll site into the `docs` directory.

This approach enables your page to be 100% compatible with GitHub Pages, making publishing updates free, reliable, and easy.

## Design Philosophy

Building this site has been a learning process for me, so I am building as I go,
as the need for new functionality and features present themselves. So yes, I am
cowboy coding this one.

The hope is that I can figure out all the nuts and bolts for my own purposes,
and then generalize the codebase so that anyone can plug in their cloud, CDN,
branding, metadata, releases, hosting providers, etc., with minimal effort.

If you notice anything I am doing wrong - or could be doing better - I invite
you to create a new GitHub issue. I will be putting the TODOs for this project
into GitHub issues for the time being, myself.

## The Future

Right now, the project as-is works well for my purposes. It needs to be
generalized further before it is an appropriate thing for others to fork.

Even then, this is not the most intuitive interface for musicians that lack the
necessary technical expertise to get up and running quickly. Comfort with the
command line, with bash, and with text editors - not to mention, with the jekyll
project - will be necessary for this template to be used successfully.

For this project to serve the average musician effectively, we will need to make
graphical interfaces and forms which allow users to easily fill in the front
matter and metadata. We'll also need to further automate the generation of all
metadata from the music assets themselves.

### Planned Features

#### Media Functionality

* Live stream/broadcast events
* Automated VOD generation & publishing
* Automated multi-casting
* Live chats

#### External Services

* Submission to other music services via APIs such as Bandcamp & SoundCloud
* Provide new entries in music release databases like Discogs & MusicBrainz
* Generation of acoustic ID & submit to AcousticBrainz (and others)

#### Metadata Tools

* Auto-generate QR codes
* Auto-assign ISRC/ISWC numbers and other barcodes

#### eCommerce

* Payment & licensing backends to facilitate independent licensing transactions
* Merch & special item sales

## Distributed & Decentralized Archives
> A work-in-progress Hypercore project for SM

### Releases

MP3 releases Hyperdrive:
`hyper://0e2d7c08d4d6e13ddc01780d6fb54db09452193863b9b922fe3d9edcd2d79ff2/`

To sync it to your file system:

```sh
$ hyp sync hyper://0e2d7c08d4d6e13ddc01780d6fb54db09452193863b9b922fe3d9edcd2d79ff2/ ./mp3-files
```

### Mix Sessions
> TBD

### Mastering Sessions
> TBD

## Acknowledgements

Many thanks to [akiritsu](https://github.com/akiritsu) for their outstanding
[pRoJEct-NeGYa](https://github.com/akiritsu/pRoJEct-NeGYa) jekyll template.
Without it, I'd just be another backend nix guy struggling with CSS and JS.
