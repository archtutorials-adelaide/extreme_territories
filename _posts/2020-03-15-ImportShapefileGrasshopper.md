---
layout: post
date:   2020-03-15
image: "/extreme_territories/images/tutorial1_tumb.png"
title:  "How to import shapefiles into Grasshopper using Urbano"
author: "Victor Calixto"
---

In this tutorial we are going to explore how to import vector and features data from a shapefile into a Grasshopper definition using [Urbano](https://www.food4rhino.com/app/urbano) plugin. We assume that you already have installed [Rhino 6](https://www.rhino3d.com/download) as well as completed Rhino and Grasshopper online tranning from the Assessement 3A from [Archistar Academy](https://academy.archistar.ai/) on Rhino and Grasshopper Essentials.
Therefore, this tutorial is divided in three parts:

1. Installing software dependencies 
1. Preparing shapefiles in QGIS
1. Import shapefiles into Grasshopper

### 1. Installing software dependencies 

This tutorial uses three plugins:

* **[Urbano](https://www.food4rhino.com/app/urbano)** which is a Urban Design Grasshopper plugin that for mobility and utilisation analisys of amenities, streets, and public spaces. Also, we can use it to import shapefiles into our Grasshopper definition.

* **[Bifocals](https://www.food4rhino.com/app/bifocals)** it will be used to display at the same time names and icons of components on the Grasshopper canvas. It is a great resource for who are starting to use Grasshopper.

* **[Legend_Settings](https://github.com/archtutorials-adelaide/extreme_territories/raw/master/assets/Legend_Settings.ghuser)** it is a grasshopper cluster built for this discipline to provide settings parameters for a legend based on `Gradient` component.

#### 1.1 Installing Urbano and Bifocals

To install **Urbano** go to [`https://www.food4rhino.com/app/urbano`](https://www.food4rhino.com/app/urbano) and register on the site to have access to the download files. After register and login, download `Urbano v1.0 Installer` and executes the file to install.

Go to [`https://www.food4rhino.com/app/bifocals`](https://www.food4rhino.com/app/bifocals) and download `Bifocals Installer`. Run it to install **Bifocals** plugin.

#### 1.2 Installing Legend Settings (ghuser)

To install the *Legend Settings* component, download [`Legend_Settings.ghuser`](https://github.com/archtutorials-adelaide/extreme_territories/raw/master/assets/Legend_Settings.ghuser) into your computer, then open Rhino and Grasshopper and go to `File > Special Folder > User Object Folder` and copy `Legend_Settings.ghuser` in this folder. After that, close and open Rhino and Grasshopper again, It should appers on Grasshopper panel `Extreme Territories`.

![](/extreme_territories/images/install_legend.gif?raw=true)

### 2. Preparing shapefiles in QGIS

Before we start to import our files into Grasshopper, it is important that we select the region that we will work on, avoing  to load unecessary information in your Grasshopper definition. We can prepare our data for the Grasshopper on a **GIS** environment, such as `QGIS` or `ArcMap`.  

In this tutorial we are going to use `QGIS`; however, this procedure can be done through a similar way on `ArcMap`.

First, we need to create a new file on `QGIS` and insert the layers that we want to import into Grasshopper. Here we are going to use the `Suburbs_Territory`and `Street_Network_2019`, both files are part from the provided dataset `Datasets_LARCH7031_Part_1` in the discipline. To insert the layers go to `Layer > Add Vector layer` click on `...` and choose `Suburbs_Territory` click `Add`and `...` choose `Street_Network_2019` click `Add` and close the window.

![](/extreme_territories/images/insert_layers.gif?raw=true)

Second, we need to select the region that we want to work using right click on the layer `Suburbs_Territory`, then  `Open Attribute table` and click on the feature that corresponds to the desired area. The selected area should appers highlighted.

![](/extreme_territories/images/select_attribute.gif?raw=true)


Now we are going to clip the layer `Street_Network_2019` according the selected area. With the area selected go to menu `Vector > Geoprocessing Tool >  Clip`. In the parameter `Input Layer` choose `Street_Network_2019` and `Overlay layer` select `Suburbs_Territory` and check the box bellow `Selected features only`, then click `Run` and choose a folder and a name to the clipped file. A new layer should appers in the layer toolbar with the choosen name.

![](/extreme_territories/images/clip_gemetry.gif?raw=true)

Add other layer, such as `Greenspaces`, and `LandUse` and repite the clip process using `Suburbs_Territory` as `Overlay layer`.

![](/extreme_territories/images/clipped_geometries.gif?raw=true)

Now our files are ready to be imported into Grasshopper.


### 3. Import shapefiles into Grasshopper

Open Rhino and Grasshopper, create a new Grasshopper file and go to `Urbano` table in Grasshopper. 
Under `Urbano` table in the category `Input/Ouput` grab the component `Import Shapefile Features`. Then, go to `Params` table in the `Primitive` category and grab the parameter `File Path`, after that go to `Input`category inside the same `Param`table and grab one `Panel` parameter and write `54H`, which represents the UTM zone for Adelaide.

![](/extreme_territories/images/import_shape_file_urbano.gif?raw=true)


