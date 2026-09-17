# SHARDS — assemble LIVE public/catalog

## Detected LIVE layout
- `/catalog/sets-index.json`
- `/catalog/set-cards/{set_id}.json` (per-set checklist)

Year `.jsonl.gz` shards are **source material**. Build should:

1. Gunzip `sets-index.json.gz` → `public/catalog/sets-index.json` (or rebuild from `sets.jsonl` + card counts).
2. For each `cards-*.jsonl.gz` (skip `cards-ALL` if using year parts):
   - Gunzip → stream JSONL
   - Group rows by `set_id`
   - Write `public/catalog/set-cards/{set_id}.json` for each group
     - Preferred body: JSON **array** of card objects (match existing live files)
3. Copy/gunzip `sources` only if the app reads them; catalog UI primarily uses sets-index + set-cards.
4. **Include every year shard** — pre-1990 through 2009 + unknown. Do not leave only 2005–2007.
5. **Do not Publish** until the full tree is on disk in the Build sandbox.

## Size guide
Individual year shards are ~1.2–5.3 MB gzip (under ~5–8 MB target). `cards-ALL.jsonl.gz` is ~30 MB optional convenience.

## Batch order suggestion for Build fetch
1. `sets-index.json.gz` + `sets.jsonl.gz` + `sources.jsonl.gz`
2. `cards-pre-1990` … `cards-2004`
3. `cards-2005` … `cards-2007` (fills the live gap)
4. `cards-2008` … `cards-2009` + `cards-unknown`

## Never
- Invent rows
- Drop Collection
- Publish the shrunk 2005–2007-only sandbox
