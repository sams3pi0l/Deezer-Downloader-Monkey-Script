# DeezRevived

A Tampermonkey / Violentmonkey / Greasemonkey userscript to download music
from [Deezer](https://www.deezer.com/) in MP3 (128k / 320k) and FLAC.

> Revisited from the original *Deezer:Download* script by several contributors.
> License: Beerware — see the header of `DeezRevived_1.2.js`.

## Features

- Download tracks, albums and playlists from the Deezer web player.
- Choose between **MP3 @128k**, **MP3 @320k** and **FLAC** (configurable).
- Bulk / tracklist downloader.
- Cover art embedding (configurable size & quality).
- Fully local decryption — no external servers handle the audio.
- Multi-language interface (en, de, es, fr, it, pt, pt-BR, ru).

> HQ / HiFi quality requires a Deezer **Premium** subscription. Standard
> quality works without one, depending on your account.

## Installation

1. Install a userscript manager:
   - [Tampermonkey](https://www.tampermonkey.net/) (Chrome, Firefox, Opera, Edge)
   - [Violentmonkey](https://violentmonkey.github.io/) (recommended for Greasemonkey)
2. Open `DeezRevived_1.2.js` and let your manager install it, or copy the
   script contents into a new userscript.
3. Browse to any track, album or playlist on `https://www.deezer.com/`.

## Usage

- Open a track / album / playlist page on Deezer.
- A **Deezer:D➲wnloader** panel appears. Click it, or press the **`D`** key.
- Pick the desired format for each track, or use *Download tracklist* for a
  bulk download.
- Files are decrypted in a Web Worker and saved to your default download folder.

## Configuration

Edit the constants at the top of `DeezRevived_1.2.js`:

| Option             | Default | Description                                  |
|--------------------|---------|----------------------------------------------|
| `showMp3_128`      | `true`  | Show MP3 @128k download                      |
| `showMp3_320`      | `true`  | Show MP3 @320k download                      |
| `showFLAC`         | `true`  | Show FLAC download                           |
| `showListDownloader` | `true` | Show bulk tracklist downloader               |
| `coverSize`        | `600`   | JPEG cover size in px                        |
| `coverQuality`     | `80`    | JPEG cover quality (0–100)                   |

Debug toggles (`SHOW_KEYS`, `DEBUG`, `L10nDEBUG`, `L10nOVERRIDE`) are also
available near the top of the file.

## How it works

- Deezer's encrypted audio is fetched and decrypted in-browser using an
  embedded Blowfish implementation (Web Worker).
- Metadata (ID3 for MP3, Vorbis comments for FLAC) and cover art are written
  locally — no data leaves your browser except the normal Deezer requests.
- A `fetch()` shim captures track info; on Greasemonkey a warning is shown
  recommending Tampermonkey / Violentmonkey.

## Notes

- This script does **not** fetch lyrics (the previous AZLyrics dependency has
  been removed).
- Respect Deezer's terms of service and applicable copyright law in your
  jurisdiction. This project is provided for personal, educational use.
