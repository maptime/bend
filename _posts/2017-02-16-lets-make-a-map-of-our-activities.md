---
layout: post
title: "Go for a hike|bike|ski|run and make a map"
date: 2017-02-16 22:18:00
author: Blair Deaver
---

### Dreaming of tacky trails.

February is around the time of year in Bend that I begin to get the itch to ride mtn bike trails and go for a hike.  In fact my Garmin GPS unit has been collecting dust...


![Hawaii Map]({{ site.url }}/bend/assets/trail_mapping/lonely_garmin.jpeg "Lonely Garmin")

Today we will take some of your athletic pursuit data that you have collected and try to make a map using QGIS.  We will focus on pulling down data from <a href="https://www.strava.com/">Strava</a> and <a href="https://connect.garmin.com">Garmin Connect</a> since both offer a way to export GPS tracks to GPX and/or Google Earth KML format.


### Pre-requisites

You will need GIS software such as Esri's ArcGIS Pro or QGIS to make a map product.  For today's exercise we will use QGIS.

To install QGIS go to the <a href="http://www.qgis.org/en/site/">home page</a> and click on the "Download Now" button.

![QGIS]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_2_52_05_PM.png "QGIS")

**NOTE:** The file download is around 500 MB.

Once you have installed QGIS you should now have a fancy new application installed under Application or Program Files that awaits your mapping needs.

**Boundless QGIS Installers**

As Andy pointed out in the meetup announcement, another install route is to use the  [Boundless's QGIS installers](http://boundlessgeo.com/solutions/solutions-software/qgis/qgis-download/). Although their release is a couple versions behind the latest QGIS build, they include everything you'll need to get started. Their site also requires you to enter your email address, and then they'll email you a link to the installers. For your convenience, I've done that already and have linked directly to the ZIP archives here:

Windows installer: [Download](https://www.dropbox.com/s/ewlw2lr6md0fdxq/OpenGeoSuite-QGIS-windows-latest.zip?dl=0)

Mac installer: [Download](https://www.dropbox.com/s/vlh8elshnb7175s/OpenGeoSuite-QGIS-osx-latest.zip?dl=0)

### Extracting Data From Strava

Strava is used primarily by cyclists and runners to track activities.  I am sure for most Strava users the mapping interface works well - but since it is MAPTIME we want to make our own maps.

* Login to <a href="https://www.strava.com/">Strava</a>
![Hey look at my Strava Dashboard]({{ site.url }}/bend/assets/trail_mapping/Screen Shot 2017-02-16 at 4.30.07 PM.png "QGIS")
* Strava lets you bulk download data for all your activities!  Go to <b>Settings</b> -> <b>'Download your data'</b>
![Hey look at my Strava Dashboard]({{ site.url }}/bend/assets/trail_mapping/Screen Shot 2017-02-16 at 4.38.39 PM.png "QGIS")
* Strava will send you an email to your account with a zip file of all your activities.

### Extracting Data From Garmin Connect

For those of you using a Garmin device that is not linked to Strava, you can extract data from Garmin's web-based system.

* Login to <a href="https://connect.garmin.com">Garmin Connect</a>
![Hey look at my Garmin Dashboard]({{ site.url }}/bend/assets/trail_mapping/Screen Shot 2017-02-16 at 4.46.45 PM.png "QGIS")
* Navigate to the activity you want to extract.  Export the activity as a GPX file.
![Hey look at my Garmin Data]({{ site.url }}/bend/assets/trail_mapping/Screen Shot 2017-02-15 at 7.30.46 PM.png "QGIS")

### Load data into QGIS

If you have made it here, you are successful!  Unzip either your Strava or Garmin data.

* Login to <a href="https://connect.garmin.com">Garmin Connect</a>
![Hey look at my Garmin Dashboard]({{ site.url }}/bend/assets/trail_mapping/Screen Shot 2017-02-16 at 4.46.45 PM.png "QGIS")
* Navigate to the activity you want to extract.  Export the activity as a GPX file.
![Hey look at my Garmin Data]({{ site.url }}/bend/assets/trail_mapping/Screen Shot 2017-02-15 at 7.30.46 PM.png "QGIS")

***Add the Shapefile to QGIS***

* Launch QGIS
* Click the "Add Vector Layer" button from the Data Toolbar<br>
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen_Shot_2015-01-07_at_4_05_00_PM.png "QGIS FTW")
* Navigate to where you downloaded the City Limits shapefile and select the .shp file.<br>
![QGIS FTW]({{ site.url }}/bend/assets/trail_mapping/Screen Shot 2017-02-16 at 5.00.16 PM.png "QGIS FTW")
* Feel free to add tracks, waypoints, and or routes.
![QGIS FTW]({{ site.url }}/bend/assets/trail_mapping/Screen Shot 2017-02-16 at 5.05.07 PM.png "QGIS FTW")
* You should see several GIS layers including points and lines.
![QGIS FTW]({{ site.url }}/bend/assets/qgis-lets-make-a-map/images/Screen Shot 2017-02-16 at 5.08.43 PM.png "QGIS FTW")

OH AWESOME! Zoom in on this data.  Click the identify tool.  Explore your first dataset you have added to QGIS.

***Check out these awesome QGIS links and tutorials***
I am running time.  We have been here before.  You should check these links!!!

* <a href="http://maptime.io/bend/2015/01/07/lets-make-a-map-with-qgis/">QGIS FTW!</a>
* <a href="https://github.com/AmericanRedCross/workflows/blob/master/qgis_print_composer_tricks.md">Emily Eros' QGIS: Tips and tricks for the print composer</a>



### Added Bonus

Suppose you want to merge ALL of your tract data into one GIS feature (aka Shapefile)....

*Navigate to your uncompressed `activities` folder. (Must have <a href="http://trac.osgeo.org/gdal/wiki/DownloadingGdalBinaries">gdal</a> installed.)

```
for i in $( ls *.gpx ); do ogr2ogr final_gpx.shp -append $i tracks -fieldTypeToString DateTime; done
```

**CONGRATS**
We are all winners today!
![Well done](http://i.giphy.com/11KzAJHqRIbfwY.gif "QGIS FTW")
