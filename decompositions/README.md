# Decompositions — character component data

Character decomposition data using **IDS (Ideographic Description Sequence)** notation, the same format used by [cjkvi-ids](https://github.com/cjkvi/cjkvi-ids) and Unicode.

The Nôm Na Việt app uses this data to power:

- **Component search** — find characters by their parts (e.g. find all chars containing 氵).
- **Reverse lookup** — show all characters that share a phonetic element (e.g. all chars built on 㝵).
- **Phono-semantic patterns** — help learners recognize that characters sharing a phonetic component often sound similar.

## Files

| File | Purpose | Size |
|---|---|---|
| `example-decompositions.csv` | Hand-curated examples — **read this first** | ~16 rows |
| `missing-decompositions.csv` | Characters with no decomposition data — main contribution target | ~1,600 rows |
| `partial-decompositions.csv` | Characters with broken decomposition data (placeholder refs like `①②③`) — quick fixes | ~125 rows |

## Column reference

| Column | Description |
|---|---|
| `Character` | The character itself (do not change) |
| `Unicode` | e.g. `U+6D77` (do not change) |
| `Type` | `han`, `nom`, or `both` (do not change) |
| `StrokeCount` | (do not change) |
| `Radical` | Existing Kangxi radical, if known (do not change) |
| `CurrentIDS` | Existing decomposition (only set in `partial-decompositions.csv`) |
| `Structure` | IDS structure operator: `⿰` `⿱` `⿲` `⿳` `⿴` `⿵` `⿶` `⿷` `⿸` `⿹` `⿺` `⿻` `⿼` `⿽` `⿾` `⿿` |
| `Semantic` | Semantic component(s). Use `+` to join multiple (e.g. `日+月`) |
| `Phonetic` | Phonetic component (leave blank for compound ideographs with no phonetic) |
| `Notes` | Free-form. Include the Hán Việt reading of the phonetic if you know it (e.g. "MOI" for 每), the meaning of the semantic, or any caveats |

## IDS structure operators (cheat sheet)

| Operator | Layout | Example |
|---|---|---|
| `⿰` | left + right | 海 = ⿰氵每 |
| `⿱` | top + bottom | 想 = ⿱相心 |
| `⿲` | left + middle + right | 街 = ⿲彳圭亍 |
| `⿳` | top + middle + bottom | 衷 = ⿳亠中𧘇 |
| `⿴` | full enclosure | 國 = ⿴囗或 |
| `⿵` | top-bottom-left enclosure | 問 = ⿵門口 |
| `⿶` | bottom enclosure | 凶 = ⿶凵㐅 |
| `⿷` | left enclosure | 區 = ⿷匚品 |
| `⿸` | top-left enclosure | 病 = ⿸疒丙 |
| `⿹` | top-right enclosure | 句 = ⿹勹口 |
| `⿺` | bottom-left enclosure | 起 = ⿺走己 |
| `⿻` | overlaid | 坐 = ⿻土从 |

Full reference: [Wikipedia — Ideographic Description Characters](https://en.wikipedia.org/wiki/Chinese_character_description_languages#Ideographic_Description_Sequence).

## Phonetic vs. semantic — how to decide

Most Hán characters are **phono-semantic compounds (形声字)**: one component carries meaning (semantic / signific / radical-like) and the other suggests pronunciation (phonetic).

Heuristics:

- The **semantic** is usually the radical or a meaning-related component — water (氵) for water-related characters, heart (心) for emotion-related, etc.
- The **phonetic** is the component that other characters with similar Sino-Vietnamese readings share. If you see 馬 (MÃ) in a character read MÃ, MA, MẠ, that's almost certainly the phonetic.
- For **compound ideographs** (会意字) like 明 (sun + moon = bright) or 林 (two trees = forest), there is no phonetic — leave that column blank, list both components in `Semantic` joined with `+`.
- For **purely phonetic borrowings** in Nôm (where a Hán character is borrowed only for its sound), the entire character may be phonetic with no semantic — note this in the `Notes` column.

When in doubt, leave a column blank and explain in `Notes`. A "best guess + reasoning" is more useful than nothing.

## Atomic characters

If a character has no meaningful decomposition (it's an atomic component itself, like 一, 人, 日, 月), **skip it** — leave the row as-is or delete it. These will be handled separately as components rather than decompositions.

## How to contribute

1. Pick one of the CSVs.
2. Edit it in any spreadsheet program (Google Sheets, Excel, Numbers) or directly in GitHub's web UI.
3. **Important — when saving from a spreadsheet, export as UTF-8 CSV** so Hán Nôm characters survive.
4. Submit a PR with your changes — even partial fills are welcome (1 row or 100 rows, no minimum).

## After your PR is merged

Maintainers will review and merge the data into the app's `characters` table after a sanity check. You'll see your contributions live in the next data refresh.
