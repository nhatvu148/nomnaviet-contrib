# Variants — Unicode-codepoint dị thể (異體字)

Variant character pairs where multiple Unicode codepoints have historically been used to write **the same Vietnamese word**.

The Nôm Na Việt app uses this data to surface alternate forms on every character page — under the "Dị thể (異體字)" row — so readers of manuscripts and printed Nôm texts can recognize that, e.g. **徃** and **往** are the same word `vãng`.

## Why this needs human contribution

Unicode's [Unihan database](https://www.unicode.org/charts/unihan.html) provides a lot of variant data (`kSemanticVariant`, `kZVariant`) for **Hán** characters — about 4,300 pairs that the app already imports automatically. But Unihan is **Sinophone-centric**: it does not capture Vietnamese scribal variation.

In particular, the gap is huge for:

- **Pure-Nôm characters** (the Vietnamese-invented ones, character_type=`nom`): only **2.3%** currently have any variant data
- **Mixed-use characters** (used as both Hán and Nôm): only **35%** covered
- **PUA-range Nôm characters** (U+F0000–U+FFFFD): essentially zero coverage from Unihan

This kind of knowledge — recognizing that the scribe of a particular woodblock used `㑹` where the modern dictionary form is `會` — sits in the heads of paleographers, classicists, and serious Nôm readers. Crowdsourcing it is the only realistic path.

## Files

| File | Purpose | Size |
|---|---|---|
| `example-variants.csv` | Hand-curated examples — **read this first** | ~30 rows |
| `missing-variants.csv` | All Nôm + mixed-use characters with **no variant data yet** — main contribution target | ~15,000 rows |

`missing-variants.csv` is **not a list of confirmed variants** — it's a list of characters that *might* have variants. Most rows will end up with empty `Canonical` / `CanonicalUnicode` because the character simply doesn't have a known variant; that's fine, leave them blank. **Only fill in rows where you know a real variant pair.** Don't guess.

## Column reference

| Column | Description |
|---|---|
| `Variant` | The rarer / non-standard / scribal form (the codepoint that "points to" the canonical) |
| `VariantUnicode` | e.g. `U+5F83` (do not change after filling) |
| `Canonical` | The canonical / standard form |
| `CanonicalUnicode` | e.g. `U+5F80` (do not change after filling) |
| `Reading` | Shared Vietnamese reading (Hán Việt or Nôm), e.g. `vãng`, `làm`, `phật` |
| `Notes` | Free-form. Source manuscript, period, regional preference, or any caveat |

## What counts as a variant pair

A pair belongs here if **both codepoints encode the same Vietnamese word** — i.e. a scribe writing one is producing the same lexical item as a scribe writing the other. Examples:

- **徃 ≡ 往** (`vãng`, "to go") — 徃 is an older / abbreviated form of 往
- **㑹 ≡ 會** (`hội`, "meeting") — 㑹 is a common scribal shortcut for 會
- **𫜵 ≡ 爫** (`làm`, "to do") — Nôm characters where the same word was written two different ways
- **戦 ≡ 戰** (`chiến`, "war") — the first is a Japanese-style simplification but appears in Vietnamese woodblocks

A pair does **not** belong here if:

- The two characters are related but mean different things (e.g. share a phonetic but encode different words) → use the [`decompositions/`](../decompositions/) folder to record component sharing instead
- One character is a *radical positional variant* of the other (e.g. 水 / 氵) — those are radical forms, not lexical variants
- The relationship is already in Unihan (`kSemanticVariant` / `kZVariant`) — those are imported automatically. Check by searching the character in the app: if "Dị thể" already shows the variant, no need to add it here. Use this folder for **Vietnamese-specific** pairs Unihan misses.

## Convention

By convention, the **first column** (`Variant`) is the *rarer* or *less standardized* form, and the **second column** (`Canonical`) is the more common / dictionary-headword form. The app uses this convention to auto-generate "Biến thể của <canonical>" meanings on the variant character's page.

## How to contribute

1. Open `example-variants.csv` in any spreadsheet program (Google Sheets, Excel, Numbers) or directly in GitHub's web UI.
2. Add new rows at the bottom — one variant pair per row.
3. **Important — when saving from a spreadsheet, export as UTF-8 CSV** so Hán Nôm characters survive. Extended-plane chars (U+20000+) are particularly easy to corrupt.
4. Submit a PR with your changes — even one row is welcome.

## How to find the Unicode codepoint

If you don't know the codepoint of a character:

- In the Nôm Na Việt app, every character page shows `U+XXXX` in its header. Quickest way.
- Online: <https://www.unicode.org/charts/unihan.html> → "Lookup."
- Command line: `python3 -c "print(hex(ord('徃')).upper())"` → `0X5F83`.

## After your PR is merged

Maintainers review each pair (variant relationships can be subtle — a wrong pair pollutes the dictionary). After review, contributions are appended to `apps/api/src/data/han-nom-variants.json` in the main app and re-seeded into the database. You'll see your pairs live on the app's "Dị thể" row in the next data refresh.

## Questions

Open an [Issue](../../issues) on this repo, or email nhatvu148@gmail.com. Especially welcome:

- Suggestions for which **regional** Vietnamese scribal traditions are underrepresented
- Pointers to **printed sources** (woodblock collections, regional dictionaries) where variant pairs are documented
- Disagreements about whether a particular pair belongs here vs. in `decompositions/`
