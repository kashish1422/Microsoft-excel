# 02 · Personal Expense Tracker in Excel

**Business question:** Where does a student's money actually go each month, and which spending categories break the budget?

## Key results
- **₹43,202 spent across 72 transactions** in 8 categories (October: ₹24,066 · 1–18 November: ₹19,136).
- **Rent is the biggest fixed cost at 37%** of spending. **Food is the biggest controllable cost at 30%** (₹13,120).
- **October: 4 of 8 categories went over budget**: Shopping (₹1,740 over), Travel (₹1,210), Food (₹930) and Entertainment (₹69).
- **November (to the 18th): Travel and Shopping are already over budget**, and Food has used ₹5,190 of its ₹7,000 budget with 12 days still to go.

**Recommendation:** Food takes about 30% of spending. Cutting unnecessary food orders could save **₹1,000–₹1,500 a month**, and setting a realistic travel budget would stop it going over every month.

## How it works

| Sheet | What it does |
|---|---|
| **Data** | One row per expense: Date, Category, Item, Amount, Payment Mode, plus a Month column built with `TEXT()` |
| **Summary sheet** | Category × Month spending grid, totals, budget vs actual for each month, and an insights section |

- **One formula fills the whole grid.** `SUMIFS` with mixed references (`$A2` for the category, `B$1` for the month) is written once and copied down and across.
- **Budget vs actual.** *Over/Under* = Budget − Actual, so a negative value means overspending.
- **Overspending flags itself.** Conditional formatting turns any negative *Over/Under* value red.
- **Insights are calculated, not typed.** `INDEX` + `MATCH` finds the biggest category, and its share of total spending is calculated next to it.

## Data
72 sample transactions from 1 October to 18 November 2026, modelled on typical monthly expenses for a student in India (PG rent, food delivery, metro, subscriptions). November is a part-month.

## Files
- `expense_tracker.xlsx`: the Data and Summary sheets

## Skills
Excel · Relative, absolute and mixed cell references · SUMIFS · TEXT · INDEX + MATCH · Conditional formatting · Budget vs actual analysis
