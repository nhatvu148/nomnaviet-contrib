# Classifications — A1-G2 character formation

Each Hán Nôm character can be classified by **how it was formed** — borrowed from Hán, compounded from semantic + phonetic parts, etc. This system follows **Nguyễn Quốc Hùng's *Tự Điển Chữ Nôm Dẫn Giải*** (NXB Giáo Dục, 2014). The Nôm Na Việt app currently has classifications for **~7,700 characters**; **~18,000 are blank** awaiting community contributions.

## The codes

| Code | Meaning |
|---|---|
| **A1** | Sino-Vietnamese loan (semantic) — same form, same Hán Việt reading. e.g. `才 tài` |
| **A2** | Sino-Vietnamese loan (semantic) — same form, shifted Vietnamese reading. e.g. `务 mùa` |
| **B**  | Sino-Vietnamese loan (semantic) — pure Vietnamese sound. e.g. `凸 lồi` |
| **C1** | Phonetic loan from Hán — same form, used for sound only. e.g. `没 một` |
| **C2** | Phonetic loan with shifted reading. e.g. `饒 nhau` |
| **D1** | Self-created compound — sound-meeting, equal partners (đẳng lập). e.g. `嶺 lần` |
| **D2** | Self-created compound — sound-meeting, head-modifier (chính phụ). e.g. `邵 trở` |
| **E1** | Self-created compound — meaning-meeting, equal partners. e.g. `兲 trời` |
| **E2** | Self-created compound — meaning-meeting, head-modifier. e.g. `焼 tro` |
| **F1** | Self-created phono-semantic compound (hình thanh) — equal. e.g. `燊 trăm` |
| **F2** | Self-created phono-semantic compound — head-modifier. e.g. `怙 ghét` |
| **G1** | Self-created single component — phonetic only. e.g. `帯 nào` |
| **G2** | Self-created single component — semantic only. e.g. `女 đỉ` |

See [`example-classifications.csv`](./example-classifications.csv) for a few canonical examples in CSV format.

## Files

| File | Purpose |
|---|---|
| `character-classifications.csv` | **Main contribution target.** ~25,827 rows, one per character. The `code` column is filled where known, blank where not. |
| `example-classifications.csv` | Small reference set showing the format. |

## How to contribute

1. Open `character-classifications.csv` in Google Sheets or Excel (it's UTF-8 CSV).
2. Filter or sort to find rows with **blank `code`** — those are the contribution targets.
3. Fill in a **valid code** (one of: `A1`, `A2`, `B`, `C1`, `C2`, `D1`, `D2`, `E1`, `E2`, `F1`, `F2`, `G1`, `G2`).
4. Optionally add a short `note` (free text — your reasoning, source, or quick gloss like *"phonetic borrow from MA"*).
5. Save the file (export as CSV, UTF-8) and submit a PR.

You can fill 5 rows or 5,000 — even small contributions are valuable.

### What if you want to **correct** an existing classification?

If you believe a code is wrong (e.g. tdcndg labeled it F2 but you think it's actually D1), just change the value. PR diffs make corrections easy to review.

## Format details

Columns:
- `character` — the character itself (do not change)
- `unicode` — e.g. `U+6D77` (do not change)
- `type` — `han` / `nom` / `both` (do not change)
- `stroke_count` — (do not change)
- `radical` — (do not change)
- `code` — **edit this**: A1–G2 or `B`
- `note` — **edit this**: free-text notes for your contribution

## Tips for getting the code right

- **Look at the structure first.** Phono-semantic compounds (F1/F2) have one component that hints at sound and another that hints at meaning. e.g. `海 = 氵 (water-meaning) + 每 (MOI-sound)` → C1 if borrowed wholesale, F2 if Vietnamese-coined.
- **Sino-Vietnamese loans (A/C)** are when the *whole character* is borrowed from Hán — distinguish A (kept its meaning) from C (used for sound only).
- **Self-created (D-G)** means the character was invented in Vietnam to write a Vietnamese word, often by combining or repurposing existing components.
- **When in doubt**, leave a note explaining your reasoning so reviewers can sanity-check.

## After your PR is merged

A maintainer runs `task converter:classifications:apply` (which reads this CSV) and the new codes land in the live database. Users will see them on character pages with the explanatory popup.

## Source

Code system from: **Nguyễn Quốc Hùng** — *Tự Điển Chữ Nôm Dẫn Giải*, NXB Giáo Dục, 2014. The visual decision tree is rendered in the app at [the classification popup](https://nomnaviet.com/vi/character/海).
