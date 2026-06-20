Spatial Intelligence for Housing

This repository contains the production-grade, object-oriented Python codebase used to process, clean, and enrich regional housing data for deployment into **Esri ArcGIS Online** and the interactive **ArcGIS StoryMap** ecosystem.

## 🔗 Live Interactive Map & StoryMap
The full analytical review, interactive web maps, and regional breakdowns are published and fully accessible here:
👉 **[Spatial Intelligence for Housing StoryMap](https://storymaps.arcgis.com/stories/f59512cff20a4ebeb8b14570cfbae7fa)**

---

## 📌 Project Overview
This pipeline acts as the spatial data engineering backbone for Bellway's North West and Manchester Divisions. It automates the preparation of localized planning authority datasets to drive strategic land appraisal applications.

The application harmonizes geographic layers with two key metrics:
1. **Housing Delivery Test (HDT) Scores (2023 Measurement):** Sourced from the Ministry of Housing, Communities & Local Government (MHCLG), tracking delivery requirements, net completions, and National Planning Policy Framework (NPPF) consequences (*Presumption, Action Plan, Buffer, or Pass*).
2. **Residential Property Values (2025 Index):** Sourced from HM Land Registry (UK House Price Index Price Paid Data), identifying high-value concentrations and market premium indicators.

---

## 🏗️ Architecture & Clean Code Design (OOP)
The codebase has been refactored into a strict **Object-Oriented Programming (OOP)** design to ensure modularity, maintainability, and clean separation of concerns[cite: 2]:

* **`Config`**: Single source of truth managing target coordinates, National Planning Policy thresholds, regional division mapping (Manchester vs. North West LPAs), and styling parameters[cite: 2].
* **Data Loaders (`HDTLoader`, `HousePriceLoader`, `BoundaryLoader`)**: Dedicated atomic classes responsible for multi-format ingestion (ODS tables, standard CSV indices, and zipped shapefile polygons) with built-in data type normalization and a fallback mock generation matrix if local files are missing[cite: 2].
* **`NorthWestDataMapper`**: Handles relational intersections and spatial attribute joins, calculating percentages and embedding explicit color themes[cite: 2].
* **`MapPlotter`**: Generates dual-canvas diagnostic thematic visual charts via `matplotlib` (Side-A: HDT Consequence, Side-B: Residential Price Heatmap with higher values flowing to lighter greens)[cite: 2].
* **`GeoJSONExporter`**: Re-projects data streams to `EPSG:4326` (WGS 84) and formats schemas directly for seamless ingestion into **ArcGIS Online / Esri Feature Layers**[cite: 2].

---

## 📂 Data Sources & Directory Structure
To run the automated synchronization pipeline, ensure your local directory environment matches the following scheme[cite: 2]:

```text
├── Housing_Delivery_Test_2023_measurement.ods  # MHCLG Official Release
├── May2025CouncilBoundaries.zip               # ONS Local Administrative Districts
└── House_Planning/
    └── House_Prices.csv                       # HM Land Registry Price Paid Data (2025)
