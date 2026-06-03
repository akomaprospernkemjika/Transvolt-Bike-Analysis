# 🚴 Tranvolt Bikes — Customer Purchase Behaviour Analysis

![Excel](https://img.shields.io/badge/Tool-Microsoft%20Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![PowerBI](https://img.shields.io/badge/Learning-Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Dataset](https://img.shields.io/badge/Records-1%2C000-blue?style=flat)
![Regions](https://img.shields.io/badge/Regions-3-orange?style=flat)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat)

An end-to-end Excel analytics project examining what drives bike purchase decisions across 1,000 customers in Europe, North America, and the Pacific. The project covers raw data cleaning, pivot table analysis, KPI calculation, and an interactive dashboard with slicer-based filtering.

> **Beyond the dataset:** This analysis mirrors the exact kind of customer segmentation and conversion analysis that FMCG companies, retail chains, and consumer goods businesses run every quarter — just at a larger scale. The thinking, structure, and recommendations here are directly transferable to real business decisions.

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Real-World Business Application](#real-world-business-application)
- [Dataset Description](#dataset-description)
- [Workbook Structure](#workbook-structure)
- [Key Findings](#key-findings)
- [Dashboard Features](#dashboard-features)
- [How to Use](#how-to-use)
- [Recommendations](#recommendations)
- [Known Limitations](#known-limitations)
- [Project Structure](#project-structure)
- [About the Author](#about-the-author)

---

## Project Overview

**Business question:** What demographic and lifestyle characteristics make a customer more likely to purchase a bike?

Tranvolt Bikes operates across three global regions and needed to understand which customer segments were converting and which were not — and why. This project analyses 1,000 customer records to surface actionable insights around age, income, commute behaviour, education, and geography.

**Deliverables:**
- A cleaned and documented dataset
- Pivot table metrics across 5 analytical dimensions
- An interactive Excel dashboard with dynamic slicers
- An executive summary with 6 key insights and 6 strategic recommendations

---

## Real-World Business Application

This project is not just an academic exercise. The framework used here — segmenting customers by demographics, identifying high-converting groups, and translating that into targeted action — is the backbone of how data-driven decisions are made in real businesses every day.

### How this applies to FMCG and consumer goods companies

Fast-moving consumer goods companies like Unilever, Nestlé, P&G, and their regional equivalents deal with exactly this type of question at scale:

> *Who is buying our product, who isn't, and what do we do about it?*

| What this project does | What an FMCG business does |
|------------------------|---------------------------|
| Segments 1,000 bike customers by age, income, commute | Segments millions of shoppers by demographics, basket size, purchase frequency |
| Identifies that 35–44 year-olds have the highest purchase rate | Identifies that young urban professionals are the fastest-growing segment for a product |
| Finds Pacific region converts at 59% but North America at 43% | Finds that Lagos outperforms Abuja in unit sales despite lower distribution spend |
| Recommends doubling down on the Pacific | Recommends reallocating trade spend to high-conversion territories |
| Shows short commuters buy the most | Shows that customers within 2km of a retail outlet have 3x the purchase frequency |

### Specific FMCG use cases this analysis maps to

**Route-to-market optimisation**
FMCG brands need to know which territories, channels, and customer types yield the best return on sales effort. The regional conversion analysis in this project (Pacific 59% vs North America 43%) is the same logic applied when a sales director decides where to deploy field reps or increase distributor investment.

**Consumer segmentation for campaign targeting**
The finding that single professionals aged 35–44 with Bachelor's degrees are the top-converting segment is identical to how a brand team would define a target persona before a campaign brief. Marketing agencies and in-house brand teams build entire campaign strategies on exactly this kind of segmentation output.

**Shelf placement and distribution decisions**
The commute distance insight — short commuters buy the most — parallels proximity-to-point-of-sale analysis. FMCG brands pay attention to whether customers are buying near home, near work, or on impulse. Distance to retail is a known driver of purchase frequency for impulse and convenience categories.

**Sales force effectiveness (SFE)**
The regional breakdown showing North America underperforming despite having the most customers is a classic SFE red flag. In an FMCG context, this would trigger a territory review — are reps calling on the right outlets? Is the product priced correctly for that market? Is distribution adequate?

**Distributor and retail partner reviews**
FMCG companies present analyses like this to their retail partners (supermarkets, pharmacies, convenience stores) to negotiate better shelf space, promotional slots, and category positioning. A well-structured dashboard with clear conversion metrics is a standard tool in those conversations.

### The bottom line

Whether the product is a bike, a sachet of detergent, a beverage, or a consumer electronics device — the analytical questions are the same: *Who buys? Who doesn't? What separates them? Where do we focus?* This project demonstrates the ability to answer those questions clearly and turn the answers into decisions.

---

## Dataset Description

The dataset contains **1,000 customer records** with the following 13 fields:

| Column | Type | Description |
|--------|------|-------------|
| `ID` | Integer | Unique customer identifier |
| `Marital Status` | Categorical | `Married` or `Single` |
| `Gender` | Categorical | `Male` or `Female` |
| `Income` | Numeric | Annual income in USD (binned to nearest $10,000) |
| `Children` | Integer | Number of children (0–5) |
| `Education` | Categorical | Highest education level attained |
| `Occupation` | Categorical | Job category |
| `Home Owner` | Boolean | `Yes` or `No` |
| `Cars` | Integer | Number of cars owned (0–4) |
| `Commute Distance` | Ordinal | Distance band: `0-1 Miles` through `10+ Miles` |
| `Region` | Categorical | `Europe`, `North America`, or `Pacific` |
| `Age` | Integer | Customer age in years |
| `Purchased Bike` | Boolean | Target variable — `Yes` or `No` |

**Education levels** (ordered low to high):
`Partial High School` → `High School` → `Partial College` → `Bachelors` → `Graduate Degree`

**Occupation categories:**
`Manual`, `Clerical`, `Skilled Manual`, `Professional`, `Management`

> **Note on income:** Values are rounded to the nearest $10,000 — they represent income bands rather than precise figures.

> **Data quality flag:** One record (ID: 15628) has an age of 89, which is a likely data entry error. Retained but flagged.

---

## Workbook Structure

The workbook contains **6 sheets**, each serving a distinct purpose:

### 1. `Dashboard!`
The main output. An interactive visual report with 4 live KPI cards, 3 pivot charts, and 3 slicers (Gender, Marital Status, Occupation). All values update dynamically when slicers are applied.

### 2. `Bike Buyers`
The raw dataset with abbreviated categorical values. Source of truth for all analysis.

### 3. `WORK FIELD!`
Cleaned version of the raw data with all abbreviations expanded to full text. Used as the data source for pivot tables to ensure readable chart labels and slicer values.

### 4. `Pivot Gear!`
All calculated metrics powering the dashboard — KPIs, purchase rates by age and commute, income by region and age bracket, and education/occupation cross-tabulation.

### 5. `KPIs & Metrics!`
Planning reference sheet listing all KPIs and metrics targeted in this analysis.

### 6. `Summary & Key Insights!`
Written executive summary with full findings and strategic recommendations, suitable for non-technical stakeholders.

---

## Key Findings

### 1. Short commuters are the top buyers
Customers commuting **0–1 miles** made **207 purchases** — the highest of any group. Long-distance commuters (10+ miles) bought only 33. Bikes are being chosen for short, convenient trips.

### 2. The 35–44 age group dominates purchases
This bracket accounts for **19.7% of all purchases** — the highest buyer-to-non-buyer ratio of any age group. Purchase likelihood drops sharply after 55.

### 3. Single customers out-purchase married ones
Single customers: **259 purchases** vs. married: **236** — despite married customers being the larger group. Fewer financial commitments likely drives more flexible spending.

### 4. Higher education correlates with higher purchase rates
- Bachelor's degree: **169 purchases** (top group)
- Graduate degree: **95 purchases**
- Partial High School: **22 purchases** (lowest)

### 5. Income difference is real but modest
Buyers average **$57,474** vs. non-buyers at **$55,028** — a $2,446 gap. Income amplifies other factors but is not a strong standalone predictor.

### 6. Pacific region converts best; North America underperforms
Pacific: **59% conversion rate** (smallest region, best results).
North America: **43% conversion rate** (most customers, worst results) — the biggest untapped opportunity in the dataset.

---

## Dashboard Features

### KPI Cards
| Metric | Value |
|--------|-------|
| Total Records | 1,000 |
| Purchase Rate | 48.1% |
| Total Buyers | 481 |
| Average Income | $56,360 |

### Charts
| Chart | Type | What it shows |
|-------|------|---------------|
| Purchase Rate by Age Group | Line chart | Buyer vs. non-buyer proportion across age brackets |
| Purchase Rate by Commute Distance | Bar chart | Buyer vs. non-buyer split across 5 distance bands |
| Income Distribution by Region | Column chart | Average income across Europe, North America, Pacific |

### Slicers
- **Gender** — Male / Female
- **Marital Status** — Married / Single
- **Occupation** — Manual / Clerical / Skilled Manual / Professional / Management

All three slicers filter every chart and KPI card simultaneously.

---

## How to Use

1. Download `data/Tranvolt_Bikes_Dataset.xlsx`
2. Open in **Microsoft Excel 2016 or later**
3. Go to the `Dashboard!` tab
4. Use the slicers to filter by Gender, Marital Status, or Occupation
5. All KPI cards and charts update automatically
6. To reset, click the clear filter icon (top-right of each slicer)

> Google Sheets is **not supported** — slicers and chart formatting will not render correctly.

---

## Recommendations

| # | Recommendation | Rationale |
|---|---------------|-----------|
| 1 | **Target short commuters aggressively** | 0–1 mile commuters are the #1 buyer group. Market bikes as a convenient daily solution, not a sport product |
| 2 | **Build campaigns around single professionals aged 35–44** | Highest-converting segment. All primary messaging should start here |
| 3 | **Invest more in the Pacific region** | 59% conversion rate — the most receptive market. Increase distribution and promotions immediately |
| 4 | **Fix the North America strategy** | Most customers, worst conversion (43%). A targeted diagnosis here could deliver the biggest sales uplift |
| 5 | **Lead with education-based positioning** | Higher-educated customers buy more. Use language around efficiency, sustainability, and smart commuting |
| 6 | **Re-engage married customers with family messaging** | Currently underperforming. Bike as family activity, school run savings, and health benefits for parents |

---

## Known Limitations

| Limitation | Detail |
|-----------|--------|
| Income precision | Binned to $10,000 intervals — not exact figures |
| Age outlier | One record has age = 89, likely a data entry error |
| No time dimension | No purchase date available — trend analysis over time is not possible |
| Small sub-groups | 75–84 and 85–94 age brackets have 3 and 1 records respectively — interpret with caution |
| Google Sheets | Slicers and chart formatting not compatible |

---

## Project Structure

```
tranvolt-bikes-analysis/
│
├── README.md                        ← Project overview and findings
├── CHANGELOG.md                     ← Version history
│
├── data/
│   └── Tranvolt_Bikes_Dataset.xlsx  ← Full workbook (data + analysis + dashboard)
│
└── docs/
    ├── data-dictionary.md           ← Field definitions and value descriptions
    └── methodology.md               ← Analysis approach, decisions, and known issues
```

---

## About the Author

**Akoma Prosper Nkemjika**
*Entrepreneur | Sales & Marketing Professional | Aspiring Data Analyst*

I am not a typical data analyst. Before I ever opened a spreadsheet to analyse numbers, I was analysing people — reading rooms, understanding motivations, and shaping conversations. As an English Studies graduate, I trained in the close reading of language, narrative, and human behaviour. That foundation never left me; it simply found a new application.

In 2024, I built a production business from the ground up and grew it to **300 customers**, achieving **50% profit margins within 4 months** — not through luck, but through understanding what customers wanted, where the market gaps were, and how to position a product to convert interest into purchase. That is, at its core, what data analysis is: turning information into decisions that produce outcomes.

Today, as a **Sales and Marketing Intern**, I sit at the intersection of two disciplines that most people keep separate. I understand how products move through markets, how customers make decisions, and how businesses grow — and I am now building the technical skills to quantify, model, and communicate those dynamics with data.

I work primarily in **Microsoft Excel** (pivot tables, dashboards, slicers, dynamic KPIs) and am actively developing my skills in **Power BI**. My goal is to become a data analyst in the FMCG or consumer goods sector — where the gap between a good insight and a missed target is measured in revenue, shelf space, and market share.

What makes my approach different is that I do not separate the numbers from the business. I analyse data the way I once analysed texts and conversations — looking for patterns, understanding context, and asking what the numbers are actually saying about human behaviour. Because at the end of the day, every dataset is a record of decisions that people made. And understanding people has always been what I do.

---

### Connect
- 📧 Open to data analyst roles, collaborations, and FMCG analytics conversations
- 🌍 Based in Nigeria

---

*Last updated: June 2026*
