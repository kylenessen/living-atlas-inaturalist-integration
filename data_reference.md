# Data Structure Reference

## CNDDB Shapefile Structure

**File**: `data/gis_com/cnddb.shp`
**Records**: 104,435
**Columns**: 42

### Key Fields

| Field | Type | Description | Sample Values |
|-------|------|-------------|---------------|
| SNAME | chr | Scientific name | "Gopherus agassizii" |
| CNAME | chr | Common name | "desert tortoise" |
| ELMCODE | chr | Element code | "ARAAF01012" |
| OCCNUMBER | int | Occurrence number | 1, 3, 4, 30, 23... |
| TAXONGROUP | chr | Taxonomic group | "Reptiles", "Mammals" |
| ACCURACY | chr | Location accuracy | "specific area" |
| PRESENCE | chr | Presence status | "Presumed Extant" |
| OCCTYPE | chr | Occurrence type | "Natural/Native occurrence" |
| OCCRANK | chr | Occurrence rank | "Good", "Unknown" |
| SENSITIVE | chr | Sensitive flag | "N", "Y" |
| SITEDATE | chr | Site observation date | "20040412", "1987XXXX" |
| FEDLIST | chr | Federal listing status | "Threatened", "None" |
| CALLIST | chr | California listing status | "Threatened", "None" |
| GRANK | chr | Global rank | "G3", "G4T3", "G1" |
| SRANK | chr | State rank | "S2S3", "S3", "S1" |
| CDFWSTATUS | chr | CDFW status | "FP", "SSC" |
| LOCATION | chr | Location description | Text descriptions |
| THREAT | chr | Threat descriptions | Text descriptions |
| AREA | dbl | Area in square meters | Large numeric values |
| geometry | MULTIPOLYGON | Spatial geometry | Polygon coordinates |

### Important Notes
- Contains both point and polygon occurrences
- Covers multiple taxonomic groups (Reptiles, Mammals, etc.)
- Includes federal and state conservation status
- Has temporal data (observation dates)
- Contains threat assessment information
- Spatial data in projected coordinate system (likely UTM or State Plane)