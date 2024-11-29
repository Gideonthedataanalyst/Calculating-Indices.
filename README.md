# Calculating-Indices.

Spectral Indices are central to many aspects of remote sensing. Whether you are studying vegetation or tracking fires - you will need to compute a pixel-wise ratio of 2 or more bands. The most commonly used formula for calculating an index is the Normalized Difference between 2 bands. Earth Engine provides a helper function normalizedDifference() to help calculate normalized indices, such as Normalized Difference Vegetation Index (NDVI). For more complex formulae, you can also use the expression() function to describe the calculation.




1. Image
The image variable is a median composite of Sentinel-2 images that meet the filtering criteria.

What it does:
Combines multiple images from the Sentinel-2 collection into a single image by taking the median value of each pixel across the time range (2019-01-01 to 2020-01-01).
Filters out cloudy pixels using the CLOUDY_PIXEL_PERCENTAGE filter (less than 30% cloud cover).
Covers the geographic bounds of Nairobi, Kenya.
Why it’s useful:
The composite reduces noise caused by clouds or other anomalies and provides a clearer, representative image of the area over the time period.

2. NDVI (Normalized Difference Vegetation Index)
The NDVI is a measure of vegetation health and density based on the reflectance in the Near-Infrared (NIR) and Red bands of Sentinel-2 data.

Formula:
NDVI
=
(
NIR
−
RED
)
(
NIR
+
RED
)
NDVI= 
(NIR+RED)
(NIR−RED)
​
 
Bands used:
NIR (B8): Near-Infrared light, which vegetation strongly reflects.
RED (B4): Red light, which vegetation absorbs for photosynthesis.
Values:
NDVI ranges between -1 and 1:
< 0: Non-vegetative surfaces (e.g., water, urban areas).
0–0.2: Bare soil or sparse vegetation.
0.2–0.8: Healthy vegetation (higher values indicate denser vegetation).
Why it’s useful:
NDVI helps monitor vegetation health, drought, agricultural growth, and land cover changes.

3. SAVI (Soil-Adjusted Vegetation Index)
The SAVI is similar to NDVI but adjusts for the influence of soil brightness, which can affect vegetation readings in areas with sparse vegetation or bare soil.

Formula:
SAVI
=
1.5
⋅
(
NIR
−
RED
)
(
NIR
+
RED
+
0.5
)
SAVI=1.5⋅ 
(NIR+RED+0.5)
(NIR−RED)
​
 
Bands used:
NIR (B8): Near-Infrared.
RED (B4): Red.
Adjustment factor:
The 0.5 in the denominator reduces soil influence in sparse vegetation areas.
Why it’s useful:
SAVI is more accurate than NDVI in areas where soil is visible, such as semi-arid regions or agricultural land during early planting.

4. MNDWI (Modified Normalized Difference Water Index)
The MNDWI highlights water bodies using the reflectance difference between the Green and Shortwave Infrared (SWIR) bands.

Formula:
MNDWI
=
(
GREEN
−
SWIR1
)
(
GREEN
+
SWIR1
)
MNDWI= 
(GREEN+SWIR1)
(GREEN−SWIR1)
​
 
Bands used:
GREEN (B3): Green light, strongly reflected by vegetation and moderately by water.
SWIR1 (B11): Shortwave Infrared, absorbed strongly by water.
Values:
Positive values (typically > 0.1): Water bodies.
Negative or low values: Non-water features like vegetation or soil.
Why it’s useful:
MNDWI is effective for detecting and delineating water bodies, even in urban areas where built-up features might confuse other indices.

Visualization
The visualizations use predefined color palettes:

NDVI: Green represents healthy vegetation.
MNDWI: Blue represents water.
SAVI: Similar to NDVI, highlights vegetation with soil adjustment.
