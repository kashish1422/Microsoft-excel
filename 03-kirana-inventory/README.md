# 03 · Kirana Store Inventory in Excel

**Business question:** A neighbourhood kirana store tracks stock with product codes and messy product names. What does the store have, where is its money tied up, and what needs restocking right now?

## Key results
- **₹1,01,579 of stock** across 37 products in 6 categories.
- **Grocery holds 62.5% of all stock value (₹63,475).** Just two items, Fortune Sunflower Oil 5L (₹28,860) and India Gate Basmati Rice 5KG (₹21,240), make up almost **half of the store's entire stock value**.
- **20 of 37 products (54%) need action:** 7 are out of stock and 13 are at or below their reorder level.
- **Every category has at least one product that is out of stock or needs reordering.** Snacks are hit hardest: both Haldiram Bhujia packs are out of stock.

**Recommendation:** Restock the 7 out-of-stock items first, starting with fast movers like Haldiram Bhujia, Tata Tea Gold 1KG and Amul Butter 500G. Next, top up daily essentials that are running low: Amul Taaza Milk 1L (3 left), Mother Dairy Curd and Parle-G. Before reordering bulk grocery packs, check how fast they actually sell, because they already hold most of the store's cash.

## How it works

| Sheet | What it does |
|---|---|
| **Inventory** | Splits each SKU (e.g. `DAI-AMUL-500ML-0001`) into category, brand, pack size and ID. Cleans product names, calculates stock value, and flags each item as *Out of Stock*, *Reorder* or *OK* |
| **Summary** | Total stock value and a category-level view using `UNIQUE` and `SUMIFS` |

- **Decoding product codes.** The brand and pack-size parts of the SKU have different lengths for each product, so the codes are split at the dashes rather than at fixed positions.
- **Name cleaning.** `TRIM` and `PROPER` remove extra spaces and fix inconsistent capitalisation.
- **Category names.** Short codes (DAI, BEV, SNK, DRY, PER, HOM) are converted into readable names.
- **Stock status.** Each product's quantity is compared with its own reorder level.

## Data
37 sample products modelled on a typical Indian kirana store (Amul, Tata, Parle, Haldiram, Fortune, Colgate and others), with deliberately messy product names.

## Files
- `Kirana_store.xlsx`: the Inventory and Summary sheets

## Skills
Excel · LEFT · MID · FIND · SUBSTITUTE · TRIM · PROPER · IFS · UNIQUE · SUMIFS · Inventory analysis
