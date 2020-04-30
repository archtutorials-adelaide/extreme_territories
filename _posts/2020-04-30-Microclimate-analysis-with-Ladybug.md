---
layout: post
date:   2020-04-30
image: "/extreme_territories/images/microclimate/logodocofossor.png"
title:  "Microclimate analysis with Ladybug"
author: "Juliana Croffi Calixto"
---

### 1. Visualizing Weather Data

#### 1.1 Ladybug_Import EPW (weather file)

This component will import and separate all the weather data from an EPW file. 
The data will be used to perform analysis with Ladybug Located on `Ladybug > 0|Ladybug > Ladybug_Import EPW`


![](/extreme_territories/images/microclimate/LB_01.jpg?raw=true)


* The EPW file must to be in the C: Driver (any folder)
* Right-click on the path, Select an existing file, select the EPW file.
* Connect the path to the `“_epwFile”` input

#### 1.2 Ladybug_SunPath

This component creates a 3D sun-path.
Located on `Ladybug > 2|VisualizeWeatherData > Ladybug_SunPath`

![](/extreme_territories/images/microclimate/LB_GIF_01.gif?raw=true)
 
* The north is set to the Y-axis by default. You can change it connecting a Vector to the input `“_north”`
* Connect to `“_location”` the output `“location”` from the Ladybug_Import EPW component.
* To set the hours of analysis use the sliders connected to the Series components. The start number is the first hour of the day for the analysis and the count number is the amount of hours in sequence.

#### 1.3 Ladybug_WindRose

This component creates a Wind Rose according to the weather data.
Located on `Ladybug > 2|VisualizeWeatherData > Ladybug_WindRose`

![](/extreme_territories/images/microclimate/LB_GIF_02.gif?raw=true)
 
* The north is set to the Y-axis by default. You can change it connecting a Vector to the input `“_north”`
* Connect to `“_hourlyWindDirection”` the output `“WindDirection”` from the Ladybug_Import EPW component.
* Connect to `“_hourlyWindSpeed”` the output `“WindSpeed”` from the Ladybug_Import EPW component.
* Set the Boolean Toggle to True to run the component.


### 2. Environmental Analysis

#### 2.1 SunLight Hours Analysis

This component calculates the number of hours of direct sun-light received by an input geometry using sun vectors from the sunPath component.
Located on `Ladybug > 3| EnvironmentalAnalysis > Ladybug_ SunLight Hours Analysis`

![](/extreme_territories/images/microclimate/LB_GIF_03.gif?raw=true)

* The north is set to the Y-axis by default. You can change it connecting a Vector to the input `“_north”`
* First, let’s reduce the number of mesh face in order to decrease the analysis time. Use the component Remesh Square from the plugin Bison located on `Bison > Mesh > Remesh Square`. 

Increase the dimension of the Grid input do reduce the number of faces of the mesh.

* Connect the reduced terrain mesh to the `“_geometry”` input. 
* Connect to `“_sunVectors”` the output `“sunVectors”` from the Ladybug_sunPath component.
* Set the Boolean Toggle to True to run the component.
* Change the High bound value to match the high bond from the analysis result.
* Change the Gradient index to change the colours of the legend.
* Change the month on the sunPath component and run the analysis again.

#### 2.1.1 Context

* You can use the vegetation as context to see how it affects the sun hours on the terrain analysed.

![](/extreme_territories/images/microclimate/LB_GIF_04.gif?raw=true)

* For this simulation it was used the existing trees generated using points cloud and [image sampler](https://archtutorials-adelaide.github.io/extreme_territories/2020/04/19/ImageSampler-RandomPlanting.html)
