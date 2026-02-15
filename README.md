# Accessibility-Modelling
Repository for article on task-specific quality assessment of global open building datasets (OBDs) using health accessibility modelling. This project evaluates the fitness of four major open building datasets—Google, Microsoft, OSM, and GBA—for spatial analysis in healthcare access studies.
```
data/
├── raw/                      # Original downloaded datasets
│   ├── google_buildings/    # Google Open Buildings
│   ├── microsoft_buildings/ # Microsoft Building Footprints  
│   ├── osm_buildings/       # OpenStreetMap data
│   └── esri_buildings/      # Esri Living Atlas
├── processed/                # Harmonized/cleaned datasets
├── reference/                # Administrative boundaries, study areas
│   └── study_area.geojson   # Your AOI polygon
└── ancillary/                # Supporting data
    ├── health_facilities/    # Hospital/clinic locations
    ├── road_network/         # Transportation networks
    └── population/           # Gridded population data
```

# Dataset Specifications

<img width="2562" height="1265" alt="image" src="https://github.com/user-attachments/assets/04c2462c-db97-4ee1-aeb3-08d04bc5e618" />


# Create directory structure
mkdir -p data/{raw/{google_buildings,microsoft_buildings,osm_buildings,esri_buildings},processed,reference,ancillary/{health_facilities,road_network,population}}

# Download study area boundary (example for Nairobi)
# Add your study area polygon to data/reference/study_area.geojson

# Download health facilities (example using OSM)
python scripts/download_health_facilities.py --city "Nairobi" --output data/ancillary/health_facilities/

# Extract road network
python scripts/download_road_network.py --city "Nairobi" --output data/ancillary/road_network/


# Example data loading in notebook
google_data = gpd.read_file('data/processed/google_buildings_nairobi.geojson')
microsoft_data = gpd.read_file('data/processed/microsoft_buildings_nairobi.geojson')  
osm_data = gpd.read_file('data/processed/osm_buildings_nairobi.geojson')
esri_data = gpd.read_file('data/processed/esri_buildings_nairobi.geojson')
facilities = gpd.read_file('data/ancillary/health_facilities/nairobi_hospitals.geojson')

# Data Sources & Download Instructions
Google Open Buildings: Download via VTP

Microsoft Footprints: GitHub Releases

OSM Data: Geofabrik Downloads

Esri Footprints: Living Atlas

Health Facilities: healthsites.io or OSM

Population Data: WorldPop or GHSL

# Notes
Clip all datasets to your study area before processing to reduce file sizes

Ensure coordinate reference systems match (use EPSG:4326 for consistency)

For large areas, consider tiling or sampling approaches

See scripts/preprocessing/ for harmonization utilities

Add this section to your README to guide users through pr
