##Simplified workflow

This workflow is a simplified step by step guide to to display OpenStreetMap (OSM) data using the layers and stylesheet provided in this repository. It is 
designed to optimise the speed at which the data is processed and displayed in ArcGIS. It uses a custom built model based on the OpenStreetMap Editor for 
ArcGIS tools with a number of the required parameters, such as tag names, preprogrammed to aid the user in the process.

For a more detailed workflow showing exactly what happens at each step, see the [extended workflow](extended.md).

###Downloading the data
	
1. Download the raw OSM data for the area of interest from [Geofabrik](http://download.geofabrik.de/):
	1. Download the .bz2 compressed OSM file.
	
	2. Unzip the .bz2 file.

_**Important:** The OSM world dataset is so large now that the file geodatabase model is insufficient to store the planet dataset. Smaller geographies - 
continents, countries - are OK. Therefore, it is recommended that you load the smallest .osm file that meets your needs._

###Processing the data
The simplified workflow uses the **Complete Load OSM Process** model, in the [toolbox](../download/toolbox.md) in this repository. The model loads and 
processes the data with minimal input from the user.

1. **Complete Load OSM Process model:**
	1. Download the [OpenStreetMap Models](../download/toolbox.md) toolbox. Unzip it and locate the unzipped folder in ArcCatalog.
	
	2. Run the **Complete OSM Load Process** model:
	![Complete OSM Load Process model](https://raw.githubusercontent.com/GASCUK/OpenStreetMap-ArcGIS/master/Images/CompleteOSMLoadProcess.png)
	
	3. Select the unzipped .osm file as the *OSM input file*.
	
	4. Create a file geodatabase in your workspace and name the *Target feature dataset* witin it "planet".
	
	5. Select the *Network configuration file* for the creation of the network dataset. This will default to a OpenStreetMap sample file (DriveGeneric.xml).
	Click [here](network.md) for more information on network configuration files.
	
	6. Select whether to *Create OSM network dataset* by checking or unchecking the box.

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