---
title: Get ready to use IIIF and Allmaps
description: Open Science Week 2026 workshop
---

Workshop [Get ready to use IIIF and Allmaps](https://www.tudelft.nl/en/events/2026/open-science/get-ready-to-use-iiif-and-allmaps), Sep 14 2026, TU Delft Library.

_NB: This guide will be published as part of the [Allmaps documentation](https://allmaps.org/docs/introduction)._

This guide describes the process of georeferencing a IIIF resource in [Allmaps Editor](https://editor.allmaps.org). It presumes you already have a URL to a IIIF Resource that can be opened in Allmaps. At the bottom of this page, you'll find a list of repositories supporting IIIF.

### What is georeferencing?

Georeferencing an image means relating specific pixels of the image `[x, y]` to corresponding geographic coordinates `[longitude, latitude]`. A pair of corresponding points is called a Ground Control Point or GCP. With at least 2 or 3 GCPs, correspondences can be computed between any other pixel in the image and the world map. If all pixels are transformed, it is possible to render the original image on top of a world map. Depending on the algorithm used, the image is warped in a different way to suite the given set of GCPs as well as possible.

Georeferencing is not a new thing. Classical GIS tools like QGIS and ArcGIS have allowed this for a long time. Traditionally, this means saving a warped copy of the original image as a GeoTIFF, or generating an accompanying ‘world’ file. In both cases, the original raster image and its copies needed to be stored on the user’s device. This creates a lot of extra data and does not allow for easy updates to the georeferencing data.

Allmaps takes a different approach: it works with IIIF resources which are hosted primarily on institutional servers rather than personal devices. The only thing Allmaps requires is a so-called Georeference Annotation, a light-weight standardized document that includes all the information needed to georeference a resource. Allmaps automatically keeps a copy for all maps georeferenced in Allmaps Editor, thereby creating a collective open dataset of georeferenced maps around the world. No derivatives are stored: the original image is warped in the browser. This is very fast and can immediately reflect changes to the source data.

### Step 1: Opening a IIIF resource

- Open [Allmaps Editor](https://editor.allmaps.org)
- Paste the URL to a IIIF resource in the input field and press enter. You can also pick a map from one of the partner institutions listed further down the page.

> **Supported resources**
>
> Allmaps Editor currently supports the following IIIF resources:
>
> - [IIIF Manifest](https://iiif.io/api/presentation/3.0/#52-manifest) (version 2 or 3). A IIIF resource containing canvases with painting annotations.
> - [IIIF Collection](https://iiif.io/api/presentation/3.0/#51-collection) (version 2 or 3). This is a special type of manifest containing references to other IIIF Collections or Manifests.
> - [IIIF Image](https://iiif.io/api/image/3.0/) (version 1, 2 or 3). When loading a IIIF Image URL directly you might need to append `/info.json` to the URL. Please note that no metadata will be available when loading images.
> - Georeference Annotation URLs served by Allmaps. These start with `https://annotations.allmaps.org`.

- At the top you now see four tabs: **Images**, **Draw mask**, **Georeference** and **Results**. You can always go back and forth between them. If instead you receive an error message, double check if you copied the correct link.

> **Dealing with error messages**
>
> Sometimes opening a valid IIIF Manifest URL might still throw an error. This could be caused by various issues, such as:
>
> - The IIIF Manifest is not (yet) supported by Allmaps. For example, a Manifest containing a `choice` property will not be loaded.
> - The IIIF Manifest is invalid. In this case, the parser will indicate which properties fail to follow the IIIF specifications.
> - The IIIF Manifest cannot be loaded due to [CORS](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing) restrictions (i.e. the server hosting the Manifest has not allowed other domains, in this case Allmaps Editor, to load the resource). Some manifests that fail to load in Allmaps might still load in other IIIF Viewers.
>
> If you think Allmaps should support the Manifest, please [file an issue here](https://github.com/allmaps/allmaps), or contact us by email or through the [IIIF Slack](https://iiif.io/community/). If you think the loaded Manifest is incorrect, contact the content provider and aks them to improve their services. If the error message is unclear, contact us for a more detailed explanation.

- Select an image under the Images tab (often there's only a single image to select).
- There could be one or two icons beneath the map, indicating whether a map has already been georeferenced. A green map icon indicates that one or more maps have been georeferenced for that image. If the georeferencing process was not completed, this is indicated by a yellow warning symbol; this means you can improve and complete the work!
- Notice the address bar at the top of the window. It shows the type of resource loaded, its title and URL. Click on it to view the metadata contained in the IIIF Manifest (this is loaded directly from the institution and can vary between different content providers). If you have opened an IIIF Image, no metadata will be available.

### Step 2: Drawing the mask

- Click the **Draw mask** tab. The mask specifies the cartographic part of the image. It will later be used to crop the map in the results tab and Allmaps Viewer. Draw a mask around the part of the image where the map is located. Start by zooming in and clicking on the image. Don’t worry if you made a mistake: you can correct the mask later.

> **Which mask?**
>
> Some maps have clear frames, others not so much. Try to include as much cartographic information as possible within the boundaries of the mask, including labels, but remove non-cartographic elements such as ornamentation, rims or legends. In the end, there is no "correct" mask and where you draw it depends on your interests and how you want to use the map. Fortunately, you can always go back and change the mask in Allmaps, or even create multiple masks for the same image, in case it contains additional inset maps, for example.

- Finish the mask by clicking the Finish button or its start point. You can also remove the mask by clicking Cancel or pressing `esc`.
- After finishing the mask, you can move points around or add new points to the mask by clicking and dragging points or lines. You can also remove a point by right clicking it.
- If you want to remove a mask and start over, click the **Maps** button on the bottom right of the window. This opens up a panel listing all masks; click the bin to remove the mask.

> **Your data in Allmaps**
>
> Edits in Allmaps Editor are automatically stored in the Allmaps database. They are licensed [CC0](https://creativecommons.org/public-domain/cc0/) and published daily as an open dataset on the Allmaps homepage.
>
> Other users opening the same map in Allmaps Editor will see the same edits, and will be able to alter and (hopefully!) improve them. Although Allmaps already stores individual edits in the database, you cannot yet easily pin a version or restore a previous version (undo). These functionalities will be added in future versions of Allmaps Editor.
>
> It is therefore wise to save a copy of your data yourself if you want to keep this specific version.

- It’s possible to draw multiple masks since an image can depict multiple maps, such as inset map). The active mask can be selected from the **Maps** menu by clicking the shape. After selecting, it will be highlighted with a thicker border, also in the next step.

> **Existing work**
>
> If you already see a mask, someone else has previously georeferenced the map. Please check their work and consider improving it. You can also select another map to georeference.

### Step 3: Adding Ground Control Points

- Now go to the **Georeference** tab. On the left you see the selected image, on the right a world map. Zoom to the relevant region on the world map. You can easily zoom to a region by holding shift and drawing a box, or by searching for a location by clicking the magnifying glass button. Click a point you recognize on both maps which has remained the same over time, such as a church tower or a road crossing. Add the point on both sides by clicking on the image and map; a number will indicate that they are paired. Add at least three of these points (they are called _control points_). Ideally, they are spread out over the map and do not lay on a straight line.

> **navPlace**
>
> If the loaded IIIF Manifest contains a [navPlace](https://iiif.io/api/extension/navplace/) property, this will be used to initiate the map view.

- Open the Maps menu to obtain an overview of your masks and their control points. You can remove points if needed. You can also select another mask and start adding control points for that one. The ordering might change after reloading the page.
- You can rotate the image and map by holding `crtl` and dragging the respective views.
- Once you have added three points, the warped mask will be rendered in the map view. You can customize this behavior through the settings menu (click the cogwheel icon in the map view). The first options set the visibility of the mask and opacity of the warped map for the Georeference and Results tabs. Below that you can customize the reference map and load a custom XYZ tile source or another Georeference Annotation.

### Step 4: Viewing and exporting results

- After creating three or more points, click the **Results** tab. The image is now cropped and rendered on top of the world map. You can zoom and pan this view and use `space` to toggle between image and map. In the menu at the bottom center you can choose to show only the current map, all maps of the current image or all maps in the current resource (which could have multiple images).
- Open the Maps panel the mask and control points. Next to the map, there’s a dropdown menu with the name Polynomial. This refers to the transformation algorithm used to convert between pixels and geospatial coordinates. You can try changing it to Helmert or Thin plate spline to see if this gives a more satisfactory result.

> **Transformation algorithms**
>
> Polynomial uses a homogenous transformation to fit the image on the map (by moving, scaling, rotating and skewing it). This means that the control points might not be rendered in their exact geographical position. Helmert does the same without skewing the image. Thin plate spline respects the location of each control point and will transform the map between those points. This can result in a more distorted image.

- Click the Export button on the top right to inspect the data you have created in the previous steps.

> **Georeference Annotation**
>
> This JSON-LD document contains one or more Georeference Annotations. These conform to the specifications of the [Georeference Extension](https://iiif.io/api/extension/georef/), an official extension to the IIIF Presentation API and contain the following parts:
>
> - A reference to the IIIF Resource that has been annotated under target \> source.
> - The mask that indicates the location of the map under target \> selector.
> - The control points and chosen transformation algorithm under body.
>
> Multiple annotations will be exported as an [Annotation Page](https://www.w3.org/TR/annotation-model/#annotation-page), which contains a list of Georeference Annotations.

- A IIIF Manifest (with multiple images) or a single IIIF Image can contain multiple maps. When viewing or exporting the results, different options are available for exporting annotations of the currently selected map (or mask), the current image, or the entire manifest. The following options can be selected under **Export options for**:
	- Current map: refers to the current selected mask (and related control points). This selection can be changed in the Maps menu.
	- Current image: refers to all the masks (and related control points) of the currently selected IIIF Image (or Canvas)
  - All images: refers to all the masks (and related control points) of all the images in the current IIIF Manifest (see the Images tab). This option won’t be visible when opening a single IIIF Image.
- The export panel contains various options to export your work. An overview of the options:
  - View in Allmaps Viewer: opens the Georeference Annotation in Allmaps Viewer, which has more advanced options to view maps. Clicking this link loads the annotation directly from the Allmaps database. This means that new edits in the Editor will become visible in the Viewer after refreshing the page. You can leave both tabs open to improve your work.
  - Georeference Annotation: opens the Georeference Annotation (or an Annotation Page with multiple annotations, depending on your selection) in a new window.
  - XYZ map tiles: Opens a preview of the map loaded through an XYZ tile proxy, or copies the XYZ template URL. This can be used to load the map in GIS-applications.

### Managing annotations

Allmaps plans to release a tool for keeping track of your georeference maps and managing crowd-sourcing projects. Until this becomes available it's a good idea to keep track of all the images you georeferenced and the georeference annotations they resulted in, especially when working with groups. This could be for example a sheet with the following columns:

- Title
- Resource URI
- Georeferencing status: (todo, in progress, to verify, done, …)
- Georeference Annotation URI
- Georeference Annotation JSON or name and location of downloaded JSON file
- Notes

## Finding IIIF Resources

### detektIIIF3

[detektIIIF3](https://chromewebstore.google.com/detail/detektiiif3/aaodcobgcadinjipaocibamdfcffpcpp) is a browser extension for Chrome that will indicate if a IIIF URL is available for the currently opened web page. If this is the case, it will list those URLs and allow you to copy them. This is a great way of finding IIIF resources and opening them in Allmaps: URLs copied from the Manifests, Images and Collections tabs can be pasted in Allmaps Editor and Viewer.

In the options of the plugin you can also add the following patterns under Manifest Viewers for opening resources in Allmaps directly:

| Label | URL |
|---|---|
|Allmaps Viewer|`https://viewer.allmaps.org/?url=%%%URI%%%`|
|Allmaps Editor|`https://editor.allmaps.org/images?url=%%%URI%%%`|

### Institutions

Below is a list of organizations and repositories supporting IIIF. Trailing emojis 🌱 and 🚀 respectively indicate Allmaps Supporters and Innovators as part of the [Allmaps-IIIF Partnership](https://allmaps.org/iiif-partnership).

- [4TU.ResearchData](https://data.4tu.nl/)
- [Austrian Academy of Sciences](https://www.oeaw.ac.at/en/)
- [Bayerische Staatsbibliothek](https://www.digitale-sammlungen.de/en/search?query=&sortField=scanDate&filter=type_content%3A%22map%22&filter=features%3A%22iiif%22)
- [Bibliothèque nationale de France 🌱](https://gallica.bnf.fr/)
- [Bodleian Libraries - Oxford University 🌱](https://www.bodleian.ox.ac.uk/home)
- [David Rumsey Map Collection](https://www.davidrumsey.com/luna/servlet/view/all)
- [Det Kgl. Bibliotek](https://www5.kb.dk/maps/kortsa/2012/jul/kortatlas/subject206/da/)
- [Digital Commonwealth](https://www.digitalcommonwealth.org/search?f%5Bgenre_basic_ssim%5D%5B%5D=Maps)
- [Eesti Rahvusraamatukogu 🌱](https://www.rara.ee/en/)
- [Erfgoed Leiden en Omstreken](https://www.erfgoedleiden.nl/)
- [Ghent Centre for Digital Humanities](https://ghentcdh.ugent.be)
- [Gouda Tijdmachine](https://www.goudatijdmachine.nl/data/collection/ark:/60537/bb25wx)
- [Harvard Library Digital Collections](https://digitalcollections.library.harvard.edu/catalog?f%5BresourceType%5D%5B%5D=cartographic)
- [Indiana University Libraries 🌱](https://libraries.indiana.edu/)
- [Institut Cartogràfic i Geològic de Catalunya](https://cartotecadigital.icgc.cat/)
- [Kent State University Libraries](https://www.library.kent.edu/special-collections-and-archives)
- [Leventhal Map & Education Center at the Boston Public Library](https://www.leventhalmap.org/)
- [Library of Congress](https://www.loc.gov/maps/)
- [Los Angeles Public Library](https://www.lapl.org/digital-library)
- [Minnesota Digital Library](https://mndigital.org)
- [Musea Brugge](https://www.museabrugge.be/collecties/doorzoek?subject=cartografie)
- [Nasjonalbiblioteket](https://www.nb.no/search?mediatype=kart)
- [Nationaal Archief](https://www.nationaalarchief.nl/onderzoeken/zoeken?activeTab=maps)
- [National Library of Scotland](https://maps.nls.uk)
- [New York Public Library 🌱](https://digitalcollections.nypl.org/search/index?filters%5Btype%5D=cartographic)
- [Penn State University Libraries](https://libraries.psu.edu)
- [Polona](https://polona.pl)
- [Princeton University Library](https://maps.princeton.edu)
- [Rijksdienst voor het Cultureel Erfgoed](https://beeldbank.cultureelerfgoed.nl)
- [Riksarkivet](https://sok.riksarkivet.se)
- [Stadsarchief Amsterdam](https://archief.amsterdam/beeldbank)
- [Stanford Libraries 🚀](https://earthworks.stanford.edu/catalog?featured=scanned_maps)
- [State Library Victoria](https://www.slv.vic.gov.au/search-discover)
- [TU Delft Library](https://heritage.tudelft.nl/)
- [Texas A&M University Libraries 🌱](https://library.tamu.edu/)
- [The National Library of Wales 🌱](https://www.library.wales/)
- [Universitaire Bibliotheken Leiden](https://digitalcollections.universiteitleiden.nl)
- [Universiteitsbibliotheek Gent](https://lib.ugent.be/en/catalog?access=zoomable&type=map)
- [Universiteitsbibliotheek Utrecht](https://www.uu.nl/en/utrecht-university-library-special-collections/collections/maps-and-atlases)
- [Universiteitsbibliotheek VU](https://researchworks.oclc.org/iiif-explorer/search?q=collection.id%3Ahttps%3A%2F%2Fresearchworks.oclc.org%2Fdigital%2Fdataset%2F21033_krt)
- [Universiteitsbibliotheek van Amsterdam 🌱](https://uvaerfgoed.nl/)
- [University of Chicago Library 🌱](https://www.lib.uchicago.edu/collex/collections/)
- [University of Colorado Boulder](https://scholar.colorado.edu)
- [University of Groningen](https://dbc.rug.nl/)
- [Yale Library 🚀](https://collections.library.yale.edu/)

### Repositories

The following repositories support IIIF and can be used to publish your own images:

- [4TU.ResearchData](https://data.4tu.nl/)
- [Zenodo](https://zenodo.org/)
- [Internet Archive](https://archive.org/)

### 4TU.ResearchData IIIF Service

Datasets in the [4TU data repository](https://data.4tu.nl/) can be accessed through the IIIF APIs. You can find the link to the IIIF Manifest under the interoperability header in the right side bar. For example:

| Dataset URL | IIIF Presentation API endpoint |
| --- | --- |
| `https://data.4tu.nl/datasets/8289a903-7ccf-401b-af66-f5b3c9abe4b6/1` | `https://data.4tu.nl/iiif/v3/8289a903-7ccf-401b-af66-f5b3c9abe4b6/1/manifest` |

Individual Image API endpoints are based on the asset UUIDs:

| File URL | IIIF Image API endpoint |
| --- | --- |
| `https://data.4tu.nl/file/8289a903-7ccf-401b-af66-f5b3c9abe4b6/24bcf6b4-c5d5-4e3c-9cc7-3af30607481a` | `https://data.4tu.nl/iiif/v3/8289a903-7ccf-401b-af66-f5b3c9abe4b6/24bcf6b4-c5d5-4e3c-9cc7-3af30607481a` |

For draft datasets, Presentation API endpoints can be accessed as follows; but only after login:

`https://data.4tu.nl/iiif/v3/[uuid]/draft/manifest`

The response could be saved in e.g. a GitHub gist to make it available on the internet without authentication.