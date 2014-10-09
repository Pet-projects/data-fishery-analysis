# Fishery data analysis

## 1. What is this about ?

I am trying to pull together data from various sources regarding the state of the marine environment around UK.


## 2. Datasets

Marine plan areas: http://webarchive.nationalarchives.gov.uk/20140507202222/http://www.marinemanagement.org.uk/marineplanning/areas/index.htm

European marine plan areas ?: http://ec.europa.eu/fisheries/documentation/publications/poster_tac2012_en.pdf

Fisheries archive: http://webarchive.nationalarchives.gov.uk/20140108121958/http://www.marinemanagement.org.uk/fisheries/statistics/annual_archive.htm



## 3. Assumptions

- We will use a timescale of one month.
- All the location data will be splitted in tiles of 10km.
- We assume that the fish uptake on the marine areas is distributed linearly.


## 4. Findings

**The coordinate system**

The datasets from NBN use the Ordonance Survey Grid letter notation to describe position (example: SR826222).
http://en.wikipedia.org/wiki/Ordnance_Survey_National_Grid#Grid_letters

You can transform this into British National Grid Coordinate system EPSG:27700.
From EPSG:27700 you can transform to EPSG:4326 (GPS coordinates - WGS 84).


## 5. Progress

I have downloaded the Shapefile that describes the Marine plan areas.

Using QGIS I have reduced the complexity of the polygons and converted the file to KML.

I have imported the file into one Google Fusion Table:
https://www.google.com/fusiontables/DataSource?docid=1YQCLtaatdZ2PbxrhMbb3VbPMF5ve3giES_iEgcPt

Using QGIS, I have transformed the data into EPSGL27700 coordinate system and gridded the area into 10km tiles:
https://www.google.com/fusiontables/DataSource?docid=1VhuS54d9G2zDy8vqzVIdsXIvk5NiaQpbeF2tQ8lb

I am working to match the data from fisheries quotas to this marine areas




## 6. Technologies

**QGIS**

 GIS application that also works on OSX. Can be used to view and edit ShapeFiles.
 
 Can be installed from: http://www.kyngchaos.com/software/qgis

**Google Fusion Tables**

  Can be use to store and visualize location data.

**Google Cloud Storage**

  Can be used to store large file before processing them

**Google BigQuery**

  Column-based NoSQL database optimised for fast querying.
  
**AWS Elactic Map Reduce**

  On demand Hadoop cluster using AWS. It gets data from S3 and stores data to S3.
  
  
  
