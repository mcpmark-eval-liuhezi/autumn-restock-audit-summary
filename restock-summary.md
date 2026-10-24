# Autumn restock audit — coffee line

**Import method:** one product at a time via the WooCommerce products API (no bulk import), stock management enabled on all 8 products.

## Low-in-stock report — flagged items (at report time)

| Product | SKU | Stock at report time |
| --- | --- | --- |
| Summit Espresso Blend Beans 250g | SEB-250 | 2 |
| Porcelain Pour-Over Dripper Set | PPO-200 | 1 |
| Burr Hand Grinder Pro | BHG-100 | 2 |

Note on method: the store runs WooCommerce 10.7.0, where the legacy `reports/stock/low` REST endpoint has been removed (it returns 404). The report was therefore captured using the store's own low-stock evaluation (`low_stock_remaining` from the Store API), which flags these same three products.

## Store-config repository baseline

- **Repository:** `/tmp/mcp_ws` (the store-config repository in the workspace; no separate `store-config` subdirectory exists)
- **Branch:** `master`
- **Working tree:** clean — no uncommitted changes
- **Latest commit:** `25bfe74868dd8d9a9eed8113ede3cb9cf0540e21` — "Initial synthetic state" (authored by MCP World, 2026-10-24 16:54:55 +00:00)

## Restock / follow-up low-in-stock check

Every product in the line was checked against the trade-show minimum of 25 units. Three were below 25 and were topped up to exactly 25:

| Product | SKU | Before | After |
| --- | --- | --- | --- |
| Summit Espresso Blend Beans 250g | SEB-250 | 2 | 25 |
| Porcelain Pour-Over Dripper Set | PPO-200 | 1 | 25 |
| Burr Hand Grinder Pro | BHG-100 | 2 | 25 |

The other five products were already at or above 25 (AG-HB-1KG: 42, AG-ET-250: 30, RFP-600: 55, ITT-400: 48, CBC-1L: 36) and were left untouched.

**Follow-up low-in-stock result: no products flagged.** All three previously low items now report healthy stock (25 in stock each) and are no longer marked low-in-stock.

## Tracking issue

https://github.com/mcpmark-eval-liuhezi/autumn-restock-audit/issues/1
