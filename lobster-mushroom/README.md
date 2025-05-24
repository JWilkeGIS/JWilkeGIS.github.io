# Lobster Mushroom Habitat Suitability Analysis  
*Modeling Suitable Habitat for Hypomyces lactifluorum in Northern Arizona*

## Overview
This GIS project identifies suitable habitats for the lobster mushroom (*Hypomyces lactifluorum*) using terrain, vegetation, and climate data. These fungi parasitize Russula and Lactarius mushrooms and are prized by foragers for their distinctive flavor and appearance.

The goal was to create a habitat suitability model in QGIS using publicly available datasets and raster-based analysis techniques.

## Objective
- Identify areas in Northern Arizona most likely to support lobster mushroom growth.
- Integrate environmental variables including elevation, vegetation cover, NDVI, and seasonal precipitation.
- Produce a clear and visually informative suitability map.

## Study Area
The analysis focuses on high-elevation forests of Northern Arizona, particularly areas within the Coconino and Kaibab National Forests known for monsoon moisture and mixed conifer ecosystems.

![Map Preview](HypomycesLactifluorum-project.png)

## Tools Used
- QGIS 3.x
- Raster Calculator
- Slope & Reclassify tools
- Python (limited PyQGIS for automation)

## Geoprocessing Workflow

1. **Data Collection**
   - Elevation: NASA SRTM
   - Land Cover: USGS NLCD
   - NDVI: MODIS (July–September composite)
   - Precipitation: PRISM Climate Group

2. **Preprocessing**
   - All rasters reprojected to EPSG:5070 (Albers Equal Area)
   - Clipped to study extent

3. **Suitability Criteria**
   - **Elevation** between 2000–2800m  
   - **NDVI** > 0.6 during monsoon months  
   - **Land Cover**: filtered for forest types  
   - **Slope** under 30° (optional refinement)

4. **Raster Combination**
   - Reclassified rasters (1 = suitable, 0 = unsuitable)
   - Used Raster Calculator to combine layers with equal weight
   - Final output is a binary suitability raster

## Results
The final map highlights suitable zones in shaded forested regions above 2000 meters, especially those that receive monsoon precipitation and show high vegetative vigor.

View the full report: [HypomycesLactifluorum-project.pdf](HypomycesLactifluorum-project.pdf)

## Data Sources

| Dataset | Source | Link |
|--------|--------|------|
| Elevation | NASA SRTM | [earthdata.nasa.gov](https://earthdata.nasa.gov/) |
| NDVI | MODIS Terra | [modis.gsfc.nasa.gov](https://modis.gsfc.nasa.gov/) |
| Land Cover | USGS NLCD | [mrlc.gov](https://www.mrlc.gov/) |
| Precipitation | PRISM | [prism.oregonstate.edu](https://prism.oregonstate.edu/) |

All datasets were used under open data or public domain terms.

## Limitations
- NDVI values were derived from limited summer imagery.
- No ground-truthing or field validation of mushroom presence.
- Model does not include host mushroom range (e.g., Russula sp.).

## License
This project is open source under the MIT License.

## Credits
Created by John Wilke  
Special thanks to the open data providers and QGIS developer community.
