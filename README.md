# Fishery data analysis

## 1. What is this about ?

I am trying to pull together data from various sources regarding the state of the marine environment around UK.


## 2. Datasets

### Currently used datasets

European marine zones: 
http://geo.ices.dk/download.php?dataset=ices_ref:ices_areas

ICES catch data:
http://www.ices.dk/marine-data/dataset-collections/Pages/Fish-catch-and-stock-assessment.aspx


### Other datasets

ICES Fish catch by time, species and zone:
http://www.ices.dk/marine-data/dataset-collections/Pages/Fish-catch-and-stock-assessment.aspx

ICES data collections:
http://ices.dk/marine-data/dataset-collections/Pages/default.aspx

Marine Biodiversity Network: 
https://data.nbn.org.uk/Documentation/NBN_Gateway_Documentation/User_How_Tos/Downloading_records/#Downloadingrecords

National Weather Archive:
http://www.metoffice.gov.uk/learning/library/archive

MMO Marine plan areas: http://webarchive.nationalarchives.gov.uk/20140507202222/http://www.marinemanagement.org.uk/marineplanning/areas/index.htm

Fisheries archive: http://webarchive.nationalarchives.gov.uk/20140108121958/http://www.marinemanagement.org.uk/fisheries/statistics/annual_archive.htm


## 3. Assumptions

- We will use a timescale of one year.
- The time frame we are looking at spans from 2006 to 2012
- All the location data will be splitted in tiles of 10km that map to the UK grid.
- We assume that the fish uptake on the marine areas is distributed linearly.


## 4. Findings

**The coordinate system**

The datasets from NBN use the Ordonance Survey Grid letter notation to describe position (example: SR826222).
http://en.wikipedia.org/wiki/Ordnance_Survey_National_Grid#Grid_letters

You can transform this into British National Grid Coordinate system EPSG:27700.
From EPSG:27700 you can transform to EPSG:4326 (GPS coordinates - WGS 84).


## 5. Progress

I have downloaded the Shapefile that describes the European marine zones:
http://geo.ices.dk/download.php?dataset=ices_ref:ices_areas

I have exported the information about the EU marine zones and their areas into a table:
https://www.google.com/fusiontables/DataSource?docid=1IrnP_ctEv35_VRhJhuNS1u9f0ExKqTDQtQpViCOt

Using QGIS, I have transformed the data into EPSG:27700 coordinate system and gridded the area into 10km tiles.
I have computed the area of each tile and added it as a separate attribute.
I have added two new columns **XCoord_10k** and **YCoord_10k** that represents the index of the tile.

I have inserted the gridded data of the EU marine areas around Uk into the following table:
https://www.google.com/fusiontables/DataSource?docid=1Pd2mBJXCjsPVcH29A4gHHcao5WckIsgkYgN2WM6H

From the Fusion tables, I have exported them to CSV and then imported the data into BigQuery tables.

The BigQuery tables contain the following:
 - The gridded tiles for the marine zones around UK
 - List of all the ICES zones and their areas
 - A table with all the catch data from the ICES zones, by year, specie, zone.
 - List of all the species and their scientific name
 
I have derived a table from the original ICES catch table that only contains data for the UK marine zones.

Next step is to add data fron the National Biodiversity Network.


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
  
  
  
