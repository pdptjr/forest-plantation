<div>
    <img src='./assets/logo.png' height='auto' width='200' align='right'>
    <h1>Forest Plantation</h1>
</div>

Developed by ***Agrosatélite Geotecnologia Aplicada Ltda***.

## About

This folder contains the scripts to classify and post-process the **Forest Plantation** theme. 

We recommend that you read the [Forest Plantation Appendix of the Algorithm Theoretical Basis Document (ATBD)](https://mapbiomas.org/download-dos-atbds), since important informations about the forest plantation classification methodology can be found in there. 

## How to use

First, you need to copy these scripts (including those in [utils folder](./utils)) to your Google Earth Engine (**GEE**) account.

Then, in your **GEE** account, go to the **Assets tab** and create the following directory structure:

 - MAPBIOMAS/C5/FOREST_PLANTATION/RESULTS

and two **Image Collections**:

 - MAPBIOMAS/C5/FOREST_PLANTATION/RESULTS/**RAW**
 - MAPBIOMAS/C5/FOREST_PLANTATION/**REFERENCE_MAP**

On the **REFERENCE_MAP** collection, you must provide reference maps for the sampling, with pixel values of 1 for sugar cane and 0 for other classes, and a property `year` with the year of the map.

### Classification

To run the classification, follow these steps:

1. Open the script **forest_plantation/classification.js**;

2. On **line 2** (variable `api`), set the path to the [api.js](./utils/api.js) script you copied to your GEE account

3. On **line 7** (variable `outputCollection`), set the output path for the classification results;

4. On **line 10** (variable `years`), set the years you want to classify;
    
5. On **line 17** (variable `tiles`), set the WRS (path and row) you want to classify;
    
6. On **line 36** (variable `periods`), set the periods for the region you want to classify (more information about that you can read on the [ATBD Forest Plantation Appendix](https://mapbiomas.org/download-dos-atbds));
    
7. On **line 55** (variable `imageCollection`), set the Image Collection you want to use to create the mosaics;

8. On **line 58** (variable `referenceCollection`), set the path to your reference map that will be used for sampling;
  
9. Run the script.

### Post-processing

To apply the temporal and spatial filters, follow these steps: 

1. Open the script **forest_plantation/temporal_spatial_filter.js**;

2. On **line 2** (variable `input`), set the input path to the raw classification result;

3. On **line 5** (variable `output`), set the path for the filtered result;

4. On **lines 8 and 9** (variables `startYear` and `endYear`), set the years interval you want to filter;

5. Run the script.