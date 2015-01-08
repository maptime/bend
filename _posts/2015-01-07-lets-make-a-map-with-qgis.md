---
layout: post
title: "QGIS FTW!"
date: 2015-1-07 22:18:00
author: Blair Deaver
---

### What is QGIS?

QGIS (previously known as "Quantum GIS") is a cross-platform free and open-source desktop geographic information systems (GIS) application that provides data viewing, editing, and analysis capabilities.

<p>Licensed under the
    <a target="_blank" href="http://www.gnu.org/copyleft/gpl.html">GNU General Public License</a></p>

### QGIS allows you to make maps and more...

QGIS is a powerful software application that allows you to work with Geospatial data (create, read, update, and delete), create maps, visualize data, and perform rich Geospatial analysis.  Below are some examples:

**Map Cartography**
![Hawaii Map]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 11.26.46 AM.png "Hawaii Map")

**Infographics**
![Alt text](https://farm4.staticflickr.com/3889/14812503730_8c43e2dae8_c.jpg)
Source: <a href="http://www.flickr.com/photos/48244569@N02/14812503730/in/pool-qgis-screenshots/">Flickr </a>

### QGIS is a Geospatial Swiss Army Knife

QGIS is a very powerful software application.  With that said the product is very <b> feature </b> rich and is built for GIS users.

![Hawaii Map]({{ site.url }}http://tiwibzone.tiwib.netdna-cdn.com/images/ultimate-swiss-army-knife1.jpg "Hawaii Map")

**Knowing the basics of GIS will be helpful to get started**  If you are new to GIS I would recommend grabbing a fresh cup of coffee and reading <a href="https://github.com/tmcw">Tom MacWright's</a> <a href="http://mapschool.io/">MapSchool</a>.  It is an EXCELLANT read to help you better understand the basics of GIS and cartography.

### QGIS Components

**QGIS Desktop**
![Alt text](http://maptimeboston.github.io/qgis-101/images/qgisdesktopscreenshot.jpg)

**QGIS Browser**
![Alt text](http://maptimeboston.github.io/qgis-101/images/qgisbrowserscreenshot.png)

**QGIS Server**
![Alt text](http://maptimeboston.github.io/qgis-101/images/qgisserverscreenshot.png)

**BETA QGIS Server**
![Alt text](http://maptimeboston.github.io/qgis-101/images/qgisandroidscreenshot.jpg)

For this talk today we are going to focus on using the QGIS Desktop application.

### Getting Started

To install QGIS go to the <a href="http://www.qgis.org/en/site/">home page</a> and click on the "Download Now" button.

![QGIS]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_2_52_05_PM.png "QGIS")

**NOTE:** The file download is around 500 MB.

Once you have installed QGIS you should now have a fancy new application installed under Application or Program Files that awaits your mapping needs.

![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_2_57_28_PM.png "QGIS FTW")

**Boundless QGIS Installers**

As Andy pointed out in the meetup announcement, another install route is to use the  [Boundless's QGIS installers](http://boundlessgeo.com/solutions/solutions-software/qgis/qgis-download/). Although their release is a couple versions behind the latest QGIS build, they include everything you'll need to get started. Their site also requires you to enter your email address, and then they'll email you a link to the installers. For your convenience, I've done that already and have linked directly to the ZIP archives here:

Windows installer: [Download](https://www.dropbox.com/s/ewlw2lr6md0fdxq/OpenGeoSuite-QGIS-windows-latest.zip?dl=0)

Mac installer: [Download](https://www.dropbox.com/s/vlh8elshnb7175s/OpenGeoSuite-QGIS-osx-latest.zip?dl=0)

### QGIS Application - UI

**Let's get familiar with the UI**

***Main UI***

When you first launch QGIS the application should looks similar to the screenshot below:

![Alt text](http://maptimeboston.github.io/qgis-101/images/qgis-ui.png)

***Map Navigation***

![Alt text](http://maptimeboston.github.io/qgis-101/images/map-navigation.png)

The Map Navigation tools can be accessed using the top set of tools.  These tools allow you to zoom, pan, etc.

***File Toolbar***

![Alt text](http://maptimeboston.github.io/qgis-101/images/file-toolbar.png)

***Manage Layers***

![Alt text](http://maptimeboston.github.io/qgis-101/images/add-data.png)

***Attributes Toolbar***

![Alt text](http://maptimeboston.github.io/qgis-101/images/attribute-toolbar.png)

***Layers Panel***

![Alt text](http://maptimeboston.github.io/qgis-101/images/layers-panel.png)

- Access and manage map layers

***Browser Panel***

![Alt text](http://maptimeboston.github.io/qgis-101/images/browser-panel.png)

- Browse local and remote geospatial data.

***Other Panels and More***

![Alt text](http://maptimeboston.github.io/qgis-101/images/other-toolbars.png)

**OK** enough of this intro stuff.  Let's dig in and make a map.

### Let's MAKE A MAP!

**Introduction**<br>
Building on top of our previous meetups I figured that we could take a deeper look into the trail data that exists here in Central Oregon.

Let's start first with downloading some City Limit data from the [Oregon State Geospatial Clearinghouse](http://www.oregon.gov/DAS/Pages/irmd/geo/sdlibrary.aspx).  The Oregon State Geospatial Clearinghouse is a great resource for State level Geospatial data.  Local County and City data can be accessed (sometimes for $) from Deschutes County and the City of Bend.

![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 3.51.20 PM.png "QGIS FTW")

**Bend City Limits**
***Steps to Download Our First Dataset***

* Go to the [Spatial Data Library Alphalist](http://www.oregon.gov/DAS/CIO/GEO/pages/alphalist.aspx)
* Download the [City Limits 2013 Polygon Shapefile](http://navigator.state.or.us/sdl/data/shapefile/k24/citylim_2013.zip)
* Unzip the compressed file to your local machine - you should see several files which as a whole make up a [Shapefile](http://en.wikipedia.org/wiki/Shapefile)

![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.01.43 PM.png "QGIS FTW")

***Add the Shapefile to QGIS***

* Launch QGIS
* Click the "Add Vector Layer" button from the Data Toolbar<br>
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_4_05_00_PM.png "QGIS FTW")
* Navigate to where you downloaded the City Limits shapefile and select the .shp file.<br>
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_4_07_01_PM.png "QGIS FTW")
* You should see a polygon GIS layer with boundaries of Oregon City limits.
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.09.22 PM.png "QGIS FTW")

OH AWESOME! Zoom in on this data.  Click the identify tool.  Explore your first dataset you have added to QGIS.

***Changing Symbology for our City Limits Layer***
I am not sure about you but I am not a fan of the mauve color QGIS randomly selected for my City Limits.  In fact I really only want an outline color and no fill pattern.  Let's explore changing the symbology for our City Limits layer.

* Double click or Right Click (you WindowZ peeps) on the "citylim_2013" layer in the Map Table of Contents.  A Layer Properties Dialog should appear.
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.15.08 PM.png "QGIS FTW")
* Change the Symbol Layer Type to "Outline: Simple Line".  Pick a line color to fit the mood you are in.
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.16.36 PM.png "QGIS FTW")
* I am in the mood for a DASHED line pattern
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_4_18_38_PM.png "QGIS FTW")
* Press Apply.  Your layer symbology should have changed.  You should see the beautiful shape of Bend City Limits.
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.22.23 PM.png "QGIS FTW")

Congrats we now see the lovely shape of our fair city.

**OpenStreetMap Trail Data**

OK. Big deal I see the City of Bend.  I thought we were going to access some trail data.  U BETCHA!

As we learned in our previous meetup OpenStreetMap is a treasure trove of spatial data.  There are many ways to extract.  Today we will try using [Overpass](http://overpass-turbo.eu/) so that we can pull in .geojson data.

* Go to the [Overpass website](http://overpass-turbo.eu/).  Overpass is amazing.  Lets dig deeper.
* I want to extract all lines (known in OSM as ways) that have been tagged as a bike path.
* Zoom to Bend.
* Enter the following text to the left panel
{% raw %}
<osm-script output="json" timeout="25">

  <!-- bike routes -->
  <query type="way">
    <has-kv k="bicycle" regv="^(yes)$"/>
    <has-kv k="highway" regv="^(path)$"/>
    <bbox-query {{bbox}}/>
  </query>



  <!-- print results -->
  <print mode="body"/>
  <recurse type="down"/>
  <print mode="skeleton" order="quadtile"/>
</osm-script>

{% endraw %}
* Run the Query and Export a GEOJSON file
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.48.23 PM.png "QGIS FTW")
* Add the .geojson file that you downloaded to your computer to QGIS.  Symbolize to your heart content.

*NOTE*:  Looks like some of the data in OSM needs to better attributed.

**Let's Add Some Imagery**

One of the AMAZING features of OSM are all the User Plugins available.  Plugins add extra functionality to QGIS.  To complete our map we need some imagery.


* Click on the Plugins menu > Manage Plugins
* Install the OpenLayers Plugin
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_4_52_57_PM.png "QGIS FTW")
* Close the Plugins Dialog.  You should now have a new Toolbar name "Web"
* Choose to add Microsoft's Bing Aerial Map
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.54.50 PM.png "QGIS FTW")
* You may need to drag and drop the layers in your Layer list to move the imagery to the bottom.


**ZOMG -  I AM A CARTOGRAPHER**

OK...Let's make a map.

* Position the map.
* Once positioned the way you want. Go to the Project menu and choose "New Print Composer"
* Give a name for your beautiful new print composition
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.58.40 PM.png "QGIS FTW")
* A whole new Application Window should appear with a Blank Paper Canvas.  This is our MAP!!!
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 4.59.50 PM.png "QGIS FTW")
* Click on the "Add New Map" tool and drag a rectangle representing where you want to add a new map
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_5_01_11_PM.png "QGIS FTW")
* WOAH we have a map.  Feel free to add a title, north arrow, legend and more!
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2015-01-07 at 5.03.42 PM.png "QGIS FTW")


**CONGRATS**
YOU just made your first QGIS Map
![QGIS FTW](http://media.tumblr.com/tumblr_lghpobCmQv1qbw3y0.gif "QGIS FTW")

**Special Thanks**
Thank you MapTimeBoston for your [QGIS-101 tutorial](http://maptimeboston.github.io/qgis-101)  Several images from this presentation are referenced in this lesson.

