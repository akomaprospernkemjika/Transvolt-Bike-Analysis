# Methodology

**Project:** Tranvolt Bikes — Customer Purchase Behaviour Analysis
**Tool:** Microsoft Excel (pivot tables, pivot charts, slicers, linked shapes)

---

## 1. Objectives

The goal was to answer one primary business question:

> *What demographic and lifestyle characteristics make a customer more likely to purchase a bike?*

Secondary questions:
- Which region has the highest and lowest conversion rate, and why might that be?
- Which age group represents the highest-value target segment?
- Does commute distance predict purchase behaviour?
- Is income a meaningful differentiator between buyers and non-buyers?

---

## 2. Data Preparation

### 2.1 Source data
The raw dataset (`Bike Buyers` sheet) was provided with abbreviated categorical values (`M`/`S`, `M`/`F`) to reduce file size. These abbreviations work for computation but produce unreadable labels in charts and pivot table headers.

### 2.2 Expansion to WORK FIELD!
A cleaned copy of the dataset was created in the `WORK FIELD!` sheet with all abbreviations replaced by full descriptive text:
- Marital Status: `M` → `Married`, `S` → `Single`
- Gender: `M` → `Male`, `F` → `Female`

This sheet is used as the data source for all pivot tables to ensure chart labels, slicer values, and pivot headers are human-readable without any additional formatting.

### 2.3 Data quality checks
The following issues were identified:

| Issue | Record | Detail | Action taken |
|-------|--------|--------|-------------|
| Age outlier | ID 15628 | Age = 89 | Retained; flagged in documentation |
| Possible region misassignment | ID 14063 | Pacific region, but positioned between North America records | Retained; flagged for review |
| Income precision | All records | Income binned to $10,000 intervals | Documented as a known limitation |

No rows were deleted. All 1,000 records are present in both the raw and cleaned sheets.

---

## 3. Metric Design

### 3.1 KPIs
Four headline KPIs were defined to give an at-a-glance view of the dataset:

| KPI | Formula | Source cell |
|-----|---------|------------|
| Total Records | `COUNTA` of ID column | Pivot Gear E1 |
| Purchase Rate | Count of Yes / Total records | Pivot Gear B20 |
| Total Buyers | Count of `Purchased Bike = Yes` | Pivot Gear C20 |
| Average Income | `AVERAGE` of Income column | Pivot Gear E20 |

All KPI values on the dashboard are linked directly to the Pivot Gear sheet via cell references — they are not hardcoded. This means they update automatically when slicers filter the underlying pivot tables.

### 3.2 Age grouping
Customers were grouped into 10-year age brackets:

| Bracket | Age range |
|---------|-----------|
| 25–34 | 25 to 34 |
| 35–44 | 35 to 44 |
| 45–54 | 45 to 54 |
| 55–64 | 55 to 64 |
| 65–74 | 65 to 74 |
| 75–84 | 75 to 84 |
| 85–94 | 85 to 94 |

The 75–84 and 85–94 brackets have very few records (3 and 1 respectively) and should be interpreted with caution.

### 3.3 Purchase rate calculation
Purchase rate is expressed as a proportion (0–1) rather than a percentage in the underlying pivot data, then formatted as a percentage on the dashboard. This was a deliberate choice to keep pivot formulas consistent — all rates are `Count of ID (Yes or No) / Grand Total`.

---

## 4. Pivot Table Structure

Nine pivot tables were built in the `Pivot Gear!` sheet:

| Pivot | Rows | Values | Purpose |
|-------|------|--------|---------|
| KPI summary | Purchased Bike | Count, Average Income | Top-level KPI cards |
| Max income by age | Age bracket | Max Income | Exploratory — highest earner per group |
| Displayed KPIs | — | Linked values | Dashboard KPI card sources |
| Purchase rate by age | Age bracket | Count of ID (% of total) | Age group chart |
| Purchase rate by commute | Commute Distance | Count (% of total) | Commute chart |
| Income by region | Region | Average Income | Region income chart |
| Income by age bracket | Age bracket | Sum and Average Income | Income distribution analysis |
| Purchase rate by education/occupation | Education, Occupation | Count of ID | Cross-tab analysis |

---

## 5. Dashboard Construction

### 5.1 Layout approach
The dashboard uses floating drawing objects (shapes, text boxes, charts) layered over a blank worksheet with gridlines hidden. No values are stored in worksheet cells — all content is in the drawing layer. This gives full control over layout and visual design without being constrained by cell boundaries.

### 5.2 KPI cards
Each KPI card is built from:
- A filled rectangle shape (background)
- A text box (label + icon)
- A linked text box (value, linked to a Pivot Gear cell via `textlink` property)

The linked text boxes pull their display value directly from the pivot sheet, so they update when slicers are applied.

### 5.3 Charts
Three pivot charts are embedded as floating objects:
- **Chart 1** (Line): Purchase rate by age group — two series (buyers vs. non-buyers as proportion of total)
- **Chart 2** (Bar): Purchase rate by commute distance — two series (buyers vs. non-buyers)
- **Chart 3** (Column): Average income by region — single series

Chart titles are currently implemented as separate floating text boxes rather than as native chart title properties. This is a known limitation — see section 6.

### 5.4 Slicers
Three slicers (Gender, Marital Status, Occupation) are connected to all pivot tables simultaneously. Selecting a value in any slicer filters all charts and KPI cards at once. Multiple values can be selected using Ctrl+Click.

To clear a slicer filter, click the clear button (top-right corner of the slicer, icon looks like a funnel with an X).

---

## 6. Known Issues and Design Decisions

### Chart titles as floating text boxes
Chart titles were placed as separate floating text boxes rather than embedded in the chart title property. This means titles do not move with the chart if the chart is repositioned.

**Recommended fix:** Right-click each chart → Edit → Chart Title → type the title directly into the chart object.

### Age group chart uses a line chart
The purchase rate by age group uses a line chart. For discrete categorical data (age brackets), a clustered column chart is more statistically appropriate — a line implies continuous change between categories.

**Recommended fix:** Change chart type to Clustered Column.

### Education/occupation pivot filter
The `Purchase Rate by Education and Occupation` pivot in Pivot Gear has a filter applied that limits the view to `Partial College` only. The full education breakdown across all levels is not currently visible.

**Recommended fix:** Clear the filter on the Education field in that pivot table.

### Duplicate raw data
The `Bike Buyers` and `WORK FIELD!` sheets contain identical data — one abbreviated, one expanded. This doubles the storage of raw data in the workbook.

**Alternative approach:** Use `IF` or `IFS` formulas in `WORK FIELD!` to dynamically expand abbreviations from `Bike Buyers`, reducing storage and ensuring the two sheets are always in sync.

---

## 7. Analytical Decisions

**Why proportions rather than raw counts for purchase rate?**
Raw counts favour larger groups. A group with 200 buyers from 400 customers is more noteworthy than a group with 250 buyers from 700 customers. Using proportion (% of total) normalises for group size and makes cross-group comparison meaningful.

**Why average income rather than median?**
Average income is used throughout for consistency with the pivot table default. The income distribution in this dataset is right-skewed (a few high earners pull the mean up), so median would be a more robust central tendency measure. This is noted as a limitation.

**Why three regional categories?**
The data was provided with three pre-defined regions. No country-level breakdown was available, so regional analysis is the finest geographic granularity possible with this dataset.
