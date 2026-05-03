# i18n — UI translations

Translation files for the Nôm Na Việt web app. Each file is a flat JSON with namespaced keys.

| File | Language |
|---|---|
| `vi.json` | Tiếng Việt (Vietnamese) — source of truth for meaning |
| `en.json` | English |
| `fr.json` | Français |
| `zh.json` | 中文 (Traditional Chinese) |

## How to fix a translation

1. Open the file for the language you want to fix (e.g. `fr.json`).
2. Find the entry — keys are usually self-explanatory (`Search.placeholder`, `Character.strokes`, etc.).
3. Edit the value.
4. Submit a PR.

## Plurals and ICU syntax

Some strings have plural forms that can't be handled by simply adding `(s)`. Use ICU plural syntax:

```json
"resultsFound": "{count, plural, =0 {Aucun caractère trouvé} =1 {1 caractère trouvé} other {# caractères trouvés}}"
```

Compare to the equivalent English entry:

```json
"resultsFound": "{count, plural, =0 {No characters found} =1 {1 character found} other {# characters found}}"
```

If you spot strings that currently show `(s)` markers and want to convert them to proper plurals, please flag them in your PR description so the corresponding code change can be coordinated.

## Diacritics

Vietnamese and French diacritics matter. Common issues to watch for:

- French: `caractère` (not `caractere`), `composé` (not `compose`), `trouvé` (not `trouve`).
- Vietnamese: tone marks must be on the correct vowel; check both old-style and new-style placement is consistent across the file.

## What NOT to translate

- Keys (left side of `:`).
- Placeholders inside `{...}` like `{count}`, `{character}` — keep them exactly as-is.
- Hán Nôm characters embedded in example strings.

## After your PR is merged

Maintainers periodically sync this folder back into the main app's `apps/web/messages/` directory and ship it in the next release.
