---
layout: post
date:   2020-04-27
image: "/extreme_territories/images/roboticlandscapes.jpg"
title:  "Docofossor Terrain Manipulation Components - Basic Operations"
author: "Juliana Croffi Calixto"
---

### 1. Operation with curves

These components will use curves to modify the terrain mesh.

#### 1.1.	Fill on Path

This component creates a relative fill along a path curve.
Located on `Docofossor > Operations Relative > Fill on Path`


![](/extreme_territories/images/basicOperation/COMPONENT_LOCATION_1.jpg?raw=true)


* Docofossor List `(df)` will be THE LAST input that you will connect.
* First you will need to draw a curve in Rhino where you want to create the path. In Grasshopper, use the Curve parameter to reference your curve: right-click on the `curve parameter> Select one curve > click on the curve` that you draw. Connect the curve to the curve input `(crv)`
* The next input is the maximum height at the centre `(mxh)`. Give it a value for the height that you want
* The next input is the Width (wt) of the path.
* The input Slop Angle `(sa)` is the angle, in degrees, of the slop.
* You can have two different slops, for each side of the curve. If you give a value to the input `"sa2"` it will assign the value for the slop on the right side of the curve. If you don’t give any value to it, by default it will use the same value from `"sa"`.
* The input Maximum Distance `(d)` is the maximum distance of the slop from the curve.
* After setting up all the inputs of the component you will connect the Docofossor List to the input `“df”`. Wait for it to run. Connect the output from `Fill on Path` to the component `Grid Mesh` to visualise the modified mesh.


![](/extreme_territories/images/basicOperation/GIF_01.gif?raw=true)

Modify the Maximum height at the centre `(mxh)`

![](/extreme_territories/images/basicOperation/GIF_02.gif?raw=true)

Modify the Width `(wt)`

![](/extreme_territories/images/basicOperation/GIF_03.gif?raw=true)

Modify the Slop Angle `(sa)`

![](/extreme_territories/images/basicOperation/GIF_04.gif?raw=true)

Modify the Maximum Distance `(d)`

![](/extreme_territories/images/basicOperation/GIF_05.gif?raw=true)

#### 1.2 Fill in Path

This component creates a trapezoidal fill along a path curve.

Located on `Docofossor > Operations Absolute > Fill in Path`

