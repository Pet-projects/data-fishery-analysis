Fishery data analysis
=

1. What is this about ?
==

I am trying to pull together data from various sources regarding the state of the marine environment around UK.


2. Datasets
==

Marine plan areas: http://webarchive.nationalarchives.gov.uk/20140507202222/http://www.marinemanagement.org.uk/marineplanning/areas/index.htm

Fisheries archive: http://webarchive.nationalarchives.gov.uk/20140108121958/http://www.marinemanagement.org.uk/fisheries/statistics/annual_archive.htm

3. Assumptions
==

- We will use a timescale of one month.
- All the location data will be splitted in tiles of 10 kilometers.
- We assume that the fish uptake on the marine areas is distributed linearly.


4. Process
==

 I have downloaded the Shapefile that describes the Marine plan areas.
 I am working to transform this information into the grid format that we use.



5. Technologies
==

**QGIS**

 GIS application that also works on OSX. Can be used to view and edit ShapeFiles.

**Google Fusion Tables**

  Can be use to store and visualize location data.

**Google Cloud Storage**

  Can be used to store large file before processing them

**Google BigQuery**

  Column-based NoSQL database optimised for fast querying.
  
**AWS Elactic Map Reduce**

  On demand Hadoop cluster using AWS. It gets data from S3 and stores data to S3.
  
  
  
