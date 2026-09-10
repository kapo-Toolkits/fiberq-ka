# The three rules

FiberQ's `docs/TRANSLATING.md` calls these three rules *inviolable*. Breaking any of them
happens **silently** — there is no error message.

---

## Rule 1 — never change `<source>`

The English text is the **lookup key**. The running plugin asks for the translation of that
exact phrase.

```xml
<!-- correct -->
<source>Place Manhole</source>
<translation>ჭის განთავსება</translation>
```

```xml
<!-- wrong — this string will never be translated again -->
<source>ჭის განთავსება</source>
<translation>ჭის განთავსება</translation>
```

One character — even a stray space — and the phrase quietly reverts to English.

!!! tip "If you spot a mistake in the English"
    That is a real and useful find — but it is fixed with an issue, not by editing the
    `.ts` file.

---

## Rule 2 — placeholders must survive exactly

Markers in curly braces that the plugin replaces with real values at runtime.

They must appear in the translation **exactly as in the English** — braces and all, in
lowercase. You may **move** them; you may not rename, translate or drop them.

```
source:      Imported {count} points into layer '{layer}'!
✅ correct:  '{layer}' შრეში იმპორტირებულია {count} წერტილი!
❌ wrong:    '{შრე}' შრეში იმპორტირებულია {რაოდენობა} წერტილი!
❌ wrong:    შრეში იმპორტირებულია წერტილები!
```

!!! danger "A dropped placeholder is worse than an untranslated string"
    The plugin can raise an error when it tries to fill it in. The code even guards against
    this — `safe_format()` falls back to the English source if the translation cannot be
    formatted. But then the user sees an English label.

### Georgian and case endings

The most frequent trap for us. The suffix sits **outside** the braces:

| Case | Example |
|---|---|
| Adverbial ("in") | `'{layer}'-ში` |
| Dative ("for") | `{crs}-სთვის` |
| Genitive ("of") | `ODF-ის` |
| Instrumental ("by") | `{distance}-ითაა` |
| Ablative ("from") | `{target}-იდან` |

The placeholder stays byte-identical and the sentence still declines naturally.

### The 34 placeholders

`{allowed}` `{bound}` `{computed}` `{count}` `{crs}` `{details}` `{distance}` `{expected}`
`{ext}` `{features}` `{fid}` `{field}` `{fields}` `{format}` `{km}` `{label}` `{language}`
`{layer}` `{layer_id}` `{layers}` `{list}` `{name}` `{new}` `{old}` `{path}` `{rules}`
`{scope}` `{shortcut}` `{shown}` `{stored}` `{summary}` `{target}` `{tol}` `{total}`
`{value}`

Plus Qt's own **`%n`** counter in the 13 `numerus` strings.

### Other things that must survive

| Element | Example | Why |
|---|---|---|
| `\n` | `Language set to {language}.\n\n…` | Line break |
| `…` (U+2026) | `Add drawing…` | Qt convention: "opens a dialog" |
| `...` (three ASCII dots) | `Export selected...` | The catalogue mixes both styles — copy whichever the source has |
| `:` | `Severity:` | Filter label |
| `;;` | `Images (*.jpg);;All files (*.*)` | Qt file-filter separator |
| `->` | `Project -> Properties -> CRS` | Menu path |

---

## Rule 3 — compile nothing

`.qm` files are the compiled binary catalogues the plugin actually loads. **The maintainer
generates them.**

- In Qt Linguist: **File → Save** ✅
- In Qt Linguist: **File → Release** ❌ **never**
- Only the **`.ts`** goes back

---

## Not rules, but they matter

**Do not submit raw machine translation.** `CONTRIBUTING.md` explains why: engines get
fibre terminology confidently and consistently wrong. Using one as a first draft you then
correct yourself is fine; sending untouched output is not, because it **looks finished and
is unusable**.

**Read the `<extracomment>` before translating.** 95 strings carry a maintainer's note.
They exist because the English alone is ambiguous.

**When in doubt, ask — do not guess.**

> a flagged gap is more useful than a confident wrong term

An untranslated string is visibly English and obviously pending. A wrong term looks
finished, gets copied into later work, ships to users, and misleads the engineers who trust
it.
