---
layout: post
date:   2020-03-15
image: "/extreme_territories/images/tutorial1_tumb.png"
title:  "How to import shapefiles into Grasshopper using Urbano"
author: "Victor Calixto"
---

In this tutorial, we are going to explore how to import vector and features data from a shapefile into a Grasshopper definition using [Urbano](https://www.food4rhino.com/app/urbano) plugin. We assume that you already have installed [Rhino 6](https://www.rhino3d.com/download) as well as completed Rhino and Grasshopper online training from the Assessment 3A from [Archistar Academy](https://academy.archistar.ai/) on Rhino and Grasshopper Essentials.
Therefore, this tutorial is divided into three parts:

1. Installing software dependencies 
1. Preparing shapefiles in QGIS
1. Importing shapefiles into Grasshopper

### 1. Installing software dependencies 

This tutorial uses three plugins:

* **[Urbano](https://www.food4rhino.com/app/urbano)** which is an Urban Design Grasshopper plugin that for mobility and utilisation analysis of amenities, streets, and public spaces. Also, we can use it to import shapefiles into our Grasshopper definition.

* **[Bifocals](https://www.food4rhino.com/app/bifocals)** it will be used to display at the same time names and icons of components on the Grasshopper canvas. It is a great resource for who is starting to use Grasshopper.

* **[Legend_Settings](https://github.com/archtutorials-adelaide/extreme_territories/raw/master/assets/Legend_Settings.ghuser)** it is a grasshopper cluster built for this discipline to provide settings parameters for a legend based on `Gradient` component.

#### 1.1 Installing Urbano and Bifocals

To install **Urbano** go to [`https://www.food4rhino.com/app/urbano`](https://www.food4rhino.com/app/urbano) and register on the site to have access to the download files. After register and login, download `Urbano v1.0 Installer` and executes the file to install.

Go to [`https://www.food4rhino.com/app/bifocals`](https://www.food4rhino.com/app/bifocals) and download `Bifocals Installer`. Run it to install **Bifocals** plugin.

#### 1.2 Installing Legend Settings (ghuser)

To install the *Legend Settings* component, download [`Legend_Settings.ghuser`](https://github.com/archtutorials-adelaide/extreme_territories/raw/master/assets/Legend_Settings.ghuser) into your computer, then open Rhino and Grasshopper and go to `File > Special Folder > User Object Folder` and copy `Legend_Settings.ghuser` in this folder. After that, close and open Rhino and Grasshopper again, It should apper on Grasshopper panel `Extreme Territories`.

![](/extreme_territories/images/install_legend.gif?raw=true)

### 2. Preparing shapefiles in QGIS

Before we start to import our files into Grasshopper, it is important that we select the region that we will work on, avoiding to load unnecessary information in your Grasshopper definition. We can prepare our data for the Grasshopper on a **GIS** environment, such as `QGIS` or `ArcMap`.  

In this tutorial we are going to use `QGIS`; however, this procedure can be done through a similar way on `ArcMap`.

First, we need to create a new file on `QGIS` and insert the layers that we want to import into Grasshopper. Here we are going to use the `Suburbs_Territory` and `Street_Network_2019`, both files are part of the provided dataset `Datasets_LARCH7031_Part_1` in the discipline. To insert the layers go to `Layer > Add Vector layer` click on `...` and choose `Suburbs_Territory` click `Add` and `...` choose `Street_Network_2019` click `Add` and close the window.

![](/extreme_territories/images/insert_layers.gif?raw=true)

Second, we need to select the region that we want to work using right-click on the layer `Suburbs_Territory`, then  `Open Attribute table` and click on the feature that corresponds to the desired area. The selected area should appear highlighted.

![](/extreme_territories/images/select_attribute.gif?raw=true)


Now we are going to clip the layer `Street_Network_2019` according to the selected area. With the area selected go to the menu `Vector > Geoprocessing Tool >  Clip`. In the parameter `Input Layer` choose `Street_Network_2019` and `Overlay layer` select `Suburbs_Territory` and check the box bellow `Selected features only`, then click `Run` and choose a folder and a name to the clipped file. A new layer should appear in the layer toolbar with the chosen name.

![](/extreme_territories/images/clip_gemetry.gif?raw=true)

Add other layers, such as `Greenspaces`, and `LandUse` and do the process again the clipping using `Suburbs_Territory` as `Overlay layer`.

![](/extreme_territories/images/clipped_geometries.gif?raw=true)

Now our files are ready to be imported into Grasshopper.


### 3. Importing shapefiles into Grasshopper

Open Rhino and Grasshopper, create a new Grasshopper file and go to `Urbano` table in Grasshopper. 
Under `Urbano` table in the category `Input/Output` grab the component `Import Shapefile Features`. Then, go to `Params` table in the `Primitive` category and grab the parameter `File Path`, after that go to `Input`category inside the same `Param`table and grab one `Panel` parameter and write `54H`, which represents the UTM zone for Adelaide.

![](/extreme_territories/images/import_shape_file_urbano.gif?raw=true)

Connect the `Panel` parameter into `UTM` input of `Import Shapefile Features` component, then right-click on `File Path` parameter and `Select one existent file` choose the clipped `LandUse.shp` which was created on **QGIS** the previous step.

![](/extreme_territories/images/import_urbano2.gif?raw=true)

Then get a `Polyline`component under table `Curve` category `Spline` and connect `pts` output from `Import Shapefile Features` to `Vertices` input  in `Polyline ` component. Hide the preview of `Import Shapefile Features` to visualise the created lines.

![](/extreme_territories/images/LandUse_urbano.gif?raw=true)

To extract the shapefile features use the Urbano component `Deconstruct Metadata`under `Urbano` table category `Metadata`. 
Connect the output `Metadata` of`Import Shapefile Features` component in the input `Metadata` of `Deconstruct Metadata` component.
The outputs will be divided into `Keys` and `Values`, organised in a data tree structure.

![](/extreme_territories/images/Extract_Metadata_urbano.gif?raw=true)

Now we can start to import the other shapefiles following the same previous steps.
However, when we import new shapefiles it is important that all the information match each other.
To do that use the **output** `Translation Vector` from the first `Import Shapefile Features` component to correct the others `Import Shapefile Features`, connecting in the **input** `Translation Vector` which carries other shapefiles imported.

![](/extreme_territories/images/Correct_vectors_urbano.gif?raw=true)

Then we need to clean the values and geometries that become invalid during the clipping process. First, we `Flatten` the `Polyline`output which are organised in branches, then we restructure the `data tree` using `Graft`component, isolating each polyline geometry in a different list. Then, we use  `Clean Tree` component to clean the invalid geometry, including empty branches. `Clean tree component` is located under`Set > Tree > Clean Tree`. Then, we use the component `Tree statistics` to extract all the branches names with valid geometry to use as a reference for the output `Values` from the `Deconstruct Metadata`  component. Finally, we use the `Tree Branch` component to select the valid features that match the valid polylines. The **output** `Paths`from `Tree statistics` in the **input** `Path` of `Tree Branch` and the output `Values` from `Deconstruct Metadata` in the input `Tree` of `Tree Branch`. Now our data is cleaned to be manipulated.

![](/extreme_territories/images/cleaning_data_tree.gif?raw=true)

So, the process to import shapefiles in Grasshopper finished, then we can start to manipulate the data to generate or extract the information that we want.
For example, we can extract the number of dwelling that for each polyline that we have using the `index 0` of a  `List Item` component. 

![](/extreme_territories/images/number_dwellings.png?raw=true)


Then we can use that information to generating a gradient map based on the number of dwellings for each polyline.
To do that we can extract the **high** and **low** number in our list as a domain with the component `Bounds` which is located under `Maths > Domain > Bounds` before we connect our list in the bounds we need to `Flatten` the branches in a single list. Then, we deconstruct this domain using the component `Deconstruct Domain`located under `Maths > Domain > Deconstruct Domain`. We are going to use the `Gradient`component to build our gradient map, it is located under `Params > Input > Gradient`. Right-click in the `Gradient`component and `Presets` to choose the colour pattern to Red to BLue. It is important to notice that the pattern will be inverted to match the highest value in *red* and the lowest value in *blue*.so to do that we need to connect our `Ènd` output value from `Deconstruct Domain` in the `Lower Limit`value of the `Gradient` component and the `Start` output value from `Deconstruct Domain` in the `Upper Limit` value of the `Gradient`, then we connect our flattened list of values in the `Parameter` value of the `Gradient`. So, we have already built our gradient map based on the number of dwellings.

![](/extreme_territories/images/gradient-dw.gif?raw=true)


Then we can create a legend for our gradient map using `Legend Settings` located under `Extreme Territories > Display > Legend Settings`. This component ask for a `Legend Origin` as a `Point3d`, the `Legend_Size_x` and `Legend_Size_Y` which is related to the X and Y direction of the Legend Frame, an angle for rotate the legend `Angle_Rotation_Legend (degrees)`, an offset for the title of the legend `Legend_Offset`, the `Gradient Values`, the `Gradient Domain`, the desired number of divisions that your legend will represent `Number_of_divisions`, and which kind of number representation the legend will have `Domain Int (True) / Float (False)`, which can be in Integer (True)  or Float (False) as a boolean condition.

![](/extreme_territories/images/legend_.png?raw=true)

Finally, we can start to play with the other shapefiles. for example, we can move `Greenspaces` and `Street Network` in the Z direction, displacing it into space. To do that we can use the component `Move` component combined with `Unit Z` component and a `Number Slider` with an interactive numeric value for the translation. We can also combine it with Math operations, such as `Multiplication` to parametrically relate the two geometries. Finally, we can use the component `Custom Preview` and `Colour Swatch`to change the colours of our geometries.

![](/extreme_territories/images/shp_other_params.gif?raw=true)

So, we have finished our first tutorial on how to import shapefiles in Grasshopper using Urbano.
The Grasshopper definition of this tutorial can be downloaded [here](/extreme_territories/assets/import_urbano.gh).


