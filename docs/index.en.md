# FiberQ in Georgian

A **study notebook**, not a manual. This is where I write down what I learn about
[FiberQ](https://github.com/vukovicvl/fiberq) and about fibre network design — one term,
one button at a time.

!!! info "Who is writing this, and why"
    I come from the GIS and QGIS-plugin side and am **not a fibre specialist**. That is
    precisely why this site exists: whatever I work out stays here so I do not have to
    work it out twice. If something is wrong, that is a bug —
    [open an issue](https://github.com/kapo-Toolkits/fiberq-ka/issues) or edit the page.

!!! note "About this English edition"
    Georgian is the primary language of this site. Pages that do not have an English
    version yet fall back to the Georgian text, so nothing 404s — you will simply land on
    a Georgian page. Fully translated so far: this page, the
    [glossary](glossary.md) and the [translation project](translation/index.md).

    The glossary is the page most likely to be useful to an English reader: it is the
    English → Georgian terminology reference prepared for the FiberQ catalogue.

---

## What this is for

FiberQ is an open-source QGIS plugin for designing FTTH/GPON/FTTx networks, by
**Vladimir Vukovic**, GPL-3.0-or-later, funded by the NLnet NGI0 Commons Fund.

This site accompanies the **Georgian translation** of its interface — 306 catalogue
strings — and collects the domain knowledge needed to do that translation honestly.

## Translation status

| | |
|---|---|
| Upstream issue | [vukovicvl/fiberq#43](https://github.com/vukovicvl/fiberq/issues/43) — open |
| Catalogue | `fiberq/i18n/fiberq_ka.ts` — **does not exist yet** |
| Drafted | **306 / 306 strings (100%)** |
| Waiting on | the maintainer to generate the empty `.ts` file |

Georgian will be FiberQ's **first real translation**: the French catalogue has 0 of 306
strings filled in, the Serbian one has 3.

[:octicons-arrow-right-24: The translation project](translation/index.md)

---

## Three things the translator notes taught me

The FiberQ catalogue carries 95 `<extracomment>` notes written by the maintainer. They
are not decoration — three of them changed terms I would otherwise have got wrong:

**`Object` means *building*.** It renders the legacy Serbian `objekat`. Georgian QGIS
already translates the GIS term *feature* as `ობიექტი` — literally "object" — so the
obvious translation would have been wrong in about ten strings.

**`Route` is the physical alignment on the ground**, not a travel route and not a file
path. Georgian has a dedicated engineering word for this, `ტრასა`.

**`Cut infrastructure` is geometry editing, not a fault.** The fault concept is a
separate string, `Fiber break`. Georgian keeps the two lexically apart.

## How this site grows

1. **Every term is keyed on its English name.** English is the working language of the
   field, and site search depends on it — Georgian has no stemmer in lunr, so
   `ბოძი` will not match `ბოძის`.
2. **Sources are always named.** Where a definition comes from FiberQ's code or from a
   maintainer's `<extracomment>`, it says so. Where it is my own inference, it says that
   too.
3. **Doubt stays visible.** An unsettled term is marked, not smoothed over. A wrong term
   that looks finished does more damage than an open question.
