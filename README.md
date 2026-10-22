# lunarfizztransport.github.io

**Live site: [lunarfizztransport.github.io](https://lunarfizztransport.github.io)**

The home for my creative work and side projects: hand-cut paper collages (some
paired with short stories and poems I wrote) and tech projects like the
[Drum Groove Tool](https://github.com/lunarfizztransport/drum-groove-tool).
It's a snapshot of who I am and how I'm bridging technology with the things I
love.

The site looks like a late-90s computer desktop: pixel icons open draggable
windows, open windows appear in a taskbar at the bottom, and the **LF** Start
button opens a menu of every window and link. On phones, windows open full
screen with larger buttons, and the Start menu is the way to get around.

## What's on it

| Window | What it shows |
|---|---|
| **Collages** | A file browser of my collages. Click one to open it in a viewer with its date, size and description. Collages with a story or poem show a **Read the story / poem** button that opens the writing in its own text window. |
| **Drum Groove Tool** | A practice tool I built while learning drums. The **About** tab describes it, with demo pages it made from my own playing: how it learned my kit, a take analyzed, and the same take with AI coaching. The **Try it out** tab runs it right in the window: record yourself against a click (or upload a phone recording, or play an e-kit over USB) and see whether you rush or drag, how consistent you are, which drum is early or late, and how much you swing. Optional coaching from Claude with your own API key. Also at [/drums/](https://lunarfizztransport.github.io/drums/). |
| **Vigenère Cipher** | Encrypt and decrypt text with the classic Vigenère cipher, live as you type. Shows how each key letter lines up with the message. Runs entirely in the browser. |
| **Cue Coach** | A pool strategy trainer. Pick 8-ball or 9-ball, call your shot (ball, pocket, spin, speed, or a safety), and a coach that simulates every option grades your call and shows what it would play and why. Also at [/pool/](https://lunarfizztransport.github.io/pool/). |
| **About.txt** | What this site is about. |
| **Instagram / GitHub** | Links out. |

Direct links to a window: [#collages](https://lunarfizztransport.github.io/#collages),
[#drums](https://lunarfizztransport.github.io/#drums),
[#vigenere](https://lunarfizztransport.github.io/#vigenere),
[#pool](https://lunarfizztransport.github.io/#pool),
[#about](https://lunarfizztransport.github.io/#about).

## How it's built

A single static page with no build step and no framework, hosted on GitHub
Pages. Pushing to `main` publishes it within a minute or two.

```
index.html          the whole site: layout, styles and window manager
data/pieces.json    the collages: image, title, date, size, description, story or poem
data/site.json      site settings: my name and Instagram handle
images/             collage photos
drums/index.html    Drum Groove Tool, embedded by its window; with drums/groove.js, a copy of web/ from github.com/lunarfizztransport/drum-groove-tool
drums/demo*, kit/   demo pages the Python version made from my playing, and their audio
pool/               Cue Coach, shown in its window: index.html, plus manifest.webmanifest, sw.js and icons/
                    so it installs as an app; a copy of github.com/lunarfizztransport/pool-coach
.pages.yml          Pages CMS configuration for editing collages in a browser
```

- **Fonts:** Silkscreen, VT323 and IBM Plex Mono from Google Fonts.
- **Pixel art:** the desktop icons and the cursors (an arrow with a little
  sparkle, and a pointing hand) are inline SVG, drawn pixel by pixel.

## Adding or editing collages

The easiest way is **[Pages CMS](https://app.pagescms.org)**: sign in with
GitHub, open this repo, and choose **Collages**. Each collage has these fields:

- **Photo, Title, Date, Size, Materials, Cut from, Description**
- **Feature this one at the top of the site:** puts it first in the grid
- **Short story:** optional; adds a "Read the story" button. Blank lines become paragraph breaks
- **Is the writing a story or a poem?:** changes the button to "Read the poem" and the tag to "+ poem"
- **Note under the story title:** e.g. *Inspired by Robert Frost*

Saving in Pages CMS commits to this repo, and the site updates on its own.

You can also edit `data/pieces.json` directly. A collage with a poem looks like
this:

```json
{
  "image": "/images/ice-terraces.jpg",
  "title": "Untitled 3.0",
  "year": "April 2026",
  "size": "5 × 16 in",
  "description": "This world shrinks into a speck.",
  "story": "Whose barn this is I think I know.\nThey live out on the tranquil snow.\n...",
  "story_type": "poem",
  "story_note": "Inspired by Robert Frost",
  "featured": false
}
```

## Adding a side project

Each project is a window. In `index.html`:

1. Copy the Drum Groove Tool `<section class="win raised" id="w-drums">` and
   give it a new `id` (e.g. `w-myproject`) and `data-title`.
2. Add a desktop icon (a `<button class="icon" data-open="w-myproject">`) in
   the `.icons` list.
3. To link straight to it, add it to the `map` in the `start()` function at the
   bottom of the page (e.g. `myproject: "w-myproject"` makes `#myproject` work).

## Preview locally

The page loads its collages from `data/`, so open it through a local web
server rather than double-clicking the file:

```bash
python3 -m http.server 8765
```

Then visit <http://localhost:8765> and press Ctrl+C in the terminal when done.

## Prints and commissions

Open. Message me on Instagram at
[@lunarfizztransport](https://www.instagram.com/lunarfizztransport/).

The collages, stories and poems are my original work; please ask before reusing
them.
