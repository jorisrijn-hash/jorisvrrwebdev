# Joris VRR, portfolio

One self contained `index.html`. No framework, no build step, no runtime dependencies.
Two web fonts (Archivo, Bodoni Moda) from Google Fonts. Everything else is in the file.

## Deploy

Drop every file in this folder into a repo root and connect it to Vercel. No configuration needed.
The paths in `index.html` assume the site is served from the domain root.

```
index.html
favicon.svg  favicon-32.png  apple-touch-icon.png
icon-192.png  icon-512.png  icon-512-maskable.png
og-image.png  site.webmanifest
```

## Fill these in before it goes live

Everything below is either a placeholder or unverified. Nothing was invented to fill a gap.

1. **`CONFIG` at the top of the script.** Email, GitHub handle, LinkedIn URL, base, what you are
   building now, what you shipped last, availability. Leave `linkedin` empty and both LinkedIn
   links remove themselves.
   The GitHub value needs a decision: your repos are under `jorisrijn-hash`, the wireframe
   document says `jorisvrr`. Pick the one you want public.
2. **Project screenshots.** Every plate has a slot at 16:10. Replace
   `<span class="slot">...</span>` with `<img src="/work/ats.webp" alt="..." width="1600" height="1000" loading="lazy" decoding="async">`.
   Serve WebP at roughly 1600px wide. The slot styling disappears on its own once an image is in there.
3. **Results.** Five `[ ... ]` markers, styled in brass so you cannot miss them, mark every claim
   I could not verify: ATS analytics, BEBO intake numbers and how requests arrived before,
   the CORTEX prototype link. Fill or delete, do not guess.
4. **Client proof.** There is a commented markup block above the footer. It is empty on purpose.
5. **`og:url` and `canonical`** point at `https://jorisvrr.com/`. Change if the domain changes.

## Design system

| | |
|---|---|
| Surface | `--void` #0E120F, warm green black. Raised: `--void-2`, `--void-3` |
| Ink | `--ink` #F1ECE3 ivory, `--ink-2` secondary, `--ink-3` captions |
| Accent | `--brass` #D6B67B, index numbers and one live state. `--cypress` for status dots only |
| Display | Bodoni Moda 500, clamp to 5.25rem max, tracking -0.021em |
| Interface | Archivo. Captions at 0.6875rem, 0.14em tracking, uppercase |
| Motion | `--e-out` expo out. 160ms micro, 240ms UI, 560ms reveal, 620ms panel |

Contrast is verified: every text token clears WCAG AA on every surface it is used on.
`--cypress` is non text only, it clears 3:1 for UI elements.

## Structure

- `.caption` is the voice of the site. It labels artefacts, never headings. Do not turn it into
  an eyebrow above every section, that is the thing this design is avoiding.
- Section names sit on the hairline rule at the right, like a running head in a book.
- Numbers appear only where the content is a real sequence: the five plates, the six process
  steps, the eight case chapters.
- Case studies are static `<article>` elements at the end of the document. With JavaScript they
  become full screen panels. Without it they render as normal sections, so they stay indexable
  and readable. Adding a case means copying one `<article class="case">`, giving it a
  `data-panel` name, and adding `data-case="name"` to a plate link. The chapter rail builds
  itself from the chapter headings.
- The command palette opens with Cmd or Ctrl K. It does not animate, on purpose: keyboard
  actions should feel instant.

## Accessibility and motion

Semantic landmarks, one h1, visible focus everywhere, skip link, `inert` on background content
while a panel is open, Escape closes everything, and full `prefers-reduced-motion` support that
removes the loader and all movement while keeping the site usable.
