# hw/01 — Data

This folder contains 4 digital elevation models (DEMs), each a single-band GeoTIFF.
They are the input files for the assignment (extracting contours from a DEM with a TIN).

## Overview

| file                | area                              | CRS (EPSG)                       | resolution | size (px)   | elevation range (m) | nodata     | file size |
|---------------------|-----------------------------------|----------------------------------|------------|-------------|---------------------|------------|-----------|
| `Swiss_DHM200.tif`  | Switzerland                       | CH1903 / LV03 (21781)            | 200 m      | 1926 × 1201 | 193 – 4557          | -9999      | ~9.3 MB   |
| `brazil.tif`        | Rio de Janeiro, Brazil            | SAD69 / Brazil Polyconic (29101) | ~30 m      | 1194 × 624  | -17 – 995           | -32768     | ~1.5 MB   |
| `dem_01.tif`        | Tasmania, Australia               | GDA2020 / MGA zone 55 (7855)     | ~33.4 m    | 550 × 505   | 0 – 971             | -1.7e+308  | ~0.6 MB   |
| `dem_01_warped.tif` | Tasmania (same area, other CRS)   | GDA2020 / Australian Albers (9473) | ~33.5 m | 618 × 551   | 0 – 970             | -1.7e+308  | ~2.7 MB   |

All values are elevations in metres; the horizontal units of all four CRSs are also metres.

## Files

### `Swiss_DHM200.tif`

The Swiss national digital height model ([DHM200](https://www.swisstopo.admin.ch/en/height-model-dhm200)) at 200 m resolution,
covering all of Switzerland (approx. 5.83°E–10.98°E, 45.66°N–47.87°N).
It contains the terrain height (without buildings/vegetation), from 193 m (Lake Geneva area) up to 4557 m in the Alps.

### `brazil.tif`

A DEM of ~30 m resolution of the Rio de Janeiro area in Brazil (approx. -43.37°E–-43.01°E, -23.00°N–-22.81°N).
It contains the steep terrain of the city and its granite peaks, up to ~995 m; a few hundred pixels have slightly negative values (down to -17 m), ie water surfaces (ocean/bay/lagoons).

### `dem_01.tif`

A DEM of ~33.4 m resolution of an area northwest of Hobart, Tasmania, Australia (approx. 147.06°E–147.29°E, -42.83°N–-42.68°N).
It is stored as `float64`, which means nodata is set to the minimum float value (-1.7e+308).

### `dem_01_warped.tif`

The same DEM as `dem_01.tif`, but warped/reprojected to the projected CRS GDA2020 / Australian Albers (EPSG:9473).
It is useful to test that your program handles different CRSs correctly (the coordinates and the grid dimensions differ from `dem_01.tif`) and for `nodata` values.
