##Extended workflow

This workflow is a detailed step by step guide to to display OpenStreetMap (OSM) data using the layers and stylesheet provided in this repository. It is 
designed to optimise the speed at which the data is processed and displayed in ArcGIS. It uses the tools provided in the OpenStreetMap Editor for ArcGIS 
toolbox and gives detailed information on exactly what needs to be input for each tool to work correctly.

For a more simplified approach using a custom built model, see the [simplified workflow](simplified.md).

###Downloading the data

1. Download the raw OSM data for the area of interest from [Geofabrik](http://download.geofabrik.de/):
	1. Download the .bz2 compressed OSM file.
	
	2. Unzip the .bz2 file.

_**Important:** The OSM world dataset is so large now that the file geodatabase model is insufficient to store the planet dataset. Smaller geographies - 
continents, countries - are OK. Therefore, it is recommended that you load the smallest .osm file that meets your needs._

###Processing the data

1. In ArcCatalog, open the **Load OSM File** tool in the *ArcGIS Editor for OpenStreetMap* toolset, located in *System Toolboxes* in ArcGIS:

	![Load OSM tool](https://raw.githubusercontent.com/GASCUK/OpenStreetMap-ArcGIS/master/Images/LoadOSMFile.png)
	
	2. Select the unzipped .osm file as the *OSM File*.
	
	3. Create a file geodatabase in your workspace and name the *Target feature dataset* witin it "planet".
 
	4. Expand the optional *Adjust Input Schema* parameter and add the following OSM tag keys to schema:
		* admin_level
		* bridge
		* content
		* craft
		* drinking_water
		* emergency
		* ford
		* generator:source
		* maritime
		* name
		* name:en
		* office
		* oneway
		* pump
		* ref
		* religion
		* seasonal
		* tower:type
		* tunnel
		* The following tags are optional. They are required for a network dataset. Adding these tags at this stage speeds up the creation of the 
		network dataset if it is required:
			* access
			* construct
			* maxheight
			* maxspeed
			* proposed
			* smoothness
			* surface
	
	5. Running this tool results in a feature dataset in the selected file gdb called planet containing three feature classes; planet_osm_ln, planet_osm_ply 
	and planet_osm_pt.
	
2. If a network dataset is required, see [here](network.md) for information on this step.

3. In ArcCatalog, use the **OSM Attribute Selector** tool in the *ArcGIS Editor for OpenStreetMap* toolset on each of the three feature classes in turn 
to extract OSM keys from the tag collection and store them as standalone attributes:
	![OSM Attribute Selector tool](https://raw.githubusercontent.com/GASCUK/OpenStreetMap-ArcGIS/master/Images/OSMAttributeSelector.png)
	1. Select 'EXISTING_TAG_FIELDS' in the *OSM Tag Keys* parameter and run the tool.
<p>
4. Create attribute indexes for each of the three feature classes within the planet feature dataset:

	1. In ArcCatalog, run the **Add Index Attributes** tool on each of the feature classes and select the following for each individual one:
		* **planet_osm_ln**: aeroway, barrier, highway, osm_bridge, osm_ford, osm_seasonal, osmSupportingElement, power, railway, route, waterway.
		* **planet_osm_ply**: aeroway, amenity, building, highway, landuse, leisure, man_made, natural, osmSupportingElement, tourism, waterway.
		* **planet_osm_pt**: amenity, barrier, highway, leisure, man_made, natural, osm_admin_level, osm_content, osm_craft, osm_drinking_water, osm_emergency, 
		osm_generator_58_source, osm_office, osm_pump, osm_religion, osm_tower_58_type, osmSupportingElement, place, power, shop, tourism.

###Completing the data set
1. Add the [Natural Earth bathymetry data](../download/data.md) and the [OSM dissolved land polygon](../download/data.md) to the file geodatabase alongside 
the processed OSM data.

###Displaying the data in ArcMap
1. Download the Humanitarian OSM [stylesheet](../download/styles.md).

2. Open ArcMap and add the stylesheet: *Customize > Style Manager > Styles... > Add Style to List...*

3. Download and unzip the [layers](../download/layers.md) and add them to a new, blank MXD.

4. Arrange the layers in numerical order with the land and bathymetry layers at the bottom of the list:

5. Close ArcMap. Open ArcCatalog and set the MXD data source to the file geodatabase containing the processed OSM data.

6. Reopen the MXD in ArcMap to view the symbolised OSM data.
