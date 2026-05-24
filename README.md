# wellworth-progress

Canonical home for **`misc/progress.md`** — the WellWorth project journal.

## Why this repo exists

`progress.md` is updated on every PR per [SPECS §31 — Progress Tracking Contract](https://github.com/wellworthwp/wellworth-progress/blob/main/misc/progress.md). The 9 product repos each run a [`progress-check@v1` composite action](https://github.com/wellworthwp/.github/tree/main/.github/actions/progress-check) on every PR; that action **shallow-clones this repo** to determine whether `misc/progress.md` was touched in the PR's lifetime.

Putting `progress.md` in its own repo (rather than each product repo) keeps the canonical source single — no sync drift, no rebase fights — while the umbrella keeps every existing path reference intact via a symlink (`wellworth/misc/progress.md` → `../wellworth-progress/misc/progress.md`).

## Editing

Edit through the umbrella's path; the symlink resolves transparently:

```bash
# In the umbrella (~/Developer/BUSINESS/wellworth):
$EDITOR misc/progress.md            # writes through the symlink to here
pnpm run progress:save -- "T015 …"  # commits + pushes from this repo
```

Or edit directly inside this clone — both flows write to the same file.

## Bootstrap on a fresh machine

This repo is cloned as a **sibling** of the umbrella's other product repos. From the umbrella root:

```bash
git clone git@github.com:wellworthwp/wellworth-progress.git
# The umbrella's misc/progress.md symlink starts resolving immediately.
```

If you forget, `pnpm run spec:lint` from the umbrella will fail with a "broken symlink" error (see `DEV-SETUP.md §3.7`).

## License

MIT — see [LICENSE](./LICENSE). The progress journal is intentionally public; it's part of WellWorth's [Moat 4 transparency](https://wellworth.org/about/transparency/) commitment.

## See also

- Composite action: [wellworthwp/.github](https://github.com/wellworthwp/.github)
- Engineering rules: [umbrella `misc/RULES.md`](https://github.com/wellworthwp/wellworth-progress/blob/main/) *(currently in the umbrella; may move here in a later split)*
- Per-task plan: [umbrella `misc/FULL-MASTER-PLAN.md`](https://github.com/wellworthwp/wellworth-progress/blob/main/) *(same)*
