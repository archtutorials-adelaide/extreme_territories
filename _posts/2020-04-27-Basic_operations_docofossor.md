---
layout: post
date:   2020-04-27
image: "/extreme_territories/images/basicOperations/logodocofossor.png"
title:  "Docofossor Terrain Manipulation Components - Basic Operations"
author: "Juliana Croffi Calixto"
---

### 1. Operation with curves

These components will use curves to modify the terrain mesh.

#### 1.1.	Fill on Path

Located on `Docofossor > Operations Relative > Fill on Path`


![](/extreme_territories/images/basicOperations/COMPONENT_LOCATION_1.jpg?raw=true)


* Docofossor List `(df)` will be THE LAST input that you will connect.
* First you will need to draw a curve in Rhino where you want to modify the terrain.

In Grasshopper, use the Curve parameter to reference your curve: right-click on the `curve parameter> Select one curve > click on the curve that you draw`. 

* The next input is the maximum height at the centre `(mxh)`. Give it a value for the height that you want
* The next input is the Width `(wt)` at the top of the hill you are creating.
* The input Slop Angle `(sa)` is the angle, in degrees, of the slop.
* You can have two different slops, for each side of the curve. If you give a value to the input `"sa2"` it will assign the value for the slop on the right side of the curve. If you don’t give any value to it, by default it will use the same value from `"sa"`.
* The input Maximum Distance `(d)` is the maximum distance of the slop from the curve.
* After setting up all the inputs of the component you will connect the Docofossor List to the input `“df”`. Wait for it to run. Connect the output from Fill on Path to the component Grid Mesh to visualise the modified mesh.


![](/extreme_territories/images/basicOperations/GIF_01.gif?raw=true)

Modify the Maximum height at the centre `(mxh)`

![](/extreme_territories/images/basicOperations/GIF_02.gif?raw=true)

Modify the Width `(wt)`

![](/extreme_territories/images/basicOperations/GIF_03.gif?raw=true)

Modify the Slop Angle `(sa)`

![](/extreme_territories/images/basicOperations/GIF_04.gif?raw=true)

Modify the Maximum Distance `(d)`

![](/extreme_territories/images/basicOperations/GIF_05.gif?raw=true)

#### 1.2 Fill in Path

Located on `Docofossor > Operations Absolute > Fill in Path`

![](/extreme_territories/images/basicOperations/COMPONENT_LOCATION_2.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* This component is quite similar to the previous one. 

In this component the height of the hill you are creating will be attached to the curve that you are using as input. Move up the curve and modify it if you want. 

* Give a value to the Width `(wt)` that you want at the top.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the Grid Mesh to visualise the modification.

![](/extreme_territories/images/basicOperations/GIF_06.gif?raw=true)

* Modify the Width, Slops, Maximum Distance.

![](/extreme_territories/images/basicOperations/GIF_07.gif?raw=true)
