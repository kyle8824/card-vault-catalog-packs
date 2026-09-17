# Card Vault FULL RESTORE pack — 2026-09-17

## Purpose
Restore LIVE `card-vault.grok.me` catalog to the **full** on-disk tree (all years), with Track B stub fills overlaid. **Catalog-only. Preserve Collection. Never invent rows.**

## Hard rules
1. **Catalog data / `/catalog` routes only** — no UI redesign, no shell/chrome changes.
2. **Preserve Collection / inventory exactly** (currently ~131 items).
3. **Never invent checklist rows.** Only ship rows present in this pack.
4. **Restore ALL years** — do **not** publish the current 2005–2007-only sandbox shrink.
5. **Do not Publish** until `public/catalog` contains the full tree (sets-index + set-cards for every year).

## What this pack is
| Source | Role |
| --- | --- |
| `/workspace/card-vault-live-merge-20260915` | Authoritative full sets/cards/sources (15,580 / 1,726,669 before overlay) |
| `/workspace/card-vault-track-b-export-20260917` | Track B Grok Files export (381 / 25,062) — prefer complete over stub |

## TALLY (after overlay)
- **sets_total:** 15580
- **cards_total:** 1748086
- **complete / partial / stub:** 15426 / 5 / 140
- **images_with_url:** 9
- **Track B:** meta upgraded 89; card-replaced sets 161; TB cards written 25062

### Years 2005–2009
- **2005:** 551 sets (544 complete / 7 stub), 107333 cards\n- **2006:** 2131 sets (2124 complete / 7 stub), 171414 cards\n- **2007:** 2763 sets (2756 complete / 7 stub), 201923 cards\n- **2008:** 2476 sets (2476 complete / 0 stub), 207512 cards\n- **2009:** 2383 sets (2382 complete / 1 stub), 161124 cards\n
## Layout
```
card-vault-full-restore-20260917/
  TALLY.json
  RESTORE.md
  LIVE_BUILD_PROMPT.txt          # draft only — do not send until green-lit
  catalog/
    sets.jsonl
    cards.jsonl
    sources.jsonl
    sets-index.json              # live schema
    TALLY.json
  shards/
    MANIFEST.json
    SHARDS.md
    sets-index.json.gz
    sets.jsonl.gz
    sources.jsonl.gz
    cards-pre-1990.jsonl.gz
    cards-1990-1994.jsonl.gz
    cards-1995-1999.jsonl.gz
    cards-2000.jsonl.gz … cards-2009.jsonl.gz
    cards-unknown.jsonl.gz
    cards-ALL.jsonl.gz           # optional single archive (~30MB)
```

## LIVE schema (detected 2026-09-17)
- `GET /catalog/sets-index.json` — set index with `sets[]` + `listed_count`
- `GET /catalog/set-cards/{set_id}.json` — per-set checklist array/object

Build must **assemble** `public/catalog/set-cards/*.json` from the year card shards (group by `set_id`). See `shards/SHARDS.md`.

## Verify after restore (before Publish)
1. Sandbox `public/catalog` has years beyond 2005–2007 (e.g. 2008 Topps Baseball set-cards present).
2. 2006 Topps Baseball + 2007 Topps Baseball checklists non-empty.
3. 2008 Topps Baseball still ~661 cards.
4. Collection still ~131.
5. Index set_count → **~15,580** (or live 10,703 + 4,877 missing 2006–2007).

## GitHub
`https://github.com/kyle8824/card-vault-catalog-packs/tree/master/full-restore-20260917`
