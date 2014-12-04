---
layout: post
title: "Getting Started with OpenStreetMap Editing"
date: 2014-12-03 22:18:00
author: Beej Jorgensen
---

What is OSM?
------------

OpenStreetMap is a volunteer project to build a free map of the world.
Started in England, it has spread globally. The United States map is
functionally complete (though mapping is an endless task.)


Editing OSM data
----------------

There are several methods to edit OSM data, but the most popular are the
online [iD editor](http://wiki.openstreetmap.org/wiki/ID), and the
offline [JOSM](https://josm.openstreetmap.de/) editor.

This article focuses on iD.


Legal
-----

OSM is a free map of the world. It's HUGELY IMPORTANT that none of the
data entered into the map is encumbered by copyright. NEVER, NEVER, EVER
use a copyrighted source for map data, unless that source has been
specifically approved by OSM itself.

You are free to trace any roads or entities that you see on the
satellite view in the iD editor due to a legal agreement between OSM and
Bing.

USGS maps and imagery are also free to use, as well as NPS/FS maps.

See the [OSM Legal FAQ](http://wiki.openstreetmap.org/wiki/Legal_FAQ)
for more details.


Setup
-----

1. If you haven't already, install a supported browser, like
   [Chrome](http://www.google.com/chrome),
   [Firefox](https://www.mozilla.org/firefox), or
   [Safari](https://www.apple.com/safari/).  Sorry, Internet Explorer!
   Just kidding. I'm not sorry. That's karma for IE6. ;)
2. Visit [http://openstreetmap.org/](http://openstreetmap.org/) and
   create a free account. Log in.
3. Scroll and zoom to a place on the map you wish to edit.
4. Pull down the "Edit" menu, and select "Edit with iD".

![Start editing]({{ site.url }}/bend/assets/osm-id-editing/startedit.jpg "Start editing")

You're ready to begin improving the map!


Editing Overview
----------------

You can play around in the editor all you want without impacting the
live map. There's undo/redo functionality, and everything stays local to
you until you hit "Save".

Once you hit "Save", your data is merged into the live map data, and a
re-render of the main map tiles will be queued shortly.

> (Technically, it's only the mapnik ("Standard") layer that triggers
> immediately, and that only triggers after you zoom in and get the
> tiles again. Hit reload on the browser in the OSM area you just
> edited, then wait a minute and hit reload again. The new edits should
> show.)

Start with small edits. Don't delete anything that you didn't make
unless you know what you're doing. Have fun!


Adding and Editing Points and Shapes
------------------------------------

There are three main types of things you can edit in iD: points, lines,
and areas. You can select which you wish to draw with the menu at the
top of the map. (Hover over the items for tooltips and keyboard
shortcuts.)

![Points, Lines, and Areas]({{ site.url }}/bend/assets/osm-id-editing/pointlinearea.jpg "Points, Lines, and Areas")

Each of the items in the map database is rendered on the basis of how it
is "tagged". Tags are key/value pairs that describe what the road is.
For instance, a tag might say "this line is highway=residential", and
then a renderer will know to draw it with a certain type of line.
"water=stream" might be drawn with a different type of line.

> Technically, there are only two things in the database: nodes and ways
> (which we call "points" and "lines" in iD). An area is just a line
> that's connected and tagged with an area tag. However, iD
> differentiates lines and areas, so you need to choose the right one
> for what you're drawing.  E.g. lines for roads and streams, areas for
> city boundaries and lakes. (And when I say there are "only two
> things", I actually mean there are more than that, but go ahead and
> pretend I didn't lie there.)


### Adding Points

A point represents a single thing. Like a bathroom ("toilets") or a pub
or a post office. Or a city.

Let's add a new pub. For the demo, I'll just add it to the middle of
nowhere. Remember: you can always undo your changes before you Save.

First, click "Point" to add a new point, then click on the map to add it
to the map. When added, it has a red outline to let you know that it is
the currently-selected object.

This adds a point, but it's not tagged. Let's tag it as a pub. Click on
"Search" on the left, and type "pub". This brings up a list of matches.
With the new point selected (red outline), click on the "Pub" entry on
the left.

![Adding the pub]({{ site.url }}/bend/assets/osm-id-editing/pub1.jpg "Adding the pub")

After clicking on "Pub", a submenu opens in which you can give the pub
attributes.

In general, all attributes are optional. In this case, we really should
give it a name so people who look at the map will be able to see which
pub it is.

![Adding the pub attributes]({{ site.url }}/bend/assets/osm-id-editing/pub2.jpg "Adding the pub attributes")

(Let's say you tagged it "Pub" and you wanted to change your mind. It's
a little counter-intuitive, but you can click on "Pub" again in the
above image, and it will return to the search screen.)

At this point, if you were to hit "Save", the changes would be added
to the database for rendering!

That's all there is to it!


### Editing Points

If you click on a point, a context menu will pop up with additional
actions you can take. For points, this is simply "Delete".

![Editing points]({{ site.url }}/bend/assets/osm-id-editing/pointmenu.jpg "Editing points")

You can move a point simply by dragging it to another place.

You can select multiple points by holding down SHIFT while you select
them.

### Adding Lines

Lines work basically the same way as points, with a few more bells and
whistles.

Select "Line", and draw the line out clicking a point at a time. Here
I've found a dirt road outside of Bend, OR that's missing from OSM data:

![Drawing lines]({{ site.url }}/bend/assets/osm-id-editing/line1.jpg "Drawing lines")

Double-click the last point, or hit ESCAPE to stop drawing. Now you're
at the tagging search menu again.

Now, I know from experience that this dirt road is of type "Track". (See
the "Tagging" section, below, for how to discover more tags.) Searching
for "track", and clicking "Track" will tag this line as a dirt track and
bring up the track sub-attributes menu.

Remember, all the sub-attributes are optional, including the name.


### Editing Lines

Similar to points, lines have a context menu when you click on them. You
can straighten them, move them, delete them, and reverse them.

![Editing lines]({{ site.url }}/bend/assets/osm-id-editing/linemenu.jpg "Editing lines")

Reverse? You'll notice that between the points of the lines, there are
direction arrows showing which way the line is going. Usually this
doesn't matter, but it does in certain cases, e.g. streams, rivers, or
one-way roads.

If you first select the line, *then* click on a point on a line, you'll
get a different context menu that allows you to split the line at that
point:

![Splitting lines]({{ site.url }}/bend/assets/osm-id-editing/linesplit.jpg "Splitting lines")

That same submenu also allows you to uncouple crossing lines.

You can drag points of the line around:

![Moving line points]({{ site.url }}/bend/assets/osm-id-editing/linedragpoint.jpg "Moving line points")

And you can grab and drag one of the direction arrows to bisect a line at that
point:

![Bisecting a line]({{ site.url }}/bend/assets/osm-id-editing/linebisect.jpg "Bisecting a line")

You can select multiple lines by holding down SHIFT while you select
them. This will bring up another context menu that allows you to merge
lines


### Adding and Editing Areas

An area is just a closed line. Select the "Area" tool and click points
where you want the area to be. Double-click the last point or hit ESCAPE
when you're done.

Here is a lake that hadn't been added to the database. I traced the
outline as an area, searched for "lake", tagged it as a lake, and then
selected the area to bring up the context menu:

![Editing an Area]({{ site.url }}/bend/assets/osm-id-editing/area.jpg "Editing an Area")

The context menu has options to rotate the entire area, to square the
corners (useful for buildings), to move it, and to form a perfect circle
(useful for roundabouts).

But wait a moment... there's an island in this lake. How do we cut that
out so it doesn't render as water?

First, add the island as an area. No need to tag it as anything. Then
click the island to select it. Then, *while holding SHIFT*, click on the
lake. Now both of them are selected, and a new context menu will show
up. Hit "+" on that menu to join the areas, and the island is magically
created.

![Creating an Island]({{ site.url }}/bend/assets/osm-id-editing/island.jpg "Creating an Island")

> iD is doing a lot of stuff behind the scenes when you do this. It's
> creating another type of element called a "relation" of
> `type=multipolygon` that stores the relationship between the island
> area and lake area in the database. Relations can also be used to
> relate multiple roads that are all part of a scenic route. Or to
> relate an intersection with "right turn only".  Relations are
> powerful, important, and beyond the scope of this tutorial. You can do
> a lot of editing without ever touching them.


Tagging
-------

### Tag overview

Tags are key=value pairs that are stored in the database for a single
point, line, or area. There could be zero tags, or there could be many.

The iD editor hides the key=value information from you behind its
user-friendly UI, but you can see them if you select an object and then
click "All tags" in the edit sidebar. This will show you the key=value
pairs, and you can see how they correspond to the values entered in the
UI:

![All tags]({{ site.url }}/bend/assets/osm-id-editing/alltags.jpg "All tags")

You can also add and remove tags from the "All tags" interface. This is
particularly useful if you need to enter a tag that's not exposed in the
iD UI. You can see, above, for instance, that `fee=no` is not in the UI.

### A Note on Names

When tagging names, the general rule is to use the full name of the
object, e.g. use "Northwest Milwaukee Avenue", *not* "NW Milwaukee Ave".

### Which tag to use?

How do you know what to search for when tagging? What are the proper
tags for a parking aisle? For a driveway? For a dirt road? For a
seasonal stream? For a library? For a cliff? For a meadow?

In iD, it's always good to search for a particular tag and see what it
comes up with. If you're tagging a dam, search for "dam". That said, you
might not know what you're searching for. What's a dam called where the
water spills over the top across the full width of the river? (A
"weir".)

If in doubt, just tag it with your best guess. You or someone else can
fix it later. 90% of the work is adding the line or area, so you will
have made a valuable contribution doing that even if the tagging is
wrong.

Here is the [complete list of "official" OSM
features](http://wiki.openstreetmap.org/wiki/Map_Features). Note that
these are listed as "key=value" pairs; for example, the first one is
`aerialway=cablecar`. The third column in the table tells you which
kinds of entities can take this tag: points, lines, and/or areas.

From the Features page, there will often be links to pages for specific
types of tagging, e.g. [mountain
biking](http://wiki.openstreetmap.org/wiki/Mountain_biking). If someone
wants to render a mountain-biking-specific map, the detailed mountain
biking tags will enable them to label trail difficulty, trail width,
etc.

### What if a road is paved then turns to dirt partway through?

Each object in the database has its own set of tags. A single line
cannot be both `surface=paved` and `surface=unpaved` at the same time.
You must split the line into two, per the Editing Lines section, above,
and tag the ends separately.


Image Layers
------------

You can change the background of the map by clicking the "Background
settings" button on the right.

![Background settings]({{ site.url }}/bend/assets/osm-id-editing/backgroundsettings.jpg "Background settings")

If a detail is missing on one of the aerial maps, try another to see if
it is there.

There are also topo maps, the mapnik standard OSM render, and "custom"
if you have your own map tile server.

Under the maps, there are some overlays that you can put on top of the
base map.

One of these is the "GPS traces" layer. This is maintained by MapBox and
is rather old at this point. If you're looking to trace a GPS path, you
might want to use the "Local GPX file" layer.

Finally, one of the useful overlay layers is "New & Misaligned TIGER
Roads". If you have an unnamed road in OSM, or you're tracing a road for
which you don't know the name, see if you can find it on this layer.
More information in the TIGER section, below.


TIGER--US Census Maps
---------------------

The US Census maintains its own set of maps, called the TIGER maps. For
their purposes, geographic accuracy wasn't particularly valuable, so the
maps tended to be fairly *wrong*.

They've since made a large push to make the maps more accurate. However,
there was a massive import of the old TIGER data into OSM by Dave Hanson
many years ago, and so that data needed to be manually aligned to aerial
photos or GPS data. For the entire US. By hand. For urban areas, this is
largely complete as of 2014.


### Fixing TIGER data

In this fine example, we have the Bing aerial imagery layer, as well as
the new TIGER Roads layer activated. The TIGER data overlay is yellow
lines, as well as large, bold street names that appear on the base map
near the roads. It looks like there's a discrepancy between the new
TIGER data and what's in OSM.

![Missing Road]({{ site.url }}/bend/assets/osm-id-editing/tiger1.jpg "Missing Road")

In OSM, Whaley Drive heads southwest from Sonoma Street, but TIGER has
it in a different place.

Furthermore, there's no road where the OSM data is on the aerial photo.

Does OSM have it wrong? Is the aerial photo old? Is the TIGER data
wrong? How can you tell without being there?

First, select Whaley Drive and look at "All tags". There are a ton of
tags in there that clearly mark it as part of the original TIGER OSM
import.

![All tags of a TIGER object]({{ site.url }}/bend/assets/osm-id-editing/tigeralltags.jpg "All tags of a TIGER object")

(In these modern times, imports generally do not attach all this
metadata to the objects, but this was from a while ago.)

So we know the road was part of the automated TIGER import.

But has it been modified since then? Maybe someone with local knowledge
we don't have actually modified the line. For us to undo that work would
be an error. How can we tell?

At the very bottom of the object tags page, there's link that will take
us to OSM to check out the details by clicking on "View on
openstreetmap.org":

![Getting to the object on OSM]({{ site.url }}/bend/assets/osm-id-editing/objviewosm.jpg "Getting to the object on OSM")

When you click on that, you'll get an OSM tab that shows more info
about the line ("way"). We're looking for if it has been edited, by
whom, and when:

![Way details on OSM]({{ site.url }}/bend/assets/osm-id-editing/osmway.jpg "Way details on OSM")

It looks like this is version 2, edited 4 years ago by `balrog-kun`. If
it hadn't been touched yet, the only editor would have been
`DaveHansenTiger`. So who was `balrog-kun`, and what did they do?

If you look at the bottom of that column, you'll see a "View History"
link. There we can go see what has happened with this element, and that
might help clarify the story. (Going there reveals the initial import by
`DaveHansenTiger`, followed the subsequent edit by `balrog-kun`.)

But there's also a changeset number there at the top, 4247780. If you
click on that, it gives more details about the changeset by
`balrog-kun`.

![Changeset details on OSM]({{ site.url }}/bend/assets/osm-id-editing/changesetdetail.jpg "Changeset details on OSM")

The `bot=yes` tag is a dead giveaway that a human hasn't been here.
Looks like the bot went through the database and expanded all the
abbreviations from the TIGER import.

At this point, I'm confident that no human has reviewed this line, and
it's very likely in the wrong place.

So I'll select the node that joins Whaley to Sonoma, and choose
"Disconnect" from the context menu. Now I can drop the endpoints of the
road into the proper place between Sonoma and Viola streets. Then I
click "Save", enter a changeset description, and *BAM!* I've improved
the map!

### Other TIGER problems

There are some other common issues you might run into.

* Roads not aligned well with reality.
* Old roads on the map that no longer exist.
* New roads that exist but are not on the map.
* Roads that are tagged `highway=residential` when they're not.

"Residential" was the import default if there wasn't enough information
in the TIGER source to determine otherwise. One notable upshot of this
is that virtually all dirt roads in the forest are `highway=residential`
when they should either be `highway=track` or
`highway=unclassified`/`surface=unpaved`.

### Using TIGER to name streets

A fairly common case is that there will be some new construction that
you see on aerial photos but has not been added to OSM.

You can trace the roads, but what are their names?

Fortunately, as we've seen, you can just bring up the TIGER map overlay,
and often find the names there. Don't forget to use the full street
name--no abbreviations!


Uploading GPS Traces
--------------------

If you record a GPX file on your GPS that represents a trail or new
road (or anything else that can't easily be determined by the aerial
photos), feel free to add that to the database of GPS traces.

These traces are used especially in the JOSM editor which will show the
user all GPS traces uploaded to a region for all time. In iD, you'll
either have to wait until the OSM traces layer is updated (timeframe
unknown), or you can take your individual GPX and show it on the map as
described above.

### How to upload a trace

Click "GPS Traces" at the top of the main OSM web page, then click
"Upload a trace".

The description and tags fields are for human reference and are
freeform.

I suggest "Trackable" for the "Visibility".

Once you upload the trace, you'll get an email when it is imported.


Additional Links
----------------

### Bug Tracker (Notes)

If you're viewing (not editing) the map the website, you can click the
"layers" icon on the right side of the screen. On that popup, you can
check "Map Notes".

This is the "bug tracker" for OSM. You can comment on or resolve notes
that are on the map. Only resolve them if you are sure you have actually
resolved it. Often local knowledge is required.

To add a new note, the "add note" icon is four icons down from the
"layers" icon on the map view right sidebar.

### Map Roulette

[Map Roulette](http://maproulette.org/) will give you random things to
fix on the map. Some of them you'll be able to fix, some of them you
won't be sure of and you'll skip. If you want to pour random energy into
the map, this is a good site to do it on.


### Strava Slide

The elves as Strava Labs have developed a pretty fantastic tool to
automatically bend lines around uploaded GPS data. And since Strava is a
running/biking exercise tracking site, they have *a lot* of GPS data.

It's their [Slide](http://labs.strava.com/slide/) tool, and it's built
as a hacked-up version of the iD editor.

To use, you just select a line, and then choose "Slide geometry to
Strava heatmap" from the context menu that pops up.

*NOTE*: often the aerial photos are better for drawing trails than the
GPS data. But if you can't see the trail from the air (because of the
forest, say), then the Slide tool is about the best result you can get.

If there's just one section of a trail that needs Sliding, you can split
it into its own line, then apply the Slide tool, then merge it back
together with the lines it used to be attached to.

### JOSM

[JOSM](https://josm.openstreetmap.de/) is an offline editor, meaning
you'll download a chosen, rectangular chunk of data, edit it, and then
upload it to the server later. This differs from iD, which just allows
you to edit whereever you are, but requires you be online.

JOSM is a much, much more featureful and powerful editor than iD, with a
correspondingly steeper learning curve, and is generally used by serious
mappers. That said, I still use iD for quick fixes.

Have fun!
