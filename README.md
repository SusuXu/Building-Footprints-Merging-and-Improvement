# Building Footprints Tutorial (ArcGIS Pro Version)

Author: Runyu Gao (rgao18@jhu.edu)

## Overview

This tutorial outlines the process of working with open-sourced building footprints, including downloading, converting, preprocessing, and merging data. Additionally, it covers generating building footprints in regions without open-source data, finding historical world basemap imagery, and rasterizing building footprints. Blue blocks indicate the geoprocessing tool to be used in ArcGIS, and yellow blocks represent the parameters for each tool. The underlined steps provide detailed guidance within this tutorial.

![Example Image](https://github.com/SusuXu/Building-Footprints-Merging-and-Improvement/blob/main/TutorialPics/pic1.png "Overall Workingflow")

## Tutorial Steps

### 1. Download and Convert Building Footprints

- **Microsoft Building Footprints:** [Tutorial Link](https://colab.research.google.com/drive/14L1KgiGlaIWCoTUJCo6jOu-yt_gr0J00?usp=sharing)
- **Google Open Buildings:** [Tutorial Link](https://colab.research.google.com/drive/1t7GGe8Fyf0ufsZJxDvDsGjJIn4zwLEMO?usp=sharing)
- Convert the downloaded data to GeoJSON format.

### 2. Convert GeoJSON to Shapefile

- In ArcGIS Pro, use the **JSON To Features** Tool. Set the Geometry Type Parameter to **Polygon**.
  
![Example Image](https://github.com/SusuXu/Building-Footprints-Merging-and-Improvement/blob/main/TutorialPics/pic2.png "JSON To Features")

### 3. Preprocess Google Open Buildings Data

- Filter by confidence score. Like extracting building footprints with a confidence score threshold of **0.85**.
  
![Example Image](https://github.com/SusuXu/Building-Footprints-Merging-and-Improvement/blob/main/TutorialPics/pic3.png "Filter Option")

### 4. Merge Building Footprints from Different Sources

- Use the **Join Feature tool** to find intersections of different sources.
- Apply the **Pairwise Erase tool** to filter target sources by the intersection.
- Utilize the **Merge tool** to combine filtered sources into one.
  
![Example Image](https://github.com/SusuXu/Building-Footprints-Merging-and-Improvement/blob/main/TutorialPics/pic4.png "Step 4 Tools")

### 5. Eliminate Overlaps in Merged Dataset

- To address overlaps, find the union of overlapping building footprints.
- First, apply the **Repair Geometry Tool**, then use the **Pairwise Dissolving Tool** to avoid errors.
  
![Example Image](https://github.com/SusuXu/Building-Footprints-Merging-and-Improvement/blob/main/TutorialPics/pic5.png "Step 5 Tools")

### 6. Generate Building Footprints in Uncovered Regions

- Install the Deep Learning Library from [Esri's GitHub](https://github.com/Esri/deep-learning-frameworks/blob/master/README.md?rmedium=links_esri_com_b_d&rsource=https%3A%2F%2Flinks.esri.com%2Fdeep-learning-framework-install).
- Download the Deep Learning Tool Packages:
    - **USA:** [Package Link](https://www.arcgis.com/home/item.html?id=a6857359a1cd44839781a4f113cd5934)
    - **China:** [Package Link](https://www.arcgis.com/home/item.html?id=979cb0cf938946bfb8bb2f41cf9f9795)
    - **Africa:** [Package Link](https://www.arcgis.com/home/item.html?id=979cb0cf938946bfb8bb2f41cf9f9795)
    - **Australia:** [Package Link](https://www.arcgis.com/home/item.html?id=4e38dec1577b4b7da5365294d8a66534)
- Use the **Detect Objects Using Deep Learning** tool with specific parameters for input layer, suppression, target region coordinates, and cell size.
- Post-generation, apply the **Regularize Building Footprint tool** for polygonization, selecting the Right Angle only method as appropriate.
  
![Example Image](https://github.com/SusuXu/Building-Footprints-Merging-and-Improvement/blob/main/TutorialPics/pic6.png "Step 6 Tools")


### 7. Find Historical World Basemap Imagery

- Access historical basemap imagery via [Living Atlas](https://livingatlas.arcgis.com/wayback/).
- Download map tiles or open directly on Living Atlas for your target region and timestamps.

### 8. Rasterize Building Footprints

- Utilize the **Polygon to Raster Tool**.
- Clip to target extent and use the Con tool to generate a binary map.
  
![Example Image](https://github.com/SusuXu/Building-Footprints-Merging-and-Improvement/blob/main/TutorialPics/pic8.png "Step 8 Tools")

