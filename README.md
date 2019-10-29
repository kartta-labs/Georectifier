# Georectifier
This module first extracts image features (e.g., SIFT) or geographic features (e.g., road intersections or 
road segments) from the input datasets and then establish the correspondence between the two sets of 
extracted features (i.e., a registration). The correspondence is determined by the similarity and spatial 
relationships between the extracted features. This module will then use the determined correspondence to 
transform the raster map to align with the georeferenced dataset and compute a match score based on the 
content consistency after the transformation. 

There are a number of challenges in building this module. First, an image-feature based approach generally 
requires the two input datasets share similar visual cues (e.g., the same building in photos of different 
angles or in consecutive frames in a video), which could be difficult to obtain given that one of the input 
datasets is a historical scanned document. Second, image features can be sensitive to the image types (e.g., 
scanned documents vs. photos vs. digital documents) and hence it might not be straightforward to measure the 
similarity between image features extracted from heterogeneous images. Third, the geographic content can be 
inconsistent between the raster map and the georeferenced datasets (e.g., changes in the road network in 
time). In contrast, a geographic-feature based approach does not suffer from the first and second challenges 
described above (but still have to deal with the third challenge). The challenge for geographic-feature 
based approaches is how to automatically and accurately extract useful geographic features from various 
types of raster datasets (e.g., historical map scans). 

**Input**: a raster map with its approximate location (from Geolocalizer) and a georeferenced dataset (which 
can be georeferenced raster maps, e.g., USGS historical topographic maps, or vector data, e.g., 
OpenStreetMap or Google Maps).

**Output**: 1) a registration between the input map and the georeferenced dataset, which is a set of 
corresponding control point pairs (e.g., { (p1, p1’), (p2, p2’), (p3, p3’), ... (pn, pn’)} where pi 
represents a point in the image coordinates of the raster map (i.e., x and y within the image dimensions) 
and pi’ represent the corresponding point in the geographic coordinate system (i.e., latitude and longitude) 
and 2) a match score.

**Evaluation**: alignment offsets warping results.

