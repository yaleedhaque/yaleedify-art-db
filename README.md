# yaleedify-art-db

Community line-art stories for [yaleedify](https://github.com/yaleedhaque/yaleedify).

Each file is one song. The app fetches it from

```
https://raw.githubusercontent.com/yaleedhaque/yaleedify-art-db/main/songs/<song_id>.json
```

and draws it in the extended player, in sync with the track. Art is tiny — a whole song is
15–150 KB of SVG path data, not video.

## Contributing a song

1. Get synced lyrics: <https://lrclib.net> (free, no key).
2. From the app repo, run the generator:

   ```bash
   cd yaleedify/tools/story-art
   ./generate_song_art.py --lrc song.lrc --title "Song" --artist "Artist" --out songs/ --preview
   ```

3. Open `songs/<song_id>.html` and look at every scene.
4. Delete the scenes that are unrecognisable, blank or blobby; re-time the rest by editing
   `time_ms` if the story lags the vocal.
5. Open a pull request with the JSON file only.

The format, the exact song-id rules and the quality checklist are in
[`docs/STORY-ART.md`](https://github.com/yaleedhaque/yaleedify/blob/main/docs/STORY-ART.md).

## Rules

- One file per song, named by the song id the app derives from the tags.
- No text, no borders, no watermark in the art.
- The drawing must read without the lyric underneath it.
- Files that fail the checklist are not merged; failing gently is the whole point of the player's
  silent fallback, but a bad scene is worse than no scene.

## Licence

Art contributed here is released under CC0. The generator and the player are MIT.
