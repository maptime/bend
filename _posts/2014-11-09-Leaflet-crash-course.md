---
layout: post
title: "The fault in our parks: Leaflet mapping crash course"
date: 2014-11-09 14:19:11
author: Andy Zeigert
---

## Creating a Leaflet map and adding some data

Perhaps you've had some experience putting together Google maps using lists of addresses or other kinds of location information, but you're interested in the nitty gritty of creating a map using open-source tools. This tutorial is intended to quickly familiarize you with the tools needed to make custom maps using open-source data. 

### What we'll be using

The main tool we'll be using is [Leaflet.js](http://leafletjs.com "Leaflet.js"), a javascript library that lets you quickly build a map using just a text editor. Any text editor will do, but it helps to use one that's designed for editing code. A good, free editor is [Brackets](http://brackets.io "Brackets"). The other thing you'll probably want to have is a [Github](https://github.com "Github") account. You won't need it to write any of the code, but it's a good place to keep code and data, and you can make a copy (or clone) [the data used in this project](https://github.com/MaptimeBend/faultparks) right to your own account.

For data, we'll be using a polygon layer of Bend Parks & Recreation District properties and a polyline layer of fault lines that run through Central Oregon, both stored in GeoJSON files. JSON stands for JavaScript Object Notation, and it's basically an easy-to-read format for storing data in a way that javascript can readily access. The Geo part of GeoJSON just means that location data is stored with other item properties.

### 1. Download the data and set up a workspace

The map we'll be building uses static map tiles and then builds vector symbols on top using GeoJSON files. Create a directory called `/faultparks` on your computer. Create a `/data` directory inside. Then, open your code editor and create a new html file and save it to `/faultparks/index.html`.

Download the [data from our Github page]("https://github.com/MaptimeBend/faultparks") and copy the `.js` files to your `/data` folder. Everything else you'll need can be copied from this page.

### 2. Add the necessary code to your `index.html`

In order to create a map on our html page using Leaflet, we need to include the Leaflet javascript library in the head element.

```
<script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
```

We also need to include the Leaflet CSS file in the head element.

```
<link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.css" />
```

Now we need to create a `div` element in our `body` element with a specific `id` that we'll reference in our javascript. Nothing goes into the `div` now, but our javascript will put the map there later.

```
<div id="map"></div>
```

In addition, let's add some CSS to our head element that tells the map to be 400 pixels tall. The width will fill the width of the browser window, or in the case of this page, the parent element, which is this article.

```
<style type="text/css">
#map { 
  height: 600px;
}
</style>
```

Now we'll need to actually write the javascript that creates the map. After our `<div id="map"></div>` element, let's open a script element and start adding the Leaflet-specific javascript that builds the map:

```
  <script type="text/javascript">
    var map = L.map('map').setView([44.05, -121.30], 11);
  </script>
```

The numbers after the `setView` item tell the map that we want it centered on those geographic coordinates (those are near the center of Bend) and that we want the zoom level to be 11 (that's enough to show all of Bend). There are other ways to determine how your map is centered by default, but this is an easy one.

At this point, we technically have a working map. But it will show up with just the zoom buttons and nothing else. We haven't told it want we want to display yet.

An essential item for any webmap is a set of map tiles. Map tiles [are a way](http://wiki.openstreetmap.org/wiki/Tiles "More about map tiles on OpenStreetMap wiki") to break up a map into smaller chunks that are easier for a web browser to load. There are lots of map tile sets that you can use, but let's go with one from [Stamen](http://maps.stamen.com/ "Stamen") for this example.

Add this code to your head tag, just after the Leaflet code:

```
<script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"></script>
```

Now let's create a layer using a Stamen tile set called Toner Lite. It's a nice high-contrast base map that our colored parks and fault lines will stand out on later.

```
var layer = new L.StamenTileLayer("toner-lite");
```

Now we need to tell the page to go ahead and add that layer to our map.

```
map.addLayer(layer);
```

Here's what your index.html page should look like at this point:

{% highlight html %}
<!DOCTYPE html>
<head>
    <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7/leaflet.css" />
    <script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
    <script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"></script>
    <style type="text/css">
    #map {
        height: 600px;
    }
    </style>
</head>
<body>
    <div id="map"></div>
    <script type="text/javascript">
      var map = L.map('map').setView([44.05, -121.30], 11);
      var layer = new L.StamenTileLayer("toner-lite");
      map.addLayer(layer);
    </script>
</body>
</html>
{% endhighlight %}

Congratulations! You've now built a complete Leaflet map. That code should render something like this:

<div id="map1" style="height: 250px"></div>
  <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7/leaflet.css" />
  <script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
  <script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"></script>
  <script type="text/javascript">
    var map1 = L.map('map1', {scrollWheelZoom: false}).setView([44.05, -121.30], 11);
    var layer = new L.StamenTileLayer("toner-lite");
    map1.addLayer(layer);
  </script>

### 3. Adding markers

Leaflet allows you to add symbols to your map just by entering a line of code. For example, this bit of code drops a pin marker in the center of our map view:

```
  var marker = L.marker([44.05, -121.30]).addTo(map);
```

Go ahead, try it. You should get something like this:

<div id="map2" style="height: 250px"></div>
  <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7/leaflet.css" />
  <script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
  <script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"></script>
  <script type="text/javascript">
    var map2 = L.map('map2', {scrollWheelZoom: false}).setView([44.05, -121.30], 11);
    var layer = new L.StamenTileLayer("toner-lite");
    map2.addLayer(layer);
    var marker = L.marker([44.05, -121.30]).addTo(map2);
  </script>
  
The marker symbol is determined by the Leaflet default. You [can customize markers for your map](http://leafletjs.com/reference.html#marker "Marker API on Leafletjs.com"), if you'd like. You can also bind popup information to that marker by adding a little extra code before the final semicolon:

```
var marker = L.marker([44.05, -121.30]).addTo(map)
  .bindPopup('Sort of the center of Bend.')
  .openPopup;
```

Now you can click on the marker and see the popup:

<div id="map3" class="map" style="height: 250px"></div>
  <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7/leaflet.css" />
  <script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
  <script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"></script>
  <script type="text/javascript">
    var map3 = L.map('map3', {scrollWheelZoom: false}).setView([44.05, -121.30], 11);
    var layer = new L.StamenTileLayer("toner-lite");
    map3.addLayer(layer);
    
    var marker = L.marker([44.05, -121.30]).addTo(map3)
    .bindPopup('Sort of the center of Bend.')
    .openPopup;
  </script>
 
We can add lots of markers to our map this way, including lines and polygons (See the [Leaflet tutorials](http://leafletjs.com/examples.html) for more on that), but what we really want to do is load some external data to our map. Feel free to remove that marker from your map now, or leave it if you want.

### 4. GeoJSON basics

From [http://geojson.org](http://geojson.org) (via [Leafletjs.com](http://leafletjs.com/examples/geojson.html)):

> GeoJSON is a format for encoding a variety of geographic data structures. A GeoJSON object may represent a geometry, a feature, or a collection of features. GeoJSON supports the following geometry types: Point, LineString, Polygon, MultiPoint, MultiLineString, MultiPolygon, and GeometryCollection. Features in GeoJSON contain a geometry object and additional properties, and a feature collection represents a list of features.

That really just means that it's a file format for storing geographic data, and Leaflet plays really well with it. Here's an example GeoJSON feature:

```
var geojsonFeature = {
  "type": "Feature",
  "properties": {
      "name": "Juniper Park",
      "popupContent": "Juniper Park in Bend, Oregon"
  },
  "geometry": {
      "type": "Point",
      "coordinates": [44.03, -121.17]
  }
};
```

For this exercise, the GeoJSON files for the Bend parks ( `parks.js` ) and faults ( `faults.js` ) have already been created, and we'll load those into our Leaflet map. They're currently stored in `.js` files because they include the `var =` at the beginning and are loaded as separate scripts. Think of them as separate mini programs that declare the name of the object and then list its contents in GeoJSON. We're basically linking to that in our program.

### 5. Loading the parks and faults

We need to call the `.js` files like we would any other external script, so add this right below your `<div id="map"></div>`:

```
  <script src="data/parks.js"></script>
```

Next we tell our map to load the data onto our map. We pass the name of the variable created at the beginning of our `.js` file, in this case "parks":

```
  L.geoJson(parks).addTo(map);
```

You should end up with something like this:

<div id="map4" style="height: 250px"></div>
<link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7/leaflet.css" />
<script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
<script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"></script>
<script src="{{ site.url }}/bend/assets/data/parks.js"></script>
<script type="text/javascript">
    var map4 = L.map('map4', {scrollWheelZoom: false}).setView([44.05, -121.30], 11);
    var layer = new L.StamenTileLayer("toner-lite");
    map4.addLayer(layer);
    L.geoJson(parks).addTo(map4);
</script>

The parks are there, but they have the default appearance assigned by Leaflet. We can easily change their appearance by passing some options along with `parks`:

```
L.geoJson(parks, {
  style: { // First item in the array is style, whose property is another array containing...
    "fillColor": "green", // Fill and stroke color
    "weight": 0, // Stroke weight, zero here so we just have a fill
    "fillOpacity": 0.6 // This gives the fill a 60% transparency
  } 
}).addTo(map);
```

The last thing we want to do is add the faults. Let's add them and style them all in one step:

```
<script src="data/faults.js"></script> // Add this right below parks.js...
```

```
L.geoJson(faults, { // ...and this right after our previous geoJson call
  style: {
    "color": "red",
    "weight": 1.5,
    "opacity": 0.8
  }
}).addTo(map);
```

This should add our faults layer and give it a slightly transparent red line symbol. Our final map should look something like this:

<div id="map5" style="height: 250px"></div>
<link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7/leaflet.css" />
<script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
<script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"></script>
<script src="{{ site.url }}/bend/assets/data/parks.js"></script>
<script src="{{ site.url }}/bend/assets/data/faults.js"></script>
<script type="text/javascript">
    var map5 = L.map('map5', {scrollWheelZoom: false}).setView([44.05, -121.30], 11);
    var layer = new L.StamenTileLayer("toner-lite");
    map5.addLayer(layer);
    L.geoJson(parks, {
      style: {
        "fillColor": "green",
        "weight": 0,
        "fillOpacity": 0.6
      } 
    }).addTo(map5);
    L.geoJson(faults, {
      style: {
        "color": "red",
        "weight": 1.5,
        "opacity": .8
      }
    }).addTo(map5);
</script>

Congratulations! You've created a nice Leaflet map that lets us compare Bend parks with known fault lines. Note: Most of these fault lines haven't slipped in thousands of years and never did much anyway.

### 6. Extra credit: Adding popups

It's not hard to add another option to our GeoJSON layer calls that picks up info from the GeoJSON properties and displays it in a popup. Let's take a look at our `.js` files and find the properties for the names of each feature. Once we have the property name, we can add it in a popup quite easily:

```
    L.geoJson(parks, {
    style: {
      "fillColor": "green",
      "weight": 0,
      "fillOpacity": 0.6
    },
    onEachFeature: function (feature, layer) {
      layer.bindPopup(feature.properties.Park_Name);
    }
  }).addTo(map);
```
  
The property for each feature in the GeoJson file is "Park_Name". So we're telling the map that for each feature, look at its properties and display the one called "Park_Name." We'll do the same for the faults, except in this case the fault name is under the property "NAME."

```
    L.geoJson(faults, {
      style: {
        "color": "red",
        "weight": 1.5,
        "opacity": .8
      },
      onEachFeature: function (feature, layer) {
        layer.bindPopup(feature.properties.NAME);
      }
    }).addTo(map);
```

This gives us a map that shows Bend's parks and the faults that run through them, and we can click on each feature to see its name.

<div id="map6" style="height: 250px"></div>
<link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7/leaflet.css" />
<script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
<script type="text/javascript" src="http://maps.stamen.com/js/tile.stamen.js?v1.3.0"></script>
<script src="{{ site.url }}/bend/assets/data/parks.js"></script>
<script src="{{ site.url }}/bend/assets/data/faults.js"></script>
<script type="text/javascript">
  var map6 = L.map('map6', {scrollWheelZoom: false}).setView([44.05, -121.30], 11);
  var layer = new L.StamenTileLayer("toner-lite");
  map6.addLayer(layer);
  L.geoJson(parks, {
    style: {
      "fillColor": "green",
      "weight": 0,
      "fillOpacity": 0.6
    },
    onEachFeature: function (feature, layer) {
      layer.bindPopup(feature.properties.Park_Name);
    }
  }).addTo(map6);
  L.geoJson(faults, {
    style: {
      "color": "red",
      "weight": 1.5,
      "opacity": .8
    },
    onEachFeature: function (feature, layer) {
      layer.bindPopup(feature.properties.NAME);
    }
  }).addTo(map6);
</script>

This tutorial only scratches the surface of the Leaflet javascript library. Leaflet is designed to be easy to learn and quick to implement, and above all is completely open source.