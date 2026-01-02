# Language Endangerment Analysis

**Date:** January 2, 2026

## Overview

This analysis explores global language data with a focus on geographic distribution and endangerment status. The analysis uses spatial data visualization to map languages across the world and examines patterns of language endangerment, particularly in the United States.

## Data Sources

The analysis uses three main datasets:

1. **languages** - Core language data (8,612 languages)
   - Language ID, name, and geographic coordinates
   - Macroarea (geographic region)
   - ISO 639-3 codes
   - Countries where spoken
   - Language isolate status and family information

2. **endangered_status** - Endangerment classifications (8,567 languages)
   - Status codes (1-6)
   - Status labels (not endangered, threatened, shifting, nearly extinct, moribund, extinct)

3. **families** - Language family information (4,832 families)

## Analysis Steps

### 1. Data Preparation

- Transformed the `languages` dataframe into a spatial (sf) dataframe using latitude and longitude coordinates
- Used WGS 84 coordinate reference system (CRS 4326)
- Filtered out 312 languages with missing coordinates
- Final spatial dataset: **8,300 languages** with valid geographic coordinates

### 2. Data Integration

- Merged `endangered_status` with `languages_sf` by language ID
- All 8,300 spatial languages now have associated endangerment status information

### 3. Global Visualization

Created an interactive leaflet map showing all languages worldwide:
- Color-coded by macroarea (geographic region)
- Interactive popups with language details
- Legend showing macroarea classifications
- See: `map_global_by_macroarea.html`

### 4. United States Focus

Filtered the dataset to languages in the United States:
- **301 languages** found in the US
- Includes continental US, Alaska, Hawaii, and Pacific territories
- Geographic span: 70.11°N to -17.81°S latitude, -174.29°W to 177.77°E longitude

### 5. US Endangerment Analysis

Created a detailed map of US language endangerment status:
- See: `map_us_by_status.html`

#### US Language Endangerment Summary

| Status | Count | Percentage |
|--------|-------|------------|
| Extinct | 147 | 48.8% |
| Shifting | 49 | 16.3% |
| Nearly extinct | 39 | 13.0% |
| Moribund | 34 | 11.3% |
| Not endangered | 18 | 6.0% |
| Threatened | 13 | 4.3% |
| Unknown | 1 | 0.3% |

**Key Findings:**
- Nearly **half (49%) of US languages are extinct**
- An additional **41%** are in various stages of endangerment (shifting, nearly extinct, or moribund)
- Only **6% of US languages** are classified as "not endangered"
- The vast majority (94%) of indigenous US languages face some level of threat or have already disappeared

## Visualizations

Three interactive HTML maps were generated:

1. **map_global_by_macroarea.html** - Global language distribution colored by geographic region
2. **map_us_by_status.html** - US languages colored by endangerment status

## Technical Details

**R Packages Used:**
- `tidyverse` - Data manipulation and transformation
- `sf` - Spatial data handling
- `leaflet` - Interactive map visualization

**Coordinate Reference System:**
- WGS 84 (EPSG:4326) - Standard latitude/longitude coordinates

## Future Analysis Suggestions

- Compare endangerment patterns across different macroareas
- Analyze the relationship between language family and endangerment status
- Examine temporal trends in language endangerment
- Investigate correlations between geographic isolation and endangerment risk
- Compare US patterns with other countries or regions
