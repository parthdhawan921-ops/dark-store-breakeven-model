# Swiggy Instamart dark-store break-even model (Excel)

**Question:** How many orders a day does a quick-commerce dark store need to break even, and which lever (basket value, volume, ad income or rider cost) moves it furthest?

- **What I did:** Built an Excel model of a Swiggy Instamart dark store from its public results, with a checks sheet that must pass before any number is used.
- **What I found:** **A store needs about 1,133 orders a day to break even**, 5.4% more than today's ~1,075.
- **Why it matters:** Bigger baskets beat more orders: a 10% bigger basket adds about ₹85 crore a quarter across 1,171 stores.

**Interactive case file:** [parthdhawan921-ops.github.io/Parth_Personal/#darkstore](https://parthdhawan921-ops.github.io/Parth_Personal/#darkstore)

## Key findings

| Finding | Number |
|---|---|
| Orders per store per day, Apr to Jun 2026 | about 1,075 |
| Break-even orders per store per day | about 1,133 (5.4% above today) |
| Contribution margin, as disclosed | -0.2% of gross order value |
| Volume alone to reach +2% margin | about 2,483 orders a day (+131%) |
| +10% average order value | about +₹2.4 lakh per store per month; about ₹85 crore a quarter across 1,171 stores |
| Largest swing for a 10% move in one input | Average order value (about ₹4.9 lakh per store per month), then rider cost (about ₹2.9 lakh) |

## Scenarios

| Case | Contribution margin | Contribution per store per month |
|---|---|---|
| Base (as disclosed) | -0.2% | -₹0.45 lakh |
| Density up (+30% orders) | +0.7% | +₹2.0 lakh |
| Discount war (+₹10 discount per order, +10% orders) | -1.3% | -₹3.2 lakh |
| Lever pack (AOV +₹60, ad income +₹5, fee +₹3, rider cost -₹3) | +2.2% | +₹5.2 lakh |

The discount-war case is worth noting: order volume rises, yet the margin gets worse, because each extra order carries a deeper discount.

## Data

Swiggy Q1 FY27 (April to June 2026) shareholders' letter and KPI databook, Instamart segment:

- Gross order value (GOV): ₹7,907 crore
- Orders: 114.5 million (11.45 crore)
- Average order value: ₹691
- Adjusted revenue per order: ₹108
- Contribution margin: -0.2% of GOV
- Dark stores: 1,171 (4.92 million sq ft)

Benchmark only, not used in the break-even calculation: Blinkit (Eternal Q1 FY27), net order value per order ₹518, 2,443 stores, contribution margin 5.3% of net order value. It is there to check that the assumptions fall in a believable range.

## Method

1. Rebuild the quarter per order and per store per day: about 1,074.5 orders per store per day, a 15.6% take rate, and about ₹109.38 total cost per order.
2. Split costs into variable (rider, picking, packaging, payment, wastage) and fixed (rent, staff, power). Public data gives only the total, so the split is an assumption.
3. Calibrate to the disclosed figures. The product margin is solved so that revenue per order equals the disclosed ₹108. Fixed cost is solved so that the model reproduces the disclosed -0.2% margin. Calibrated fixed cost is about ₹8.6 lakh per store per month, against a bottom-up estimate (rent, staff, power) of about ₹7.5 lakh.
4. Break-even orders per day = fixed cost per day / contribution per order (about ₹25.42).
5. Sensitivity grids and scenarios recompute the full model in each cell.

## Assumptions

These are **not** disclosed by Swiggy. They sit in the yellow cells on the Inputs sheet, and changing any of them updates the whole workbook.

| Item | Assumed value |
|---|---|
| Delivery and handling fee | ₹12 per order |
| Ad income | ₹10 per order |
| Discounts | ₹6 per order |
| Rider cost | ₹45 per order |
| Picking and packing | ₹15 per order |
| Packaging | ₹6 per order |
| Payment gateway | 1.2% of order value |
| Wastage | 1.2% of order value |
| Rent | ₹100 per sq ft |
| Fixed staff | ₹2.5 lakh per store per month |
| Power and upkeep | ₹0.8 lakh per store per month |

## Limits

- The cost split, fee, ad income and discount per order are assumptions, not disclosures.
- Fixed cost is solved from the disclosed total and cross-checked, not observed.
- Inputs are moved one at a time. In reality, order value, volume and discounts affect each other.
- One quarter of whole-company averages. Individual stores will differ.
- Sensitivity grids use live formulas rather than Excel's Data Table feature, so they work in any spreadsheet viewer.

## Tools

Excel with live formulas throughout. No result is typed in as a hard number, and a Checks sheet confirms the workbook reproduces the headline figures.

## How to read the file

Open `A4_DarkStore_BreakEven.xlsx`. The sheets run in this order of logic: Inputs feed the Model, and the other sheets read from the Model.

| Sheet | What it holds |
|---|---|
| Summary | One-page recommendation, headline numbers and limits |
| Inputs | Disclosed figures, benchmark, derived figures, and the assumptions above |
| Model | Per-order profit and loss, calibrated fixed cost, break-even |
| Sensitivity | Three live grids: order value by volume, fee by discount, order value by rider cost |
| Scenarios | Base, density up, discount war, lever pack |
| Tornado | A 10% move in each input, ranked, with chart |
| BreakEven | Contribution against orders per day (line chart) |
| Checks | Reproduces the headline figures; should read ALL PASS |

To test the model yourself, change an assumption on the Inputs sheet (for example rider cost) and watch the break-even on the Model and Summary sheets update.