![](/extreme_territories/images/basicOperation/COMPONENT_LOCATION_2.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.

* In this component the height of the fill you are creating will be attached to the curve that you are using as input `(crv)`. The curve must to be above the terrain mesh. Move up the curve and the control points to modify the fill. 
* Give a value to the Width `(wt)` that you want for the path.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the Grid Mesh to visualise the modification.

![](/extreme_territories/images/basicOperation/GIF_06.gif?raw=true)

* Modify the `Width`, `Slops`, `Maximum Distance`.

![](/extreme_territories/images/basicOperation/GIF_07-min.gif?raw=true)

#### 1.3 Cut on Path

This component creates a relative cut along a path curve.
Located on `Docofossor > Operations Relative > Cut on Path`

![](/extreme_territories/images/basicOperation/IMG_01.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* Draw and reference a Curve to create the path `(crv)`.
* Give a value to the `Maximum Depth` at the centre input `(mxd)`.
* Give a value to the Width `(wt)` that you want for the path.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

#### 1.4 Cut in Path

This component creates a trapezoidal cut along a path curve.
Located on `Docofossor > Operations Absolute > Cut in Path`

![](/extreme_territories/images/basicOperation/IMG_02.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* Draw and reference a Curve to create the path `(crv)`.
* In this component the Depth of the cut you are creating will be attached to the curve that you are using as input `(crv)`. The curve must to be under the terrain mesh. Move down the curve and the control points to modify the cut.
* Give a value to the Width `(wt)` that you want for the path.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

#### 1.5 Cut & fill in Path

This component creates a trapezoidal cut and fill along a path curve.
Located on `Docofossor > Operations Absolute > Cut & fill in Path`

![](/extreme_territories/images/basicOperation/IMG_03.jpg?raw=true)


* Docofossor List `(df)` will be THE LAST input that you will connect.
* Draw and reference a Curve to create the path `(crv)`.
* In this component the depth and the deight of the cut and fill you are creating will be attached to the curve that you are using as input `(crv)`. The curve must cross the terrain mesh. Move down the control points to modify the cut and fill.
* Give a value to the Width `(wt)` that you want for the path.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

### 2. Operation with points

These components will use points to modify the terrain mesh.

#### 2.1 Fill on Point

This component creates relative fill on points as sine curve.
Located on `Docofossor > Operations Relative > Fill on Point`

![](/extreme_territories/images/basicOperation/IMG_04.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* Define the Point `(s)` to create the fill(s) `(pt)`.
* Give a value to the Maximum Height at the centre `(mxh)`.
* Give a value for the slop `(sa)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

#### 2.2 Fill in Point

This component creates fill on points.
Located on `Docofossor > Operations Absolute > Fill in Point`

![](/extreme_territories/images/basicOperation/IMG_05.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* Define the Point(s) to create the fill(s) `(pt)`.
* In this component he height of the fill will be attached to the point(s). The point(s) must to be above the mesh.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

#### 2.3 Cut on Point
This component creates relative cuts on points as sine curve.
Located on `Docofossor > Operations Relative > Cut on Point`

![](/extreme_territories/images/basicOperation/IMG_06.jpg?raw=true)

* This component works the same way as `Fill on Point` to create Cuts instead.

#### 2.3 Cut in Point

This component creates cuts on points.
Located on `Docofossor > Operations Absolute > Cut in Point`

![](/extreme_territories/images/basicOperation/IMG_07.jpg?raw=true)

* This component works the same way as `Fill in Point` to create Cuts instead.

### 3. Operations with Regions and Surfaces.

#### 3.1 Fill on Area

This component creates relative fill within a boundary curve.
Located on `Docofossor > Operations Relative > Fill on Area`


![](/extreme_territories/images/basicOperation/IMG_08.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* Define Boundary Curve to create the fill `(crv)`. The curve must to be planar.
* Give a value to the Maximum Height `(mxh)`.
* Give a value for the slop `(sa)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

#### 3.2 Fill in Surface

This component creates a fill with a given surface.
Located on `Docofossor > Operations Absolute > Fill in Surface`

![](/extreme_territories/images/basicOperation/IMG_09.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* Create a Surface in Rhino and reference it to create the fill `(srf)`. The surface must to be above the mesh.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

#### 3.3 Cut on Area

This component creates relative cut within a boundary curve.
Located on `Docofossor > Operations Relative > Cut on Area`

![](/extreme_territories/images/basicOperation/IMG_10.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* Define Boundary Curve to create the cut `(crv)`. The curve must to be planar.
* Give a value to the Maximum Depth `(mxd)`.
* Give a value for the slop `(sa)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

#### 3.4 Cut in Surface

This component creates a cut with a given surface.
Located on `Docofossor > Operations Absolute > Cut in Surface`

![](/extreme_territories/images/basicOperation/IMG_11.jpg?raw=true)


* Docofossor List `(df)` will be THE LAST input that you will connect.
* Create a Surface in Rhino and reference it to create the fill `(srf)`. The surface must to be under the mesh.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.

#### 3.5 Cut & Fill in Surface

This component creates a cut and fill with a given surface.
Located on `Docofossor > Operations Absolute > Cut & Fill in Surface`

![](/extreme_territories/images/basicOperation/IMG_12.jpg?raw=true)

* Docofossor List `(df)` will be THE LAST input that you will connect.
* Create a Surface in Rhino and reference it to create the fill `(srf)`. The surface must cross the mesh.
* Give a value for the slop `(sa)`.
* Give the maximum distance of the slop `(d)`.
* Connect the Docofossor List `(df)` to run the component, then connect the output to the `Grid Mesh` to visualise the modification.


