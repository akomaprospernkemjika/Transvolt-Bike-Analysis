# Data Dictionary

**Dataset:** Tranvolt Bikes — Customer Purchase Behaviour
**Records:** 1,000
**Source sheet:** `Bike Buyers` (abbreviated) / `WORK FIELD!` (expanded)

---

## Fields

### ID
- **Type:** Integer
- **Range:** 11000–29999
- **Description:** Unique customer identifier. No business meaning — used for row identification only.
- **Notes:** No duplicates. Not sequential.

---

### Marital Status
- **Type:** Categorical
- **Raw value (`Bike Buyers`):** `M` = Married, `S` = Single
- **Expanded value (`WORK FIELD!`):** `Married`, `Single`
- **Notes:** Binary field. No `Divorced`, `Widowed`, or other categories present in this dataset.

---

### Gender
- **Type:** Categorical
- **Raw value (`Bike Buyers`):** `M` = Male, `F` = Female
- **Expanded value (`WORK FIELD!`):** `Male`, `Female`
- **Notes:** Binary field as recorded in source data.

---

### Income
- **Type:** Numeric (USD)
- **Range:** $10,000 – $170,000
- **Description:** Annual household income.
- **Notes:** Values are rounded to the nearest $10,000 — these are income bands, not precise figures. Treat as ordinal/categorical for segmentation purposes.

---

### Children
- **Type:** Integer
- **Range:** 0 – 5
- **Description:** Number of dependent children in the household.

---

### Education
- **Type:** Ordinal categorical
- **Values (low to high):**

| Value | Meaning |
|-------|---------|
| `Partial High School` | Did not complete secondary education |
| `High School` | Completed secondary education |
| `Partial College` | Some university education, no degree |
| `Bachelors` | Completed undergraduate degree |
| `Graduate Degree` | Completed postgraduate degree (Masters, PhD, etc.) |

---

### Occupation
- **Type:** Categorical
- **Values:**

| Value | Meaning |
|-------|---------|
| `Manual` | Physical/unskilled labour |
| `Clerical` | Administrative and office support roles |
| `Skilled Manual` | Trades and technical manual work |
| `Professional` | Knowledge-based roles (e.g., engineer, accountant, lawyer) |
| `Management` | Supervisory or executive roles |

---

### Home Owner
- **Type:** Boolean
- **Values:** `Yes`, `No`
- **Description:** Whether the customer owns their primary residence.

---

### Cars
- **Type:** Integer
- **Range:** 0 – 4
- **Description:** Number of cars owned by the household.
- **Notes:** Higher car ownership may negatively correlate with bike purchase — worth investigating as a predictor variable.

---

### Commute Distance
- **Type:** Ordinal categorical
- **Values (shortest to longest):**

| Value | Meaning |
|-------|---------|
| `0-1 Miles` | Very short commute — walkable/cyclable distance |
| `1-2 Miles` | Short commute |
| `2-5 Miles` | Medium-short commute |
| `5-10 Miles` | Medium-long commute |
| `10+ Miles` | Long commute |

- **Notes:** This is the single strongest predictor of bike purchase in the dataset. Short commuters buy significantly more.

---

### Region
- **Type:** Categorical
- **Values:** `Europe`, `North America`, `Pacific`
- **Notes:** Three broad geographic regions. No country-level data is available. Regional income averages differ significantly (Europe: $40,900 vs. Pacific: $63,594), which may confound regional purchase rate comparisons.

---

### Age
- **Type:** Integer
- **Range:** 25 – 89 (effective range: 25–78, one outlier at 89)
- **Description:** Customer age in years at time of record creation.
- **Data quality flag:** One record (ID: 15628) has age = 89. This is a likely data entry error and should be reviewed before using age-based models or segmentations.

---

### Purchased Bike
- **Type:** Boolean (target variable)
- **Values:** `Yes`, `No`
- **Description:** Whether the customer purchased a bike.
- **Distribution:** 481 `Yes` (48.1%) / 519 `No` (51.9%)
- **Notes:** This is the dependent variable for all analysis. The near-even split makes this a well-balanced classification problem.

---

## Value Distributions (summary)

| Field | Dominant value | Notes |
|-------|---------------|-------|
| Marital Status | Married (slight majority) | Roughly 55/45 split |
| Gender | Near equal | ~50/50 |
| Education | Partial College (largest group) | 265 of 1,000 records |
| Occupation | Clerical (largest group) | — |
| Region | Europe (largest) | North America second, Pacific smallest |
| Cars | 1–2 cars (most common) | Few own 0 or 4 |
| Children | 0–2 (most common) | — |
| Commute | 0-1 Miles (most common) | 366 of 1,000 records |
