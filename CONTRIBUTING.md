# Contributing

Thank you for helping improve Nôm Na Việt!

## TL;DR

- **Translations**: edit a JSON file in `i18n/` and PR. See [`i18n/README.md`](./i18n/README.md).
- **Character decompositions**: fill rows in a CSV in `decompositions/` and PR. See [`decompositions/README.md`](./decompositions/README.md).

## PR workflow (web UI — no git needed)

1. Click any file → click the pencil icon (✏️ "Edit this file").
2. GitHub will tell you you need to fork the repo. Click **Fork this repository**.
3. Edit in the browser, scroll down to **Propose changes**.
4. Write a short title (e.g. `fix: french plural in caractère trouvé`) and click **Propose changes**.
5. On the next screen, click **Create pull request**.

That's it. You don't need to install anything or run any code.

## PR workflow (git CLI)

```bash
# fork on GitHub first, then:
git clone https://github.com/<your-username>/nomnaviet-contrib.git
cd nomnaviet-contrib
git checkout -b fix/french-plurals
# edit files
git add .
git commit -m "fix: french plural in caractère trouvé"
git push origin fix/french-plurals
# open PR on GitHub
```

## What makes a good PR

- **One topic per PR**: don't mix translation fixes with decomposition data in the same PR.
- **Small is fine**: a single typo fix is welcome. Don't feel like you need to fill a whole CSV.
- **Show your work**: in the PR description, briefly explain *why* (e.g. "this is the standard Hán Việt reading", "found this incorrect when checking against Trần Văn Kiệm").

## Review

Maintainers review PRs as time allows. For data contributions (decompositions, translations), expect a sanity check pass before merge — we may suggest edits or ask questions in PR comments.

## Code of conduct

Be kind and patient. Hán Nôm scholarship has many valid traditions and disagreements; please assume good faith and back up claims with sources where you can.
