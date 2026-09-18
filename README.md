# archival haunt

Splash page. Static HTML, no build step, no dependencies.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The whole page. Logo SVG is inlined so CSS can drive the hover. |
| `assets/memo.webp` | The memo scan, 1132×1390. |
| `assets/logo.svg` | Standalone wordmark (default state, white on transparent), for reuse elsewhere. |
| `.claude/launch.json` | Local preview config. |

## The background color

`#000000`, and that is not a guess. The memo's outer margin was sampled
pixel by pixel: solid `(0,0,0)` in all four corners, and 96.5% of the
border pixels. Matching it exactly means the scan's ragged edges dissolve
into the page with no seam or bounding box.

The paper itself is a much lighter green-charcoal, about `#232524` — that
is the value to use if you ever want the background to match the
*document* rather than its margin, at the cost of a visible rectangle
around the image.

## The logo

Two states, taken from the Figma file (`node-id=19-11`) and exported as
vector, so there is no webfont to load and no font to go missing:

- **Default** — wordmark with the hand-drawn strike through it.
- **Hover / focus** — the strike fades out in place, leaving the name
  clean. It does not move; only opacity changes.

Both layers keep the 0.5 Gaussian blur from the source file, which is what
puts the mark in the same soft-photocopy register as the memo.

Honors `prefers-reduced-motion`.

## Running it locally

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173.
