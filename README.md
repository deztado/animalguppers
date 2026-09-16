# animalguppers.com

Link hub for **Animal Guppers** — original animated shorts by Deztado.
Static site, served by GitHub Pages.

## Changing the site

Everything you'd normally want to change lives in one block at the bottom of
`index.html`, marked `EDIT HERE`:

- `SITE.title` / `SITE.byline` — the headline and credit line
- `SITE.facts` — the bulleted line in the footer
- `SITE.channels` — each platform's name, handle and URL
  (`state: "soon"` greys one out as COMING SOON)
- `VERSIONS` — the rotating versions. Each has its own palette, eyebrow text,
  background video and music track. Visitors advance one version per visit.
  Set `scrim: "heavy"` on a version whose footage is bright behind the text.

Edit that block on GitHub, commit, and the live site updates in about a minute.

## Adding video or music

Source clips must be transcoded first — the site ships video around 1–3 MB and
audio around 3 MB. Dropping in a raw 25 MB file will make the page crawl.

```
ffmpeg -i in.mp4 -an -vf scale=1280:-2 -c:v libx264 -crf 31 -preset slow \
       -pix_fmt yuv420p -movflags +faststart assets/v-name.mp4
ffmpeg -i in.mp3 -vn -c:a libmp3lame -b:a 104k assets/a-name.mp3
```

## Notes

- `CNAME` sets the custom domain. Don't delete it.
- Audio cannot autoplay before a visitor interacts — browsers block it.
  The page starts the track on the first tap or key press, and the header
  button shows the state.
