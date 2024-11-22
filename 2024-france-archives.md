# Allmaps Georeferencing Workshop at FranceArchives
Thursday, November 28, 2024

Manuel Claeys Bouuaert

[Conférence "Des outils IIIF pour valoriser et explorer les collections en ligne"](https://francearchives.gouv.fr/fr/actualite/693821456)

## Content
After a short overview presentation of Allmaps on November 27th, this workshop will explore the possibilities of  the Allmaps platform in a hands-on way. We will learn to locate map collections and their IIIF Manifest URIs of various partner archives of FranceArchives, and open them in the Allmaps Editor. We'll look at the format of a Georeference Annotation and demonstrate its usages in the Allmaps Viewer and other tools. This workshop will give you everything you need to get started. We'll share interesting maps we discover, and log issues encountered to improve the IIIF setup at the partner local archives and help the development of Allmaps.

## Step 1: Finding Maps in a Partner Archive
As FranceArchives [lists](https://francearchives.gouv.fr/fr/article/714850036) on its website, as of November 2024 about 20 national, departemental and municipal french archives have online portals that support IIIF. And many of those collections also include maps!

Earlier tests by FranceArchives staff to use the Allmaps tools with maps from these archive portals have indicated that the software implementation at some of these archives contains small imperfections, which prevents us to use them today.

> [!NOTE]  
> If you work at one of these archives, please refer to the FranceArchives staff for more information on the steps needed (by your archive or the software provider of your archive's platform) to make you archive's maps accessible in Allmaps.

### Find a Map
About 10 archives had no issues, and we'll be using these today. These archives are:

|Archive | Search portal | Search FranceArchives | Example map  |
|---|---|---|---|
|Departmental archives of Ille-et-Vilaine | [Search](https://images-archives.ille-et-vilaine.fr/) |	[Search via FranceArchives](https://francearchives.gouv.fr/fr/inventaires/FRAD035?es_digitized=True) | [Guingamp](https://images-archives.ille-et-vilaine.fr/idurl/1/103954) |
|Municipal archives of Bazas	| https://archives-numeriques.ville-bazas.fr/idurl/1/9038 |
|Municipal archives of Montbrison	| www.archives.ville-montbrison.fr/idviewer/3607/1 |
|Municipal archives of Aurillac	| bibliotheque-numerique.aurillac.fr/idviewer/10941/1 |
|Municipal archives of Saint-Omer	| bibliotheque-numerique.bibliotheque-agglo-stomer.fr/idviewer/22157/1 |
|Municipal archives of Carmaux	| archives-numeriques.carmaux.fr/idviewer/252/1 |
|Municipal archives of Dieppe	| https://patrimoine.dieppe.fr/idurl/1/14995 |
|Municipal archives of Abbeville	| https://patrimoine.abbeville.fr/collection/item/771-cartes-et-plans-1914-1918-general-plans-of-n-5-convalescent-camp-depot-cayeux-france?offset=6 |
|Digital heritage library of Alençon	| https://bibliotheque-numerique-patrimoniale.cu-alencon.fr/records/item/1924-indo-chine |
| Bibliothèque nationale de France | https://gallica.bnf.fr/ark:/12148/btv1b53029493h.r=carte%20bretagne?rk=64378;0

Now it's up to you: browse these archives and find a map you like!

### Find the Map's IIIF Manifest URL

Once we find a map, we need to find the **URL of it's IIIF Manifest** (or IIIF Image). This URL is how we will point Allmaps to the map in question.

To locate the IIIF Manifest URL, there are a couple of options. Use the one that works best for you.
- Some archive platforms make it easy by providing the **URL on the platform webpage** of the map ([example](https://images-archives.ille-et-vilaine.fr/archives/item/103954-4j-guingamp-7)), or **in the interactive viewer**. Look for the IIIF logo <img src="https://upload.wikimedia.org/wikipedia/commons/e/e8/International_Image_Interoperability_Framework_logo.png" width="20">, sometimes within the 'share' menu.
- The **FranceArchives** platform provides two viewers for each item. By selecting the **'Universal Viewer'** ('UV' logo at the bottom) we can find the IIIF Manifest URL under the 'share' button in the bottom left of the viewer, by clicking on the grey IIIF icon: this opens the IIIF Manifest in a new tab, and we can copy the URL of this tab.
- To automatically detect IIIF resources on any platform website or viewer you visit, you can use the very helpful '**detektIIIF**' browser extension. When visiting a webpage or viewer containing a IIIF Manifest, this extensions will automatically find the IIIF Manifest URL. It's available one the [Chrome webstore](https://chromewebstore.google.com/detail/detektiiif3/aaodcobgcadinjipaocibamdfcffpcpp) and as a [Firefox Add-on](https://addons.mozilla.org/en-GB/firefox/addon/detektiiif2/). If you want to use it, install the extension and pin it in your browser for easy access. 
- For some archive platforms (namely those that use Arkhênum - Limb Gallery software), we can **deduce the IIIF Manifest URL** from the platform webpage or viewer webpage by locating it's id. Here are two examples:
  - For the map at this viewer URL `https://archives-numeriques.ville-bazas.fr/viewer/9038/?offset=#page=1&viewer=picture&o=&n=0&q=` we can find the id `9038` in the URL and construct the IIIF Manifest URL `https://archives-numeriques.ville-bazas.fr/iiif/9038/manifest`
  - For the map at this webpage URL `https://images-archives.ille-et-vilaine.fr/idurl/1/103954` we can find the id `103954` in the URL and construct the IIIF Manifest URL `https://images-archives.ille-et-vilaine.fr/iiif/103954/manifest`

<!-- > [!TIP] Bookmarklet 
> 
> Deducing the IIIF Manifest url can be done automatically via this bookmarklet. -->

<!-- 💡You can use [this bookmarklet](https://iiif-bookmarklets.netlify.app/collections/internet-archive/) to quickly open the IIIF Manifest of an item in the Internet Archive and [this bookmarklet](https://iiif-bookmarklets.netlify.app/tools/allmaps/#allmaps-editor) to open the current browser address in the Allmaps Editor. Use those two in sequence. Alternatively, you can use [this form](https://dev.docs.allmaps.org/guides/finding-maps/) on the Allmaps documentation site (which is still in development). -->

> [!IMPORTANT] No Collection Manifests
> 
> Allmaps does not currently support IIIF Collections.

> [!NOTE] The difficulty of IIIF Manifests URL
> 
> You might notice that finding a IIIF Manifest URL can be a tricky step, and might be a hurdle for people new to IIIF. Indeed, improvement is still needed in platforms and viewer to make sure a IIIF Manifest can always easily be found.

## Step 2: Georeferencing a Map in the Allmaps Editor
Now that we have found a map in a partner archive, and identified the IIIF Manifest URL that points to it, we can open Allmaps Editor to georeference the map, creating a Georeference Annotation.

### Open the Manifest in Allmaps Editor
- Copy the URL of the IIIF Manifest
- Open the [Allmaps Editor](https://editor.allmaps.org)
- Paste the link in the field and click `Load`. At the top you now see four tabs (you can always go back and forth). 
- ❗ If you get an error message, double check if you copied the right link.

### Select the right Map
- Select an image under the `Collection` tab (often there's only a single image to select). 
- 🔴 There could be one or two icons at the bottom right of a map, indicating that for map a mask and/or control points are already known by Allmaps.
- ℹ️ Notice the menu on the bottom right of the window. The first of the three icons is an `i`. If you click it, you will see the metadata contained in the Manifest of the map we are georeferencing.

### Draw the Mask
- Click the `Mask` tab and draw a mask by zooming in and clicking the image. 
- The mask specifies where the map is on the image. It will later be used to crop the map in the Viewer
- Draw a mask around the part of the image where the map is located.
- ✍️ You can move points around or add new points to the mask by dragging points or lines. You can also remove a point by clicking it while holding shift.
- ↩️ If you want to start again, click the middle button of the menu on the bottom right of the window, showing a list. This opens up a panel listing all masks; click the bin to remove the mask (there's no way to undo this currently). If you accidentally create a second mask, you can quickly change tabs (to `Collection` and back) to remove it again.

### Georeference the Map
- Now go to the `Georeference` tab. On the left you see the selected image, on the right a world map. Zoom to the relevant region on the world map. Click a point you recognise on both maps (which has remained the same over time), such as a church tower or a road crossing. Add the point on both sides (a number will indicate that they are paired). Add at least *three* of these points (they are called *control points*). Ideally, they are spread out over the map as possible. 
- 📋 Click the middle button of the menu on the bottom right of the screen to obtain an overview of your masks and their control points. You can remove points if needed (there's no undo function yet). You can also select another mask and add points for that selection.
- 🙅 Removing points from the menu might confuse the numbering. Reload the page to reset the numbering. Note that the order of numbers change after reloading the page.
- ↗️ You can rotate the view by holding Option/Alt-Shift.
- 🗺️ It will soon be possible to load a custom world map to help you place the control points. Advanced: If you want to try this out now, you can do this via a bookmarklet:
  - Drag the following link to you Bookmarks bar: <a href="[1]:javascript:(function()%7BsetUserBaseMapUrl('https://tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png')%7D)()
">Allmaps Editor: OpenStreetMap background</a>
  - While in the Allmaps Editor, click this bookmark. You will see the background change to OpenStreetMap

## Step 3: Inspecting the Georeference Annotation
- Click the `</>` button on the bottom right of the screen to inspect the Georeference Annotation you just created finishing step 2. It is shown in the black pane. You can also open the annotation in a new browser tab using `Open in new tab`.
- This piece of text is a Georeference Annotation. That means it conforms to the specifications of the [Georeference Extension](https://iiif.io/api/extension/georef/), an open format used to annotate ('describe') another (online) resource. In this case, we describe that we now how that resource can be georeferenced. Since we are linking to the original resource, it's metadata are also available.
- This little document contains three important parts. Can you find them?
  1) A reference to the IIIF Resource it's annotating (under `source`).
  2) The mask which describes where the map is on that resource (under `selector`).
  3) The control points (under `features`).
- Some IIIF Manifests or Images can contain multiple maps. We can make Annotation Pages, which are lists of Annotations each describing the georeferencing of a map. You can see this in action next to `Show annotation for`: you can choose between `Manifest`, `Image`, `Map`. The annotation in the black panel will adapt to your contain the annotations of your choice.
  - `Map` refers to the current selected mask (and related control points)
  - `Image` refers to all the masks (and related control points) of the currently selected IIIF Image (or Canvas)
  - `Manifest` refers to all the masks (and related control points) of all the images in the current IIIF Manifest (see the overview in the `Collection` tab).
- 💾 Notice the `Copy` and `Download` buttons. If you want to save this Annotation in your own annotation or archival system, you could use these.

> [!IMPORTANT] Storing Georeference Annotations
> 
> The Allmaps Editor currently stores a copy of every annotation that is created. If you or someone else opens the same IIIF Manifest URL in the Allmaps Editor on a later moment, the masks and control points you entered will show up. Anyone can thus this alter and improve your annotation. It is therefore wise to save a copy of your data somewhere if you want to keep this specific version. In the future, it will be possible to pin or request specific versions of an annotation.


## Step 4: Opening a Georeference Annotation in the Allmaps Viewer
The Georeference Annotation can be used in any tool that can interpret this type of data. Allmaps Viewer is one of them. It warps the maps and displays it in the right location over a basemap.

- Copy the Georeference Annotation: Go back to the Editor and click `Copy` in the `</>` panel.
- In a new tab, navigate to the [Allmaps Viewer](https://viewer.allmaps.org/)
- Paste the Georeference Annotation in the second field and click `View`. The georeferenced map will now open in the Allmaps Viewer. You can go back and forth between the warped map and the original image by clicking the `Map` and `Image` buttons in the top right corner.
- 🎨 The Viewer has some cool tricks:
  - Hold `spacebar` to quickly hide the map
  - Press `B` or use the right knob to remove the background color
  - Press `M` to display the outline of the mask(s)
  - Press `T` to change the transformation algorithm.
- 🗺️ 🗾 If the IIIF Manifest contained multiple maps and if you copied the Georeference Annotation using `Manifest` or `Image`, all maps are rendered at once. Extra tricks when multiple maps are loaded:
  - Use `[` and `]` to browse the collection (the selected map will be on top)
  - Right click on a map to change the layer order

> [!TIP] Directly from Editor to Viewer
> 
> We suggested to copy/paste the annotation to demonstrate how Allmaps works on the basis of Georeference Annotations. It is important to be aware of these files that contain information, can be stored in an archival system and opened again. 
> 
> An quicker way to view a map from the Editor is to navigate to the `Results` tab and open one of the links, such as `View current image`. In this case, the Georeference Annotation you created is loaded from Allmaps' database directly. This means that new edits in the Editor will become visible in the Viewer after refreshing the page. You can leave both tabs open to improve your work.

> [!NOTE] Advanced: looking up manifests
> 
> In case you found a IIIF Manifest containing a map and want to find out if a Georeference Annotation exists in the Allmaps database, we already saw it's possible to simply open the IIIF Manifest URL in the Editor and see if any mask or control points are loaded. 
> 
> A second option is to directly enter the IIIF Manifest URL in the Viewer and see if a map is displayed. 
> 
> A third way to check this is more programatic and uses the Allmaps API:
> 
> - Copy the IIIF manifest link
> - Open this URL: [https://annotations.allmaps.org/?url=](https://annotations.allmaps.org/?url=)
> - Paste the IIIF manifest link after `?url=` in the browser address bar and press enter

## Extra: Step 5: Tracing features on maps
Once you georeferenced a map, you can also use it in other tools like webmaps (using the Allmaps webmap plugins) or GIS-applications like QGIS. Here, we will use it in an online GIS application an trace features on the map.

We will use Placemark Play, a free and open source online GIS tool.

- Open [Placemark Play](https://play.placemark.io/) and navigate to the location of your map.
- Add your map as a new background layer: click the layer icon in the top right (the icon under `Help`) and click the `+` button to add a new layer. Choose `+ Custom` and `XYZ`. Give your layer a name, and for the template URL go back to the Editor and copy-paste the 'XYZ' link of the Allmaps Tile Server at the bottom of the `Results` tab. Find out more about the Allmaps Tile Server below.
- It may take a couple of seconds for the map to load. If you still don't see anything, verify you are in the right location (Placemark doesn't automatically navigate to the area of the map you loaded).
- In Placemark you can now add points, lines, polygons, rectangles and circles via the buttons on the top left. You can also edit and delete features by selecting them and pressing `backspace` or clicking the bin icon in the top.
- When you click a feature, you can edit it's shape by dragging the (mid-)points. You can also edit its metadata in the panel on the right. Each row in the table represents a label-value pair: labels left and values right. You can add a new pair by adding a new row.
- Now it's up to you: trace interesting features like rivers or buildings, and describe them using their metadata.
- Don't forget to export the data you created at the end! Use `File` > `Export`. Choose a format you are familiar with (or GeoJSON by default).

You could now use this data to compare these features with similar features from other databases (like current rivers or buildings from OpenStreetMap).

> [!NOTE] About the Allmaps Tile Server
> 
> In order to add the map as a layer in Placemark Play (and also in GIS-applications like QGIS or ESRI ArcMap), you need to use the Allmaps Tile Server. The Tile Server creates [XYZ map tiles](https://en.wikipedia.org/wiki/Tiled_web_map): a very broadly supported format in GIS applications to load maps. It acts as a 'proxy server' and created the requested XYZ tiles on the fly, using the Georeferencing Annotation. This way, you can load maps that don't directly support Georeference Annotations, by loading XYZ-tiles made from your Georeference Annotation!

<!-- Placemark Play supports the TileJSON format which can be requested by using the following pattern: `https://allmaps.xyz/tiles.json?url=`. -->

## Closing off

We hope it's clear to you now how the different Allmaps tools can be used to georeference, view and use IIIF maps. If you have any questions, would like to integrate these tools in your archive's software platform or would like to use these tools in research or valorisation, don't hesitate to reach out to Allmaps!

You can [send us an email](mailto:hello@allmaps.org) or reach us in the `#allmaps` channel of the [IIIF Slack](http://bit.ly/iiif-slack).