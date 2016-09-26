# Open Source Web Cartography

## A Mapping Short Course

The availability of code-free, push-button interfaces for making sophisticated web maps remains an ongoing goal for the web mapping community (e.g., [CARTO's Builder](https://carto.com/builder/), [Mapbox's Studio](https://www.mapbox.com/mapbox-studio/), or [ESRI's Configurable Apps](http://www.esri.com/software/configurable-apps)). Gaining proficiency in web scripting languages such as HTML, CSS, and JavaScript allows web cartographers to further customize the user experience of web maps far beyond that which is provided by such tools. The availability of freely distributed, open source code libraries and application programming interfaces (APIs) provide web mappers with a growing array of geoprocessing, representational, and interaction capabilities. This short course will introduce students to the design and development practices of building custom modern, open source web maps.

**Learning Objectives**

By the end of this course, students will be able to:

* Identify and construct the principle technological components of a web mapping development stack.
* Assemble geographic data into appropriate data formats for integration within a web mapping system.
* Appraise the advantages and disadvantages of storing data in flat files vs a database.
* Manage data within a PostGIS/PostGreSQL-enabled database.
* Demonstrate the ability to load and draw data within a web document from local and remote sources.

**Requirements**

* A computer of reasonable speed and memory.
* An internet connection.
* A curiosity and a willingness to be confused and frustrated.


##1. Drawing Data with Web Maps

* Setting up a development environment
* A hello world web map
    * HTML (structure)
    * CSS (form)
    * JavaScript (behavior)
* How we store geographic information
    * various formats: Shapefile, GeoJSON,
    * flat file vs. cloud-based database
* How we load data into a web map
    * On document load
    * async via:
        * JQuery.js
        * Onnivore.js
        * Queue.js
* loading raster tiles into a web map
* drawing the building blocks of vector web mapping
    * points
    * lines
    * polygons
* UI operators: retrieving feature information and toggling overlays
* making the map whole (map elements and legends)
    * map titles
    * setting context with supplementary text
    * including metadata
    * map legends

## 2. Thematic Web Mapping: Value by Size

* making a proportional symbol map
* 

## 3. Thematic Web Mapping: Value by Area

* what's the deal with projections?
* making a choropleth web map
    * drawing polygons
    * determining class breaks
        * pre-determined/manual
        * dynamic
    * mapping class breaks to color scales

Example: Leaflet
Example: D3

## 4. 



