# nomnaviet-contrib

Community contributions to [Nôm Na Việt (喃哪越)](https://nomnaviet.com) — a platform for Vietnamese Hán Nôm studies.

This repo is the **canonical source** for translations and the **staging area** for character data contributions. Maintainers periodically sync changes back into the main app.

## What's here

| Folder | What | How to contribute |
|---|---|---|
| [`i18n/`](./i18n/) | UI translation files (vi, en, fr, zh) | See [`i18n/README.md`](./i18n/README.md) |
| [`decompositions/`](./decompositions/) | Character component data (IDS) | See [`decompositions/README.md`](./decompositions/README.md) |

More content areas may be added later (e.g. historical dictionary digitization).

## How to contribute

If you're new to GitHub:

1. Click the **Fork** button at the top right of this page.
2. Edit files directly in your fork's web UI (pencil icon on any file).
3. Click **Propose changes** → **Open pull request**.

If you're comfortable with git:

```bash
git clone https://github.com/<your-username>/nomnaviet-contrib.git
cd nomnaviet-contrib
# edit files
git add . && git commit -m "fix: ..." && git push
# then open a PR on GitHub
```

No need to run any code or set up an environment — these are plain JSON and CSV files.

## License

Contributions are released under the same license as the main project. By submitting a PR you agree your contribution may be incorporated into the Nôm Na Việt app.

## Questions

Open an [Issue](../../issues) or email nhatvu148@gmail.com.
