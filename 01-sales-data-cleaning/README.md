# 01 · Sales Data Cleaning in Excel

**Business question:** Can this sales file be trusted for reporting? What was broken, how much of it, and what changes once it's fixed?

## Key results
- **315 raw rows → 300 clean, unique orders** (15 exact duplicates removed).
- **Every row had at least one issue**: all 315 dates were stored as text in 4 different formats.
- **₹7.47 lakh of revenue was hidden**: 12 orders had blank quantities and showed ₹0 revenue. Filling them with the product's median quantity (and flagging them as estimates) brought total revenue to **₹1.70 crore (₹17,046,330)**.
- **West leads with 30% of revenue**, followed by South (27%), North (23%) and East (20%). Laptops alone drive **64% of revenue**.

## What was broken, and how I fixed it

| Area | Problem | Rows | Fix |
|---|---|---|---|
| Duplicates | Repeated orders | 15 | Removed later copies of the same OrderID (records were identical) |
| OrderDate | Text dates in 4 formats (YYYY/MM/DD, DD.MM.YYYY, DD-MM-YYYY, Mon DD, YYYY) | 315 | Parsed each format into real Excel dates |
| SalesRep | Extra spaces, mixed case, blanks | 103 + 9 blank | TRIM + PROPER; blanks labelled **Unassigned** instead of guessing |
| Region | Mixed case, trailing spaces | 79 | TRIM + PROPER → 4 regions |
| Product | Case, plurals, spaces ("Mouses", " mouse") | 75 | Standardized to 6 products |
| UnitPrice | Text with ₹ and commas | 41 | SUBSTITUTE + VALUE → numbers |
| Discount | Mix of 0.1 and "10%" | 25 | Converted all to decimals |
| Location | City and state in one column | 300 | Text to Columns → City, State |
| Quantity | Blank values | 12 | Filled with product median; **Qty_Estimated = TRUE** flag added |
| Revenue | Not present | — | `Quantity × UnitPrice × (1 − Discount)` |

## Decisions worth noting
- **No guessed salespeople.** Missing reps are marked *Unassigned*, so rep-level reports stay honest.
- **Estimates are flagged, not hidden.** Anyone can filter `Qty_Estimated = TRUE` to see or exclude the 12 imputed orders.
- **Reconciliation.** A region pivot was built on the clean data, and its grand total matches the CleanData revenue total.

## Files
- `data/raw_sales.xlsx`: the original messy file
- `data/sales_cleaning_workbook.xlsx`: RawData, CleanData, PivotbyRegion and the Cleaning Log

## Skills
Excel · TRIM · PROPER · SUBSTITUTE · VALUE · DATE · Text to Columns · Remove Duplicates · Pivot tables · Data validation thinking · Documentation
