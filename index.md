# OpenStreetMap for ArcGIS

![OpenStreetMap for ArcGIS](https://raw.githubusercontent.com/GASCUK/OpenStreetMap-ArcGIS/master/img/osm_banner_small.png)

This repository provides a means to style OpenStreetMap data imported into ArcGIS using the 
[OpenStreetMap Editor for ArcGIS](http://www.esri.com/software/arcgis/extensions/openstreetmap).

The stylesheet and layers included in the repository have been designed to simplify the process of 
symbolising and displaying OSM data. The style design is based on the 
[OpenStreetMap](http://openstreetmap.org/) humanitarian theme. The original style information can be 
found at [HDM-CartoCSS](https://github.com/hotosm/HDM-CartoCSS) and is derived from 
[CartoCSS](https://github.com/mapbox/carto).

##Workflows
The two workflows walk the user through the process of loading, processing and displaying OSM data in ArcGIS Desktop. 
There are two workflows that can be used:

1. Simplified: A simplified version of the workflow that enables the user to run the process with minimal input using the 
complete OSM load model. The Complete OSM Load model pulls the individual models included in the toolbox together into one 
process. The user selects the input raw OSM data, output file geodatabase, whether a network dataset needs to be 
created and, if so, the network configuration file to be used. 
2. Extended: A more detailed version of the workflow that takes the user through the entire process step by step using the 
individual models included in the toolbox.

##Toolbox
The toolbox contains a number of models required to load and process the raw OSM data, enabling it to be displayed 
correctly in ArcMap. The toolbox is broken down into the individual models for those who wish to process the data 
in stages, or a complete model that pulls the individual models together, allowing the user to run the process from start 
to finish without monitoring.

##Stylesheet
The stylesheet contains symbols for four distinct scale levels. Each zoom level groups one or more of 
the display levels from OpenStreetMap:

1. Display levels 0-10
2. Display levels 11-12
3. Display levels 13-15
4. Display levels 16-19

##Layer files
There are 19 OSM feature layer files included in the repository; one for each of the zoom levels. 
Each layer file contains the specific points, lines and polygon features to be displayed at each level. 
This information was drawn from the CartoCSS MSS files for the OSM humanitarian theme. The features displayed 
at each level draw their symbology from the stylesheet created based on the Nori and Maki icons, designed to 
look as similiar to the OSM humanitarian symbols as possible.

**_Note:_** *There are currently no labels included in the template as the speed that the layers take to 
display is currently being tested. In future, country and captial city labels may be included but more 
detailed labelling such as rivers and roads will probably not be added. The information for the labelling, 
such as feature names, is included in the OSM attributes so it is possible to create labels for projects 
individually in the meanwhile. OSM Humanitarian styled fonts are also available in the stylesheet.*

There are also 2 other layer files included; bathymetry and a dissolved land polygon based on the OSM data. These make 
the resulting map more aesthetically pleasing whilst giving some context to the map, rather than having the downloaded 
country data "floating" at smaller scales.