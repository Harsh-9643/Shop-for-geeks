# Grocery Inventory Manager for FreshMart Retail

A small Python project that tracks grocery stock, flags items below their minimum level, and calculates how much to reorder.

## Objective
FreshMart Retail, a local grocery chain, needs a simple way to:
- Track current stock
- Spot products that are running low
- Get a recommended reorder quantity for each product
- Export the result as a report

## Dataset
A small sample inventory of 5 products, created manually in the notebook (not a real store export).

| Column | Meaning |
|---|---|
| `ProductID`, `ProductName`, `Category` | Product details |
| `CurrentStock` | Units currently in stock |
| `MinRequiredStock` | Minimum units the store wants to keep |
| `UnitsSoldThisWeek` | Units sold in the last week |

## Tools
Python, Pandas, Matplotlib, Seaborn, Jupyter / Google Colab

## Approach
1. Built the inventory table with Pandas.
2. **Low stock check:** selected products where `CurrentStock < MinRequiredStock`.
3. **Reorder quantity:** `ReorderQty = MinRequiredStock - CurrentStock` for low-stock items, otherwise `0`.
4. Plotted current stock per product with a reference line for the average minimum stock.
5. Exported the final table to `FreshMart_Inventory_Report.csv`.

## Key Findings
- **4 of 5 products are below minimum stock:** Rice, Milk, Bread and Sugar. Only Oil is above its minimum.
- **Total reorder needed: 30 units** (Rice 10, Milk 10, Bread 5, Sugar 5).
- **Milk is the highest risk.** It has the highest weekly sales (45 units) but only 10 units in stock, so it can run out within days.
- **Oil is slow-moving.** It sold only 5 units this week while 70 units are in stock, so it should not be reordered soon.

## Limitations
- Only 5 products with sample data, so this shows the logic rather than a production system.
- Reorder quantity only brings stock back to the minimum level. It does not use sales speed, so fast sellers like Milk may still need a larger order.
- The red line in the chart is the average of all minimum stock levels, not each product's own minimum.

## Possible Improvements
- Use weekly sales to estimate days of stock left for each product.
- Load a real inventory file (CSV or SQL) instead of typing the data in.
- Build a dashboard for live stock monitoring.

## Project Structure
- `Shop_for_geeks.ipynb`: analysis notebook
- `FreshMart_Inventory_Report.csv`: generated reorder report
