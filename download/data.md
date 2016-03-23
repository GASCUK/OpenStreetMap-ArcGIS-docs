##OpenStreetMap data

1. Download the raw OSM data for the area of interest from [Geofabrik](http://download.geofabrik.de/):
	1. Download the .bz2 compressed OSM file.
	
	2. Unzip the .bz2 file.

_**Important:** The OSM world dataset is so large now that the file geodatabase model is insufficient to store the planet dataset. Smaller geographies - 
continents, countries - are OK. Therefore, it is recommended that you load the smallest .osm file that meets your needs._

##Additional data

The Natural Earth bathymetry and the OSM land polygon shapefiles are available for download:

- The bathymetry layers utilise the Natural Earth bathymetry data available at 
[naturalearthdata.com](http://www.naturalearthdata.com/downloads/10m-physical-vectors/10m-bathymetry). Select download all and unzip.
- The dissolved land polygon layer utilises pre-processed OSM available at [openstreetmap.com](http://openstreetmapdata.com/data/land-polygons). Select 
the download for: Format: Shapefile, Projection: WGS84 (large polygons not split).

**Alternatively:**

To make the process easier the dissolved land polygon and bathymetry data have been combined into a file geodatabase that can then have the OSM data 
loaded into it: [download](https://www.dropbox.com/s/wnuhvzh54rmey80/OpenStreetMap.gdb.zip?dl=0). 

_**Note:**_ *The data in this file geodatabase may 
not be up to date. To ensure the most up to date data, please see the source websites, download the latest version(s) and amend the file geodatabase 
as required.*
