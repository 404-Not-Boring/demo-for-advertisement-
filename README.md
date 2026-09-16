# Digital Wedding Invitations — Demo Site

Two interactive invitation templates, plus a landing page. Pure HTML/CSS/JS, no build step, no dependencies.

## Files

| File | What it is |
|---|---|
| `index.html` | Landing page linking to both demos |
| `classic.html` | Maroon & gold theme — curtain reveal, countdown, maze game |
| `beach.html` | Seaside theme — cabana curtain reveal, countdown, drag-and-drop photo puzzle |

## Deploying to GitHub Pages

1. Create a repo and push all four files to the root of the `main` branch.
2. In the repo go to **Settings → Pages**.
3. Under **Source**, pick **Deploy from a branch**.
4. Branch: `main`, folder: `/ (root)`. Save.
5. After a minute the site is live at `https://<username>.github.io/<repo>/`

No `.nojekyll` file is needed since none of the filenames start with an underscore.

## Customising an invitation

Everything you'd normally change is near the top of each file.

**Names** — search for `Karim` and `Lara` and replace throughout (they appear in the hero, the game, and the closing section).

**Date and time** — two places that must be kept in sync:
- the countdown target in the `<script>`: `new Date('2027-06-11T19:00:00')`
- the human-readable text in the details card: `Friday, 11 June 2027`

**Venue and map** — in the details and location sections. The map button uses a plain Google Maps search URL; swap the `query=` value for the real venue name or coordinates.

**Colours** — every colour is a CSS variable in the `:root` block at the top of each file. Change those few values and the whole invitation re-themes.

**Photos** — replace the `src` on the couple's `<img>` tags. For the beach puzzle, change the single `--puzzle-img` variable in `:root` and the puzzle tiles and the faded preview both update.

### Using your own photo files

Put images in an `images/` folder next to the HTML and reference them relatively:

```html
<img src="images/groom.jpg" alt="Karim">
```

```css
--puzzle-img:url('images/couple.jpg');
```

Relative paths like this work correctly on GitHub Pages under a subpath. Use a landscape (roughly 3:2) photo for the puzzle so the tiles crop cleanly.

## Notes

- The current demo photos are hot-linked stock images. Before going live, download the ones you want and serve them from your own repo — hot-linking can break and slows the first load.
- Both pages lock scrolling until the visitor taps the open button, so the reveal always plays first.
- Layouts are capped at 480px wide and centred, so they look right on a phone and don't stretch awkwardly on desktop.
