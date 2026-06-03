# Changelog

All notable changes to this project are documented here.

---

## [1.0.0] — June 2026

### Added
- Raw dataset (`Bike Buyers`) with 1,000 customer records across 13 fields
- Cleaned dataset (`WORK FIELD!`) with expanded categorical labels
- 9 pivot tables covering all KPI and metric dimensions (`Pivot Gear!`)
- Interactive dashboard with 4 KPI cards, 3 pivot charts, and 3 slicers
- Executive summary with 6 key insights and 6 strategic recommendations
- KPI planning sheet (`KPIs & Metrics!`)
- README with full project documentation
- Data dictionary (`docs/data-dictionary.md`)
- Methodology notes (`docs/methodology.md`)

### Known issues in this release
- Chart titles implemented as floating text boxes (not native chart title properties)
- Age group chart uses line chart type (column chart would be more appropriate)
- Education/occupation pivot has an active filter limiting view to Partial College only
- Raw data duplicated across two sheets rather than using formula-linked expansion
