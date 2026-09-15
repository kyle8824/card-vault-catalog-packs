# Catalog-only delta — append to live Card Vault

HARD RULES: catalog/data only. NO UI redesign. Preserve Collection/inventory.
Do **NOT** publish to live yourself in the fill task — this pack is append-ready only.

Append these JSONL rows into the live catalog (do not replace full catalog):
- sets.jsonl (19 sets)
- cards.jsonl (611 cards)
- sources.jsonl (23 sources)

Primary Kyle / Collectibles Lead spot-check after a later publish:
- `2003-upper-deck-ultimate-collection-football` (107 cards)

Also includes TCDB-documented related inserts/parallels/autos (Gold, Ultimate Signatures ± Gold, Dual Ultimate Signatures ± Gold, Ultimate Game Jerseys/Patches ± Gold/Signed, Dual Game Jerseys/Patches ± Gold/Signed, Autographed Buybacks).

Verify base set shows 107 cards on https://card-vault.grok.me/catalog, then publish.
