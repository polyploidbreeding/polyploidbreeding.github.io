---
layout: post
title: "Using QGIS: basic introduction - 1"
author: "Filippo Biscarini"
date: "2024-05-23"
categories: ['KNOWLEDGE BASE']
tags: ['qgis','images','informatics']
---

## QGIS TUTORIAL - 1

With this post, we begin a super-elementary tutorial on the use of the software package [**QGIS**](https://www.qgis.org/en/site/) for the processing of
geo-referenced image data: QGIS is a free and open-source framework for geographic information system (GIS) data.

A few introductory assumptions:

- we are focussing on the processing of agricultural field images from drone phenotyping
- the starting point is therefore an **orthomosaic** image file generated by combining multiple overlapping photos taken by a camera mountd on a drone
- we take the standpoint of RGB camera and RGB image files (three channels): things will be a bit different with image data from thermic or multi-spectral cameras
- we used QGIS installed on a Debian/Ubuntu Linux distribution (some details may be a bit different if you use another operating system)

For the installation of QGIS and for technical details, you can have a look at the official documentation ([here](https://www.qgis.org/en/site/forusers/download.html)).

There are two basic types of image files that are processed in QGIS: 1) **raster images** (pixel based images), and 2) **vectorial images**.
In this tutorial, in a first instance we will focus on raster images.

### Splitting the orthomosaic in subimages

Let's say that our objective is to extract interesting areas from the orthomosaic: in the case of the **polyploidbreeding project** these will be 
the different field plots where different accessions are planted or treatments applied.
Geo-referenced orthomosaic image files are typically in the `.tiff` format ([tagged image file format](https://en.wikipedia.org/wiki/TIFF)),
accompanied by a `.tfw` file of GIS coordinated ([TFW](https://fileinfo.com/extension/tfw)).

For example, we can look at the image below, where we have three geo-referenced plots that need to be separated for further processing.

<a href="/assets/img/posts/example_fields.jpg"><img src="/assets/img/posts/example_fields.jpg" alt="Example image file of an agricultural field"></a>
<div class="caption"><b>Figure</b>: Example image file of an agricultural field</div>

#### 1. Import the orthomosaic in QGIS

First, we suggest that you **create a QGIS project**: this will make it easier to handle input files, output folders and option setting.
To create a project, once you opened QGIS, you will use the main menu (top bar): 

- i) you click on `Project` > `New`
- ii) `Project` > `Save`: choose a **location** (**directory**) and a **name** where to save the project; this will create a `.qgz` file
- iii) <u>useful tip</u>: go to `Project` > `Properties` and sett the `Project home` folder; this will make it much easier to browse for input/output files and folders

Now that we have our QGIS project, we can import the orthomosaic image file (a single image of the whole agricultural field): 
from the software menu bar: `Layer` > `Add Layer` > `Add Raster Layer`, and **select the input .tiff/.tif image file**.

#### 2. The shape file

The second ingredient of geo-referenced image file analysis is the **shape file**: this is a file that indicates the boundaries of the areas of interest in the image file, i.e. the experimental plots in our example.

The shape file may be already available (from the preprocessing of drone-phenotyping images), or can be designed by the user. We take this second case, in this first post on QGIS and the processing of orthomosaic image files.

To make a **new shape file** in QGIS we can do the following:

1. `Layer` > `Create Layer` > `New Shapefile Layer`:
	- here you specify the file name (and location/filename of where to save it for future use)
	- `Geometry type`: e.g. `Polygon` if you need to draw an area (like in the case of field sub-plots)
	- define additional **attributes**: `New field`: i) id (default); ii) name; iii) etc.
2. draw shapes (ares); for this we use the *Editing tool*:
	- `Layer` > `Toggle Editing`
	- now click on the **`Polygon` icon** on the top toolbar
	- using the mouse, now **left-click** on the raster image, in the point where you want to start drawing your shape
	- with the mouse, **keep left-clicking** until you have completed drawing your shape (area)
	- to stop drawing, **right-click** with the mouse
	- a **dialogue box** will now appear: you must add the **attributes**, i.e. the `id` and `name` of each subplot
	- save the shape file: `Layer` > `Save Layer Edits`

You may want to make sure that, besides having created the shapefile layer and saved it within your project, you save the sahpfile layer to an **external shape file**, for future use. 

#### 3. Clip the raster image based on the shape file

Now that we have the orthomosaic raster image file and the shape file, we can **split the orthomosaic into the subplots of interest** based on the shapes drawn in the shape file.
To do so, and save separate files for each subplot, we first need to **select the shape (area) to export**:

1. in the **`Layers` panel** (bottom-left), **right-click on the shapefile layer**, and select `Open Attribute Table`;
2. in the pop-up `Attribute Table`, **select the desired shape** by **clicking on it** (it will be highlighted, e.g. in blue)
3. now, from the top menu: `Raster` > `Extraction` > `Clip Raster by Mask Layer`:
	- select the raster image as **input layer**
	- select the shapefile layer as **mask layer**
	- **flag the `Selected feature only` option* (<u>this is important</u>: it will clip only the selected shape from the Attribute Table)
	- **click on `Run`**
4. once the clipped shape has been extracted, you have to save it to an external file, by **right-clicking on the corresponding layer** (bottom-left panel of the GUI), and selecting `Save as`
	
<a href="/assets/img/posts/qgis_gui.png"><img src="/assets/img/posts/qgis_gui.png" alt="Screenshot of the QGIS GUI"></a>
<div class="caption"><b>Figure</b>: Screenshot of the QGIS graphical user interface</div>


Now we have three image files for the three subplots in the original orthomosaic image: job done!

<a href="/assets/img/posts/block1.png"><img src="/assets/img/posts/block1.png" alt="subplot of field"></a>
<a href="/assets/img/posts/block2.png"><img src="/assets/img/posts/block2.png" alt="subplot of field"></a>
<a href="/assets/img/posts/block3.png"><img src="/assets/img/posts/block3.png" alt="subplot of field"></a>

### What's next?

All right, we learnt how to read the orthomosaic, make the shape file and use it to split the orthomosaic into the relevant subplots.
Still, a couple of challenges are immediately obvious:

1. the process outlined above is pretty laborious: can we **automate the splitting of the orthomosaic** into the subplot images?
2. the geo-referenced orthomosaic is tilted (this depends on the GIS coordinates): is there a way to **rotate it** if our objective is to extract the subplots?

We'll deal with these issues in our <u>next post</u> of this introductory tutorial to QGIS. 