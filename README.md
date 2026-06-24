# Chocolate-Sales-Dashboard

# 🍫 Chocolate Sales Salesperson Performance Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![CSV](https://img.shields.io/badge/CSV-Data-C8860A?style=for-the-badge)
![Records](https://img.shields.io/badge/Records-1%2C094-0284C7?style=for-the-badge)
![Revenue](https://img.shields.io/badge/Revenue-$6.18M-3E1C00?style=for-the-badge)

![Chocolate Sales Dashboard](Chocolate%20Sales%20Dashboard.jpeg)

> Data Analytics Portfolio · K.S. · Tool: Power BI Desktop

---

## 📌 Project Overview

Processed 1,094 chocolate sales records spanning 8 months (Jan–Aug 2022) through a structured Power Query ETL pipeline — stripping currency symbols from the Amount column, correcting 2 data type errors, and renaming columns for DAX compatibility. • Engineered 5 DAX measures including a dynamic RANKX()-based Salesperson Rank and built a 12-visual interactive dashboard covering salesperson leaderboard, country breakdown, product performance, monthly trend, and geographic distribution. • Analyzed $6,183,625 total revenue across 177,007 boxes shipped, surfacing a $182,378 performance gap between #1 (Ches Bonnell — $320,901) and #25 (Wilone O'Kielt — $138,523), and identified a remarkably balanced 3.02pp revenue spread across all 6 global markets.

---

## 🎯 Problem Statement

Chocolate sales data for 2022 existed as a raw CSV with no reporting structure. Managers had no visibility into salesperson performance rankings, country revenue distribution, or product category trends — and the Amount column contained currency-formatted text ($5,320) making aggregation impossible without data transformation.

---

## 🎯 Objectives

- Clean currency-formatted Amount column via Power Query Replace Values ETL
- Engineer 5 DAX measures including dynamic RANKX() salesperson ranking
- Build a 12-visual leaderboard dashboard across salesperson, country, and product dimensions
- Enable cross-filtering via 2 slicers (Country, Product)
- Surface top/bottom performer gap, country distribution, seasonal trends
- Deliver portfolio-ready report with custom chocolate-branded JSON theme

---

## 📁 Dataset

| Attribute | Detail |
|-----------|--------|
| **Name** | Chocolate Sales 2022 |
| **Source** | [Kaggle — atharvasoundankar/chocolate-sales](https://www.kaggle.com/datasets/atharvasoundankar/chocolate-sales) |
| **Format** | CSV (.csv) |
| **Records** | 1,094 rows · 6 columns |
| **Date Range** | January 3, 2022 – August 31, 2022 |
| **Geography** | 6 countries: Australia, UK, India, USA, Canada, New Zealand |
| **Null Values** | Zero — 100% complete dataset |

### Columns

| Column | Type | Description |
|--------|------|-------------|
| Salesperson | Text | 25 unique sales representatives |
| Country | Text | 6 countries across 3 continents |
| Product | Text | 22 chocolate product categories |
| Date | Date | Daily transaction date (Jan–Aug 2022) |
| Amount | Decimal | Revenue per sale in USD (originally stored as text '$5,320') |
| Boxes Shipped | Whole Number | Units shipped per transaction (avg 161.8 boxes) |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Power BI Desktop** | ETL, DAX modelling, and full dashboard build |
| **Power Query Editor** | Currency cleaning, type correction, column rename |
| **DAX** | 5 calculated measures including RANKX() |
| **CSV (.csv)** | Raw source format |
| **JSON Theme File** | Chocolate Indulgence branded theme (brown/gold/caramel) |

---

## ⚙️ ETL Process — Power Query (8 Steps)

```
Step 01 → Get Data → Text/CSV → selected Chocolate_Sales.csv
Step 02 → Clicked 'Transform Data' to open Power Query Editor
Step 03 → Amount column → Replace Values: '$' → '' (empty)
          (removed dollar sign from all 1,094 Amount values)
Step 04 → Amount column → Replace Values: ',' → '' (empty)
          (removed thousand separators: '$5,320' → '5320')
Step 05 → Amount column type → Decimal Number
          (enabled SUM/AVERAGE DAX measures)
Step 06 → Date column type → Date
          (converted '04-Jan-22' text to proper Date for time charts)
Step 07 → Renamed 'Sales Person' → 'Salesperson'
          (removed space for cleaner DAX formulas)
Step 08 → Home → Close & Apply
          (loaded 1,094 clean rows — 0 errors, 0 nulls)
```

---

## 📐 DAX Measures Created

```dax
Total Revenue = SUM('Chocolate Sales'[Amount])
-- Result: $6,183,625

Total Boxes = SUM('Chocolate Sales'[Boxes Shipped])
-- Result: 177,007

Avg Revenue per Sale = AVERAGE('Chocolate Sales'[Amount])
-- Result: $5,652.31

Total Transactions = COUNTROWS('Chocolate Sales')
-- Result: 1,094

Salesperson Rank = RANKX(ALL('Chocolate Sales'[Salesperson]), [Total Revenue], , DESC)
-- Result: Dynamic rank 1–25 responding to all slicer filters
```

> ⚠️ **Key Note:** `ALL()` inside RANKX is essential — without it, every salesperson shows rank 1 because ranking happens within the already-filtered context.

---

## 📊 Dashboard Visuals (12 Visuals)

| # | Visual | Fields | Insight |
|---|--------|--------|---------|
| 1 | KPI Card | Total Revenue | $6,183,625 |
| 2 | KPI Card | Total Boxes | 177,007 |
| 3 | KPI Card | Total Transactions | 1,094 |
| 4 | KPI Card | Avg Revenue per Sale | $5,652 |
| 5 | Clustered Bar | Salesperson vs Revenue | Ches Bonnell #1 at $320,901 |
| 6 | Clustered Bar | Country vs Revenue | Australia leads at $1,137,367 |
| 7 | Clustered Bar | Product vs Revenue | Smooth Sliky Salty #1 at $349,692 |
| 8 | Line Chart | Date vs Revenue | January peak $896K → April trough $674K |
| 9 | Donut Chart | Country vs Revenue | Balanced 15.37%–18.39% spread |
| 10 | Table | Salesperson + all measures | Full 25-person ranked leaderboard |
| 11 | Slicer | Country | Cross-filters all visuals |
| 12 | Slicer | Product | Cross-filters all visuals |

---

## 📈 Key Insights & Results

### Revenue & Volume
- Analyzed **$6,183,625** total revenue across **1,094 transactions** and **177,007 boxes** at **$5,652 avg per sale** and **161.8 avg boxes** per transaction.
- **January peak: $896,105** → April trough: **$674,051** (24.8% seasonal dip) → recovery to June **$865,144**.

### Salesperson Leaderboard
- **Ches Bonnell #1 — $320,901** (5.19% · 7,522 boxes · 48 transactions)
- **Wilone O'Kielt #25 — $138,523** (2.24% · 4,033 boxes · 34 transactions)
- **Performance gap: $182,378 — top performer generates 2.32× more revenue than bottom**
- Kelci Walkden led in transactions (54) at rank #5 — high volume, lower avg deal size ($5,772 vs Ches Bonnell's $6,686)

### Complete Salesperson Rankings

| Rank | Salesperson | Revenue | Boxes | Transactions |
|------|-------------|---------|-------|--------------|
| 1 | Ches Bonnell | $320,901 | 7,522 | 48 |
| 2 | Oby Sorrel | $316,645 | 8,608 | 49 |
| 3 | Madelene Upcott | $316,099 | 7,279 | 45 |
| 4 | Brien Boise | $312,816 | 8,102 | 53 |
| 5 | Kelci Walkden | $311,710 | 8,702 | 54 |
| 6 | Van Tuxwell | $303,149 | 6,799 | 51 |
| 7 | Dennison Crosswaite | $291,669 | 8,767 | 49 |
| 8 | Beverie Moffet | $278,922 | 9,214 | 50 |
| 9 | Kaine Padly | $266,490 | 7,253 | 45 |
| 10 | Marney O'Breen | $259,742 | 8,043 | 45 |
| ... | ... | ... | ... | ... |
| 23 | Camilla Castle | $196,616 | 5,374 | 32 |
| 24 | Dotty Strutley | $190,624 | 6,853 | 36 |
| 25 | Wilone O'Kielt | $138,523 | 4,033 | 34 |

### Country Distribution
- **Remarkably balanced** — only **3.02pp spread** across all 6 countries:
  - 🇦🇺 Australia — $1,137,367 (18.39%) · 🇬🇧 UK — $1,051,792 (17.01%)
  - 🇮🇳 India — $1,045,800 (16.91%) · 🇺🇸 USA — $1,035,349 (16.74%)
  - 🇨🇦 Canada — $962,899 (15.57%) · 🇳🇿 New Zealand — $950,418 (15.37%)

### Product Performance
- **#1: Smooth Sliky Salty — $349,692 (5.66%)**
- **#2: 50% Dark Bites — $341,712 (5.53%)**
- **#3: White Choc — $329,147 (5.32%)**
- **Last: 70% Dark Bites — $211,610 (3.42%)**

---

## 📊 KPI Summary

| KPI | Value | KPI | Value |
|-----|-------|-----|-------|
| Total Revenue | **$6,183,625** | Total Transactions | **1,094** |
| Total Boxes | **177,007** | Avg Revenue/Sale | **$5,652** |
| Salespersons | **25** | Countries | **6** |
| Products | **22** | Avg Boxes/Sale | **161.8** |
| #1 Salesperson | Ches Bonnell $320,901 | #25 Salesperson | Wilone O'Kielt $138,523 |
| Performance Gap | **$182,378 (2.32×)** | Top Country | Australia $1,137,367 |
| Country Spread | **3.02pp** | Top Product | Smooth Sliky Salty $349,692 |
| Peak Month | January $896,105 | Trough Month | April $674,051 |

---

## ⚡ Challenges & Solutions

**Challenge 1 — Amount as Currency Text**
Amount stored as '$5,320' (text) — SUM() returned blank. • Fixed via 2 Replace Values steps: remove '$' then remove ',' → change type to Decimal Number.

**Challenge 2 — Date as Text String**
'04-Jan-22' format blocked date hierarchies and monthly grouping. • Changed column type to Date in Power Query — auto-parsed the format, enabling line chart monthly drill-down.

**Challenge 3 — Column Space in DAX**
'Sales Person' (with space) required quote-wrapping in every DAX formula. • Renamed to 'Salesperson' in Power Query — cleaner, less error-prone DAX throughout.

**Challenge 4 — RANKX Showing Rank 1 for All**
RANKX without ALL() ranked within filtered context — all showed rank 1. • Added ALL('Chocolate Sales'[Salesperson]) to force ranking across all 25 regardless of slicers.

**Challenge 5 — Noisy Daily Line Chart**
Line chart showed hundreds of daily spikes instead of monthly trend. • Used drill-up button on Date hierarchy to collapse to Month level — clean 8-point trend visible.

---

## 🎓 Skills Learned

- **Currency Text ETL** — Replace Values ($ and ,) → Decimal type; real-world financial data cleaning
- **RANKX() with ALL()** — Dynamic context-aware ranking; ALL() override for cross-context calculation
- **COUNTROWS() vs COUNT()** — Reliable transaction counting; understanding filter-aware row counting
- **Date Hierarchy Control** — Drill-up/down on line chart date axis; choosing correct granularity
- **Leaderboard Design** — Bar chart (visual) + Table (precise numbers) — complementary visual pairing
- **Balanced Distribution Analysis** — Recognising 3.02pp country spread as a strategic business insight
- **Chocolate Brand Theming** — JSON theme with dark brown canvas, gold KPI borders, caramel data colors

---

## 🎨 Custom Theme

`Chocolate_Indulgence_Branded_Theme.json` — Apply via **View → Themes → Browse for themes**

| Element | Color | Meaning |
|---------|-------|---------|
| Canvas | `#1A0800` — Dark Chocolate | Brand identity |
| KPI Cards | `#2D1200` bg + `#C8860A` border | Milk chocolate + caramel |
| KPI Numbers | `#F4C842` gold | Premium highlight |
| Data Colors | Gold → Caramel → Brown shades | Chocolate palette |
| Axis Labels | `#A0875A` warm taupe | Readable on dark background |

---

## 📂 Repository Structure

```
chocolate-sales-dashboard/
│
├── 📊 Chocolate_Sales_Dashboard.pbix        # Power BI dashboard file
├── 📁 Dataset/
│   └── Chocolate_Sales.csv                  # Raw source data (Kaggle)
├── 📁 Theme/
│   └── Chocolate_Indulgence_Branded_Theme.json
├── 📄 Chocolate_Sales_Portfolio_Documentation.pdf
└── 📄 README.md
```

---

## 🚀 How to Use

```
1. Download Chocolate_Sales.csv from Kaggle link above
2. Open Chocolate_Sales_Dashboard.pbix in Power BI Desktop
3. Update data source path if prompted → click Refresh
4. Apply theme: View → Themes → Browse → select JSON file
5. Use Country / Product slicers to explore performance
6. Click any bar in salesperson chart to cross-filter all visuals
```

---

---

*Data Analytics Portfolio · Project 2 of 9 · Power BI · Beginner · Dataset: Kaggle*
