# Journal

New findings land here first, then move to the page they belong on. Newest at the top.

---

## 2026-09-10 — the site went bilingual

Georgian stays primary; English lives at `/en/`. `mkdocs-static-i18n` with suffix
structure, `fallback_to_default` on so nothing 404s while pages are still being translated.

Custom domain **fiber.qgis.ge** — deliberately not `fiberq.`, because half this site is
general FTTH material that has nothing to do with the plugin, and because `fiberq.` could
be mistaken for the official FiberQ site.

**Order matters when adding a custom domain:** DNS record first, `docs/CNAME` second. Do it
the other way round and GitHub Pages switches to the custom domain immediately, redirecting
the working `github.io` URL to a name that does not resolve yet.

---

## 2026-09-10 — the site was set up

MkDocs + Material. **Zensical was not chosen**: 0.0.60, `Development Status :: 3 - Alpha`,
still 0.0.x after ten months. Material for MkDocs is in maintenance mode but stable, and
`ka` is among its 69 UI languages. Zensical reads `mkdocs.yml`, so migrating later will be
easy.

**Search limitation:** lunr-languages does not support Georgian — no stemming, so `ბოძი`
will not match `ბოძის`. That is why the glossary is keyed on the English term.

**A trap that nearly slipped through:** MkDocs' default slugify strips non-ASCII, which
would have turned every Georgian heading into `_1`, `_2` and broken all the anchor links.
Fixed with `pymdownx.slugs.slugify`.

---

## 2026-09-09 — the `latent elements` answer was already written

I asked the maintainer what `List of latent elements` meant — but the answer was in the
catalogue's own `<extracomment>`. The cause: when preparing the glossary I read the notes
in the UI-group contexts but not those in `FiberQPlugin`.

→ **Latent element**: a passive element sitting on a cable's path at a recorded distance
along it, stored as data rather than drawn as a separate map feature.

**Rule adopted:** read all the notes first, then ask questions.

---

## 2026-09-09 — `Color catalog` is not symbology

In a QGIS context "Color catalog" reads naturally as a colour palette. It is in fact the
**fibre colour code** — the TIA-598/IEC sequence identifying every tube and fibre in a
cable.

**To check:** which standard does FiberQ use, TIA-598 or IEC? I have not looked at the code
yet.

---

## 2026-09-09 — a counting error, and the correction

`<message numerus="yes">` elements were not matching my count. The catalogue has **306**
strings, not 293. Since the wrong numbers were already published in issue #43, a correction
was posted.

---

## 2026-09-09 — no language is actually translated

`fiberq_fr.ts` — 0/306. `fiberq_sr.ts` — 3/306 (test strings). The maintainer is Serbian and
has not translated his own language either.

Georgian will be the **first real translation**. That means the i18n pipeline has never been
exercised on a live catalogue, so the first one will surface problems. I found the first
already: `_LANGUAGE_NAMES` has no `ka` entry.

---

## 2026-09-09 — `Object` means building

The most consequential terminology finding. FiberQ's `Object` renders the legacy Serbian
`objekat` and means a **building** — confirmed by the layer it writes to (floors, basement
levels, street, house number).

Meanwhile Georgian QGIS translates *feature* as `ობიექტი`.

→ `Feature → ობიექტი`, `Object → შენობა`. Counter-intuitive, but correct.

---

## Template for a new entry

```markdown
## Date — title

What I worked out, or what I got wrong.

**Source:** code / `<extracomment>` / documentation / my own inference

**To check:** …
```
