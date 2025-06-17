# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an R-based data science project creating a business case for iNaturalist-Esri collaboration. The analysis compares sensitive species occurrence data from California's CNDDB (California Natural Diversity Database) with GBIF biodiversity data to demonstrate iNaturalist's value for environmental compliance.

## Key Commands

### Document Rendering
- `quarto render analysis.qmd` - Render main analysis document to HTML/PDF
- `quarto render gbif_download.qmd` - Render GBIF download workflow
- `quarto preview analysis.qmd` - Live preview during development

### R Development
- Open `living-atlas-inaturalist-integration.Rproj` in RStudio for interactive development
- Use R chunk execution in RStudio or VS Code with Quarto extension
- Environment variables stored in `.Renviron` (contains GBIF API credentials)

## Architecture

### Core Analysis Workflow
1. **Data Preparation** (`analysis.qmd`):
   - Loads CNDDB shapefile (`data/gis_com/cnddb.shp`) with 104,435 sensitive species records
   - Cleans and normalizes species names, removing taxonomic modifiers
   - Handles complex date parsing from various SITEDATE formats

2. **GBIF Integration** (`gbif_download.qmd`):
   - Matches species names to GBIF backbone taxonomy using `rgbif`
   - Downloads occurrence data for California (filtered by bounding box)
   - Requires GBIF credentials: `GBIF_USER`, `GBIF_PWD`, `GBIF_EMAIL`

3. **Data Processing Pipeline**:
   - Species list generation → GBIF name matching → bulk download → filtering → analysis
   - Handles large datasets (10M+ occurrence records efficiently using `data.table`)

### Key Data Sources
- **CNDDB**: `data/gis_com/cnddb.shp` - California sensitive species database (primary reference)
- **GBIF Download**: `data/0050088-250525065834625.csv` - 10.5M occurrence records
- **Processed Outputs**: 
  - `data/cnddb_species_list.csv` - Cleaned species names
  - `data/gbif_good_matches.csv` - Successfully matched taxonomy
  - `data/gbif_download_info.csv` - Download metadata

## Code Conventions

### R Style
- Use 2 spaces for indentation (configured in .Rproj)
- Follow tidyverse conventions with `dplyr` pipes
- Spatial data operations use `sf` package consistently
- Date handling with `lubridate` for complex SITEDATE parsing

### Data Processing Patterns
- Large dataset operations use `data.table` for performance
- Spatial filtering applied early to reduce memory usage
- Species name cleaning removes taxonomic authorities and modifiers
- Strict coordinate validation (remove records without lat/lon)

### Quarto Documents
- Use `code-fold: true` for clean presentation
- Cache computationally expensive chunks with `cache: true`
- Include both HTML and PDF output formats
- Embed resources for standalone documents

## Critical Notes

- **GBIF API Limits**: Downloads are rate-limited and may take hours for large requests
- **Memory Management**: Load large datasets incrementally, use `data.table` for 10M+ records
- **Spatial Data**: All coordinate operations assume WGS84 (EPSG:4326)
- **Species Matching**: Manual verification recommended for critical taxonomic matches
- **California Focus**: All analyses filtered to California bounding box (-124.7, 32.3, -114.1, 42.0)