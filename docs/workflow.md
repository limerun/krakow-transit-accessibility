# Workflow notes

## Provenance

Based on Dr Tomasz Pirowski's AGH exercise "Podstawy Systemow Informacji Przestrzennej: Analizy rastrowe, cz. 3: operatory odleglosci". The original teaching PDF is retained in the student's private study folder and is not redistributed here.

## Course procedure

1. Inspect the supplied EPSG:2180 population raster, stop rasters, district and urban-unit layers.
2. Calculate distances from stop cells and mask results to the city study area.
3. Reclassify distances into below 100 m, 100-300 m, 300-500 m and 500 m or more; derive a binary 500 m mask.
4. Summarise population and coverage by district and urban unit using zonal statistics / histograms.
5. For nearest-stop allocation, run GRASS `r.cost` using the city mask as a uniform unit-cost raster, and the supplied stop raster as starting cells. Retain the cost-allocation output.
6. Restrict the allocation raster to the 500 m coverage mask, remove background / NoData appropriately, and calculate population totals for allocation zones.
7. Style the saved results and prepare a map with source attribution, CRS, legend and scale.

This describes the supplied exercise, not a complete execution log of the student's session. Exact settings not recorded in the saved files must be checked before claiming a fully repeatable fresh rebuild. In particular, inspect the stop set and its identifiers, pixel alignment, NoData, `r.cost` neighbourhood options and the population aggregation units.

## Inspect saved results

Open `project.qgz`, inspect the layers and attribute tables, and compare the `MPK_map` layout with `outputs/map.png`. The `data/manifest.csv` file distinguishes inputs, retained intermediate files and results. All intermediate files still referenced by the project have been retained; no intermediate dataset was deleted from the original study folder.

## Validation scope

Packaging checks confirm that local data references resolve inside the relocated copy, layers load in QGIS and a saved print layout renders. They do not confirm that the original aggregation is free of double counting, that every zone is defined correctly, or that the method measures real pedestrian accessibility. Those require a separate analytical review.
