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

## GBIF Name Matching Results

**Source**: `gbif_download.qmd` - GBIF backbone taxonomy matching
**Records**: 3,174 matches
**Columns**: 26

### Key Fields

| Field | Type | Description | Sample Values |
|-------|------|-------------|---------------|
| usageKey | int | GBIF usage key | 2685524, 8613939... |
| scientificName | chr | Full scientific name with authority | "Abies amabilis Douglas ex J.Forbes" |
| canonicalName | chr | Canonical scientific name | "Abies amabilis" |
| rank | chr | Taxonomic rank | "SPECIES" |
| status | chr | Taxonomic status | "ACCEPTED", "SYNONYM" |
| confidence | int | Match confidence score | 96-99 |
| matchType | chr | Type of match | "EXACT", "FUZZY" |
| kingdom | chr | Kingdom | "Plantae" |
| phylum | chr | Phylum | "Tracheophyta" |
| order | chr | Order | "Pinales" |
| family | chr | Family | "Pinaceae" |
| genus | chr | Genus | "Abies" |
| species | chr | Species binomial | "Abies amabilis" |
| synonym | lgl | Is this name a synonym | FALSE, TRUE |
| acceptedUsageKey | int | Key for accepted name if synonym | NA, 2685524... |
| is_alternative | lgl | Is alternative suggestion | FALSE, TRUE |
| verbatim_name | chr | Original input name | "Abies amabilis" |
| verbatim_index | dbl | Index of original name | 1, 2, 3... |

### Important Notes
- Results from matching species names to GBIF backbone taxonomy
- Uses strict matching (no fuzzy matches)
- Contains both accepted names and synonyms
- High confidence matches (96-99%)
- Primarily EXACT match types
- Includes taxonomic hierarchy (kingdom through species)
- Links synonyms to accepted names via acceptedUsageKey
- Filtered results saved separately as "good matches" (exact, non-alternative, valid taxon keys)

## GBIF Occurrence Data

**File**: `data/0050088-250525065834625.csv`
**Records**: 10,567,290
**Columns**: 50

### Key Fields

| Field | Type | Description | Sample Values |
|-------|------|-------------|---------------|
| gbifID | int64 | Unique GBIF occurrence ID | 1213064528, 1270119042... |
| datasetKey | chr | Dataset identifier | "005eb8d8-ed94-41be-89cf..." |
| occurrenceID | chr | Occurrence identifier | "53c88e94-3a39-4f59-beb6..." |
| kingdom | chr | Kingdom | "Animalia" |
| phylum | chr | Phylum | "Mollusca", "Arthropoda" |
| class | chr | Class | "Gastropoda", "Insecta" |
| order | chr | Order | "Lepidoptera", "Chiroptera" |
| family | chr | Family | "Planorbidae", "Plebeiinae" |
| genus | chr | Genus | "Helisoma", "Plebeius" |
| species | chr | Species binomial | "Helisoma newberryi" |
| infraspecificEpithet | chr | Subspecies/variety name | Mostly empty |
| taxonRank | chr | Taxonomic rank | "SPECIES", "UNRANKED" |
| scientificName | chr | Full scientific name with authority | "Helisoma newberryi (I.Lea, 1858)" |
| verbatimScientificName | chr | Original scientific name | "Helisoma newberryi (I. Lea, 1858)" |
| countryCode | chr | Country code | "US" |
| locality | chr | Locality description | "Clear Lake", text descriptions |
| stateProvince | chr | State/province | "California" |
| occurrenceStatus | chr | Occurrence status | "PRESENT" |
| individualCount | int | Number of individuals | 24, 5, 1... |
| decimalLatitude | dbl | Decimal latitude | 39.04450, 35.68000... |
| decimalLongitude | dbl | Decimal longitude | -122.7620, -118.2... |
| coordinateUncertaintyInMeters | dbl | Coordinate uncertainty | Mostly NA |
| elevation | dbl | Elevation in meters | 563.00, mostly NA |
| eventDate | chr | Collection/observation date | "2002-05-24", "2001-07-19" |
| day | int | Day of observation | 24, 19, 8... |
| month | int | Month of observation | 5, 7, 3... |
| year | int | Year of observation | 2002, 2001, 2010... |
| taxonKey | int | GBIF taxon key | 5189725, 9052348... |
| speciesKey | int | GBIF species key | 5189725, 1923057... |
| basisOfRecord | chr | Basis of record | "PRESERVED_SPECIMEN", "HUMAN_OBSERVATION" |
| institutionCode | chr | Institution code | "FMNH", "Colorado State University" |
| collectionCode | chr | Collection code | "Invertebrate Zoology" |
| catalogNumber | chr | Catalog number | "104499", "202040" |
| identifiedBy | chr | Identifier | "Paul Opler" |
| license | chr | Data license | "CC0_1_0", "CC_BY_NC" |
| recordedBy | chr | Collector/observer | "P.Opler", "David Johnson" |
| typeStatus | chr | Type specimen status | "Holotype", mostly empty |
| lastInterpreted | dttm | Last processing date | 2025-06-03 19:50:33... |
| mediaType | chr | Associated media | "StillImage", mostly empty |
| issue | chr | Data quality issues | Various quality flags |

### Important Notes
- Large dataset with over 10 million occurrence records
- Covers multiple taxonomic groups (animals primarily shown)
- Includes specimen and observation records
- Has coordinate data for mapping
- Contains temporal data spanning multiple years
- Includes data quality indicators and issues
- Records from various institutions and collections
- Some fields have high proportion of missing values (NA)
- Data loaded using `data.table::fread()` due to tab-delimited format despite .csv extension