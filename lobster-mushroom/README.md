# Lobster Mushroom Habitat Suitability Analysis  
*Modeling Suitable Habitat for Hypomyces lactifluorum in Northern Arizona*

## Overview
This GIS project identifies suitable habitats for the lobster mushroom (*Hypomyces lactifluorum*) using terrain, land use, and elevation data. These northern Arizona mushrooms are sought after by foragers for their unique flavor and texture.

The goal was to create a habitat suitability model in QGIS using publicly available datasets and raster-based analysis techniques.

## Objective
- Identify areas in Northern Arizona most likely to support lobster mushroom growth.
- Integrate environmental variables including elevation and vegetation cover.
- Integrate other chosen variables including proximity to major roadways and proximity to Northern Arizona University campus.
- Produce a clear and visually informative suitability map.

## Study Area
The analysis focuses on high-elevation forests of Northern Arizona, particularly areas within the Coconino National Forest known for monsoon moisture and mixed conifer ecosystems.

![Map Preview](HypomycesLactifluorum-project.png)

## Tools Used
- QGIS 3.40 Bratislava
- Raster Calculator
- Slope & Reclassify tools

## Geoprocessing Workflow

1. **Data Collection**
   - Base map: OpenStreetMap
   - AZ land use cover: International Centre for Tropical Agriculture (CIAT)
   - SRTM data: CGIAR.org
   - Roadway data: AZGEO open data
   - Manually added point for NAU campus location

2. **Preprocessing**
   - All layers reprojected to WGS 84 / Pseudo-mercator
   - Clipped layers to study extent by adding hand-drawn polygon layer named "Study extent"

3. ** Raster Suitability Criteria**
   - **Elevation** between 6000 - 9000 ft. (converted to meters: 1829 - 2744 meters)
   - **Land Cover**: filtered for "evergreen forest" land use
   - **Slope** under 15% (optional refinement)

4. **Raster Combination**
   - Calculated Hillshade layer from SRTM layer
   - Calculated Slope layer from hillshade layer
   - Calculated raster defining slope less than or equal to 15% (1 = suitable, 0 = unsuitable)
   - Reclassified all rasters (1 = suitable, 0 = unsuitable)
   - Used Raster Calculator to combine layers with equal weight
   - Final output is a binary suitability raster
   - Converted suitability raster to vector layer named "Suitable areas"
  
5. **Vector Analysis**
   -Performed buffer analysis on "Suitable areas" layer to show suitable areas within 1km of Primary Roads layer
   -Used field calculator to calculate and subsequently filter out forested areas under 0.5km squared
   -Performed Near analysis on buffered Suitable Areas to show top 3 candidate locations nearest to NAU

6. **Map Production**
   -Used QGIS layout editor to add map details such as text boxes, title, and other pertinent map details

## Results
The final map highlights suitable zones in evergreen forested regions around NAU campus, with the top 3 candidate locations highlighted in green, and other candidate locations highlighted in orange.

View the PDF: [HypomycesLactifluorum-project.pdf](HypomycesLactifluorum-project.pdf)

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
