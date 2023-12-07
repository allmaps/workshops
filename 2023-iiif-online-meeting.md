# Georeferencing the Internet Archive with Allmaps
Thursday, December 07, 2023, 5:00 PM - 5:30 PM CET

Jules Schoonman & Bert Spaan

[2023 Online Meeting, IIIF Consortium](https://iiif.io/event/2023/online-meeting/)

## Abstract
Following the exciting news about the collaboration between the IA and IIIF Consortium, this workshop explores the possibilities of annotating IA material using the Allmaps platform. We will locate relevant collections and resources in the IA, and open them in the Allmaps Editor using the available IIIF Manifest URIs. We'll look at the format of a Georeference Annotation and demonstrate its usages in the Allmaps Viewer and other tools. When working with open data that is not yet available elsewhere with IIIF, the IA can thus serve as a repository to launch geospatial research projects. This workshop will give you everything you need to get started–and the approach can be replicated for other IIIF content as well. When we run into problems, we'll create issues in the relevant repositories to help the development of both Allmaps and IA's IIIF implementation.

## Step 1: Finding Maps in the Internet Archive

As of September 2023 the IIIF API of the [Internet Archive](https://archive.org/) was upgraded in collaboration with the IIIF Consortium. The implementation is still under development and some items might throw an error when opening them in Allmaps. Please notify us when this happens and we'll make sure to investigate and publish a fix when possible.

Some collections of interest:

- [Center for Sacramento History](https://archive.org/details/cshmaps)
- [United States Geological Survey](https://archive.org/details/maps_usgs)
- [Getty Research Institute](https://archive.org/details/getty)
- [Smithsonian Libraries and Archives](https://archive.org/details/smithsonian)
- [Digital Piranesi](https://archive.org/details/digital-piranesi-v17)
- [David Rumsey Map Collection](https://archive.org/details/david-rumsey-map-collection) (Please note that the images on the [David Rumsey website](https://www.davidrumsey.com/) have a higher resolution than those in the Internet Archive and also support IIIF.)

How to find the IIIF Manifest of an item in the Internet Archive?

- Locate the id in the URL: `https://archive.org/details/{id}/`
  - In the URL `https://archive.org/details/map2002023007/` the id is `map2002023007`
- Add the id to the following pattern: `https://iiif.archive.org/iiif/{id}/manifest.json`
  - E.g. `https://iiif.archive.org/iiif/map2002023007/manifest.json`

💡You can use [this bookmarklet](https://iiif-bookmarklets.netlify.app/collections/internet-archive/) to quickly open the IIIF Manifest of an item in the Internet Archive and [this bookmarklet](https://iiif-bookmarklets.netlify.app/tools/allmaps/) to open the current browser address in the Allmaps Editor.

❗Allmaps does not currently support IIIF Collection Manifests

## Step 2: Georeferencing Maps in the Allmaps Editor

- Copy the URL of the IIIF manifest
- Open the [Allmaps Editor](https://editor.allmaps.org)
- Paste the link in the field and click `Load`. At the top you now see four tabs (you can always go back and forth). If you get an error message, double check if you copied the right link.
- Select an image under the `Collection` tab (often there's only a single image to select). The two icons indicate whether a map already contains a mask and/or control points.
- Click the `Mask` tab and draw a mask by zooming in and clicking the image. The mask will be used to crop the map in the viewer. If you want to start again, click the middle button of the menu on the bottom right. This opens up a panel listing all masks; click the bin to remove one (there's no way to undo this currently). You can move points around or add new points to the mask by dragging points or lines. You can also remove a point by clicking it while holding shift.

❗If you accidentally create a second mask, you can quickly change tabs (to `Collection` and back) to remove it again.
  
- Now go to the `Georeference` tab. On the left you see the selected image, on the right a world map. Zoom to the region of the map on the right. Click a point you recognise on both maps (which has remained the same over time), such as a church tower or a road crossing. Add the point on both sides (a number will indicate that they are paired). Add at least **three** of these points (they are called *control points*) and try to spread them as much as possible. If you unfold the layers panel (middle button of the menu) you obtain an overview of your mask and the control points. You can remove points if needed (there's no undo function yet). You can also select another mask and add points for that selection.

❗Removing points from the menu might confuse the numbering. Reload the page to reset the numbering. Note that the order of numbers could change after reloading the page.

💡You can rotate the view by holding Option/Alt-Shift.

💡You can load a custom reference map by following the instructions in [this Observable Notebook](https://observablehq.com/d/f97e823615ea778c).

## Step 3: What is a Georeference Annotation?

- After finishing Step 2, Open the `</>` panel on the bottom right.
- Next to `Show annotation for:` you can choose between `Manifest`, `Image`, `Map`.
  - `Map` refers to the current selected mask (and related control points)
  - `Image` refers to all the masks (and related control points) of the currently selected image
  - `Manifest` refers to all the masks (and related control points) of all the images in the current IIIF Manifest (see the overview in the `Collection` tab).
- Select `Map` and click `Open in new tab`. You now see a json document that (almost 😅) conforms to the specifications of the [Georeference Extension](https://iiif.io/api/extension/georef/). We'll explain the different parts to make you familiar with the structure.
 
❗The Allmaps Editor currently stores the annotations for you. If someone else opens the same map, they can alter the annotation. It is therefore wise to save a copy of your data on your hard drive or elsewhere. The Editor does not yet support loading custom annotations, but the Allmaps Viewer does.

## Step 4: Opening a Georeference Annotation in the Allmaps Viewer

- Go back to the Editor and click `Copy` in the `</>` panel.
- Navigate (in a new tab) to the [Allmaps Viewer](https://viewer.allmaps.org/), paste the Georeference Annotation in the second field and click `View`. The georeferenced map will now open in the Allmaps Viewer. You can go back and forth between the original image and warped map by clicking the buttons in the top right corner. If the IIIF manifest contains multiple images and if more than one were georeferenced (and exported), all images are rendered at once. Some tricks:
  - Hold space to quickly hide the map
  - Press `B` or use the right wheel to remove the background color
  - Press `M` to show the outline of the mask
  - Press `T` to change the transformation algorithm
  - In case of multiple maps use `[` and `]` to browse the collection (the selected map will be on top)
  - Right click a map to change the layer order

💡 The copy/paste method serves to demonstrate how Allmaps works on the basis of Georeference Annotations. An easier way is to navigate to the `Results` tab and open one of the links.

- If you like to improve your work, you can go back to the editor to do so (browser back, or navigate to the tab). You can leave the Viewer tab open and reload the page to see the results.

## Step 5 (extra): Annotating maps with geojson.io

- In order to add the map as a layer in geojson.io (and also in GIS-applications), you need to use the Allmaps Tile Server. The Tile Server acts as a proxy server to translate IIIF images to [XYZ map tiles](https://en.wikipedia.org/wiki/Tiled_web_map), using the georeferencing annotation.
- There're three ways to generate the URL template for XYZ map tiles:
  - Copy the XYZ link at the bottom of the `Results` tab of the Allmaps Editor.
  - Follow the [Tile Server instructions](https://observablehq.com/@bertspaan/allmaps-tile-server) and click the `Copy URL template to clipboard` button
  - Copy the URL to the georeferencing annotation (see previous section) and place it after `=` in the following URL: `https://allmaps.xyz/{z}/{x}/{y}.png?url=`
- Go to the [geojson](http://geojson.io) editor
- Click `Meta` and `Add raster tile layer` in the top menu. Paste the URL template and give the layer a name. Navigate the map to see the result (it won't do this automatically). At the bottom right, a checkbox appears to hide/show the layer
- You can repeat these steps to add another layer
- In the geojson.io editor you can add markers, rectangles, polygons and polylines (see the tool palette). You can also edit and delete features by using the buttons at the bottom of the tool palette (follow the on-screen instructions).
- When you click a feature, you can edit its metadata in a popup panel. Each row in the table represents a label-value pair: labels left and values right. You can add a new pair by adding a new row.

❗You can also load XYZ maps in [Placemark](https://app.placemark.io/play). This app supports the TileJSON format which can be requested by using the following pattern: `https://allmaps.xyz/tiles.json?url=`.
