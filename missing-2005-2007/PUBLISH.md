# Catalog-only LIVE APPEND — missing 2005–2007

HARD RULES:
1. Catalog data /catalog-page only — NO UI redesign
2. Preserve Collection/inventory exactly
3. Never invent checklist rows

Append sets.jsonl + cards.jsonl + sources.jsonl into existing live catalog.
Priority verify after publish:
- 2006 Topps Baseball (must appear with checklist)
- 2007 Topps Baseball (must appear with checklist)
- A non-stub 2007 football set that was empty before should gain cards if complete data exists

Built from on-disk merge (no new Grok fill).
