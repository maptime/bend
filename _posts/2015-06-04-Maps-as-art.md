---
layout: event
category: event
title: "Maps are pretty!"
rsvp: "http://www.meetup.com/maptimebend/events/222384845/"
author: Andy Zeigert
published: true
---


The next Maptime Bend meetup is scheduled for Thursday, June 4!

#Maps are a powerful tools, but sometimes they can be gosh-darn nice to look at, too
 
Join the Maptime Bend crew as we take a look at some of the more creative map styles developed using Mapbox Studio and CartoCSS!

We will: 

1. Take a quick look at Mapbox Studio (This will be review for those who remember our February meetup!)

2. Download some example map styles and take a look at the file structure and how Studio uses the files

3. Spend some time customizing our own maps! 

###Important links

Mapbox Studio: [mapbox.com/mapbox-studio](https://www.mapbox.com/mapbox-studio/)

Some cool base styles:
![Woodcut]({{ site.url }}/bend/assets/map_samples/woodcut.png "Woodcut")
[Woodcut](https://github.com/mapbox/mapbox-studio-woodcut.tm2)

![Pirates]({{ site.url }}/bend/assets/map_samples/pirates.png "Pirates")
[Pirates](https://github.com/mapbox/mapbox-studio-pirates.tm2)

![Super Mario]({{ site.url }}/bend/assets/map_samples/super_mario.png "Super Mario")
[Super Mario World](https://github.com/mapbox/super-mario-world.tm2)

![Wheatpaste]({{ site.url }}/bend/assets/map_samples/wheatpaste.png "Wheatpaste")
[Wheatpaste](https://github.com/mapbox/mapbox-studio-wheatpaste.tm2)

![Comic]({{ site.url }}/bend/assets/map_samples/comic.png "Comic")
[Comic](https://github.com/mapbox/mapbox-studio-comic.tm2)

![Pencil]({{ site.url }}/bend/assets/map_samples/pencil.png "Pencil")
[Pencil](https://github.com/mapbox/mapbox-studio-pencil.tm2)

![Picture Book]({{ site.url }}/bend/assets/map_samples/picture_book.png "Picture Book")
[Picture Book](https://github.com/mapbox/mapbox-studio-picture-book.tm2)

![Space Station]({{ site.url }}/bend/assets/map_samples/space_station.png "Space Station")
[Picture Book](https://github.com/mapbox/mapbox-studio-space-station.tm2)

![Winter Wonderland]({{ site.url }}/bend/assets/map_samples/winter_wonderland.png "Winter Wonderland")
[Winter Wonderland](https://github.com/mapbox/mapbox-studio-winter-wonderland.tm2)

![Looseleaf]({{ site.url }}/bend/assets/map_samples/looseleaf.png "Looseleaf")
[Looseleaf](https://github.com/mapbox/mapbox-studio-looseleaf.tm2)

Those were all created by the Mapbox team, and they've made [a bunch more than that](https://github.com/mapbox?page=2&query=.tm2&utf8=✓). And there are so many more out there by folks like us!

###Where do I get the data???

Fortunately, Mapbox has taken the effort to provide users with what is arguably the only data set they'll ever need. Mapbox constantly pulls the latest OpenStreetMap data and sorts it into handy classes for styling. They've also included their own Terrain styles, which include vector terrain information, hillshades and topo lines.

Want to use your own data? No problem. There's a [tutorial for that](https://www.mapbox.com/guides/source-quickstart/).

###Where do I start?!?

Not sure where to start? I've conveniently put all of the above map style documents (they end in .tm2) [into a zip file that you can grab]({{ site.url }}/bend/assets/june_styles.zip).

###OK, what do I do with my map?

You can upload your style to the Mapbox service and use it in [your own projects](https://www.mapbox.com/mapbox.js/api/v2.1.9/). Because of the magic of vector tiles, you can style the entire earth with a pretty small style document.

You can also use the built-in static image export feature in Mapbox Studio to create static images for printing, if you so desire.
