# Satellite Image Analysis of Novaya Kakhovka

## Overview
This repository contains code used to develop satellite images of the Novaya Kakhovka area following the aggression against the dam by Russia. The objective of this analysis is to assess the damage caused by the incident. The work contributes to the **Satellite Art** project and is co-owned by **Tymoteusz Maj** and **Hubert Debowski**.

## How to Use
1. Clone the repository to your local machine.
2. Open the Google Earth Engine (GEE) code editor.
3. Copy and paste the code from the `main.js` file into the GEE code editor.
4. Run the code to generate and visualize the satellite images of the Novaya Kakhovka area.

## Code Overview
The code consists of three main parts:
1. **Defining the Area of Interest**: A polygon geometry is defined to represent the Novaya Kakhovka area.
2. **Data Collection**: The code downloads Landsat 9 satellite images from specific dates for analysis. It filters the images by cloud cover to ensure clear data.
3. **Image Processing**: The code processes the images, including:
   - Clipping to the defined area.
   - Creating RGB images from the satellite data.
   - Masking clouds and applying brightness and contrast adjustments.
   - Sharpening images and adding spectral channels for better visualization.

### Example Code Snippet
```javascript
// Define the area of interest
var geometry = ee.Geometry.Polygon(
    [[[32.12457614745724, 46.98680414807575],
      [32.12457614745724, 46.40282280396601],
      [33.80823093261349, 46.40282280396601],
      [33.80823093261349, 46.98680414807575]]], null, false);

// Download LANDSAT/LC08/C01/T1_TOA data
var landsatCollection = ee.ImageCollection("LANDSAT/LC09/C02/T1_TOA")
  .filterBounds(geometry)
  .filterDate(startDate, endDate)
  .sort("CLOUD_COVER", true)
  .limit(20);

// Select the median image from the collection
var medianImage = landsatCollection.median();
...
```
## Features

- **Area of Interest:** Defines the geographical area affected by the dam incident.
- **Satellite Image Processing:** Retrieves and processes Landsat images to assess damage.
- **Visualization:** Adds layers to the map for visual analysis of pre and post-damage scenarios.
- **Cloud Masking:** Implements cloud masking to improve image clarity and analysis accuracy.


