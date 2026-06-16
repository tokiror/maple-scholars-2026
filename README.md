# maple-scholars-2026

Undergraduate research: satellite data analysis of drought and natural water reservoirs in East Africa

---

## Overview

This project investigates the natural water "reservoirs" — groundwater, soil moisture, and seasonal wetlands — that sustain or end droughts in Kongwa District, central Tanzania. Kongwa is a largely rain-fed agricultural region with very little irrigation or built water storage, which makes it an ideal place to ask: when the rain stops, what holds water in the landscape, and how does the area recover?

The research is motivated by a public-health link. A previous study in the region found that a drought appeared to end earlier than rainfall alone could explain, coinciding with a measured drop in crop mycotoxins (toxins produced by fungi under crop stress). If a natural water source eased that drought sooner than expected, understanding it could have implications for food safety and water management across similar dryland farming regions.

**Researcher:** [Your Name]
**Faculty Mentor:** Prof. Paul Meyer Reimer (Physics)
**Institution:** Goshen College

---

## Research Question

What natural water reservoirs sustain or end droughts in Kongwa District, and can changes in satellite-measured water storage help explain the early drought recovery observed in prior research?

---

## Data Sets

**Raw GRACE / GRACE-FO (NASA JPL MASCON)**
Satellite measurements of total water storage anomaly (TWSA), derived from tiny changes in Earth's gravity field. Extracted via Google Earth Engine. Native resolution is coarse (~3 degrees). Units: centimeters of equivalent water height; baseline 2004–2010.

**GRACE-SeDA (Gou & Soja, 2024, Nature Water)**
A deep-learning-downscaled GRACE product that sharpens the blurry satellite signal to 0.5 degree resolution by fusing it with the WaterGAP global hydrology model. Primary dataset for the fine-scale analysis. Monthly, 2002–2022. Units: millimeters; baseline 2004–2009.
DOI: https://doi.org/10.3929/ethz-b-000648738

**SPEI (SPEIbase, CSIC)**
The Standardised Precipitation-Evapotranspiration Index, a drought severity measure. Accessed via Google Earth Engine at 0.5 degree resolution, monthly. Used to relate drought conditions to water-storage changes.

**Tanzania administrative boundaries**
District and regional boundary data used to define the Kongwa study area and provide map context.

**Kongwa health facility locations**
A dataset of 50 health facilities across Kongwa District, including coordinates and number of mothers served, used to map the public-health geography of the study area.

---

## Study Sites

- **Kongwa District** — the main rain-fed study area (resolved as 4 pixels in the downscaled data)
- **Lake Sulunga** — a large seasonal lake/wetland
- **Mtera Reservoir** — a major built hydroelectric reservoir, used as a comparison site where a strong water signal is expected

---

## Methods & Skills Used

**Satellite remote sensing**
Working with GRACE/GRACE-FO gravimetry to interpret water storage from gravity measurements, and understanding the resolution limits that determine how finely the data can resolve a region like Kongwa.

**Machine learning (applied)**
Applying a published deep-learning downscaled dataset (a convolutional neural network trained with a self-supervised approach) to sharpen coarse satellite data. The project applies and interprets this method rather than training the model from scratch.

**Scientific data processing (Python)**
Opening and processing NetCDF climate data with xarray; decoding non-standard time formats (Modified Julian Date); cleaning physically impossible artifact values; clipping global data to a study region; building and exporting time series.

**Google Earth Engine (JavaScript & Python API)**
Loading and visualizing geospatial datasets; extracting region-specific time series; mapping point data; building interactive map layers with custom styling, opacity, and legends.

**Geospatial analysis**
Identifying which data pixels cover a study area, working with latitude/longitude grids, and understanding how pixel ground-size changes with distance from the equator.

**Data visualization**
Producing clear time-series charts with Matplotlib and interactive maps in Google Earth Engine.

---

## Repository Contents

- `grace_seda_water_storage_tanzania.ipynb` — Main notebook: extracts and plots downscaled GRACE water-storage time series for Kongwa, Lake Sulunga, and Mtera Reservoir
- `grace_raw_kongwa.ipynb` — Earlier notebook: raw GRACE west/east Kongwa time-series analysis
- `kongwa_twsa_map.js` — Google Earth Engine script: visualizes downscaled water storage over Tanzania with Kongwa marked
- `kongwa_hospitals_map.js` — Google Earth Engine script: maps the 50 Kongwa health facilities, sized by number of mothers served

---

## Key Findings & Observations (in progress)

- The downscaled data resolves Kongwa as four distinct pixels, showing a measurable spatial gradient in water storage across the district.
- Water storage rises sharply across the region beginning around 2019–2020.
- Raw and downscaled GRACE products show differing amplitudes over Kongwa; reconciling this (related to scaling-factor and baseline treatment) is ongoing.

---

## Tools & Environment

- **Python** (xarray, pandas, NumPy, Matplotlib, rioxarray) — data processing and plotting
- **Google Colab** — cloud notebook environment
- **Google Earth Engine** — geospatial data access and interactive visualization
- **Git / GitHub** — version control and project backup

---

## References

- Cuthbert, M. O. et al. (2019). Sub-Saharan Africa groundwater recharge and resilience. Nature.
- Gou, J. & Soja, B. (2024). Global high-resolution total water storage anomalies from self-supervised data assimilation using deep learning. Nature Water, 2, 139–150. https://doi.org/10.1038/s44221-024-00194-w
- Kashani, A. & Safavi, H. R. (2025). Assessing groundwater drought using GRACE data and machine learning. Scientific Reports, 15, 14671.
- MacDonald, A. M. / Sanga et al. (2018). Weathered crystalline basement aquifers, East Africa. Hydrogeology Journal.
- NASA JPL GRACE / GRACE-FO mission. https://grace.jpl.nasa.gov
