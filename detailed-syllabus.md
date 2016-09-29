# Detailed lesson outline

## 1. Drawing Data with Web Maps

* Setting up a development environment
    * **exercise:** establish file/dir structure, open files with text-editor, launch local server (`python -m SimpleHTTPServer`)
* Introducing the building blocks of a "hello world" web map
    * HTML (structure)
    * CSS (form)
    * JavaScript (behavior)
* How we store geographic information
    * various formats: Shapefile, GeoJSON
        * **exercise:** create data on geojson.io
    * flat file vs. cloud-based database
* How we load data into a web map
    * On document load
    * async via:
        * JQuery.js
        * Queue.js
          * **exercise:** copy paste data from geojson.io into files and load into script
* loading raster tiles into a web map
* drawing the building blocks of vector web mapping
    * points
    * lines
    * polygons
     * **exercise:** draw data with `L.geoJson()` and style
* UI operators: retrieving feature information and toggling overlays
    * * **exercise:** retrieve feature-specific information using Leaflet tooltip and popups
    * * **exercise:** add UI control to toggle on and off layers


## 2. Thematic Web Mapping: Point Symbology

* storing point data as CSV
* transforming CSV to GeoJSON (Omnivore.js)
* making a proportional symbol map using `pointToLayer()`
* making a bi-variate map using `style()`

## 3. Thematic Web Mapping: Value by Area

* using Turf.js to do server-side geoprocessing (point in polygon)
* making a choropleth web map
    * drawing polygons (topojson)
    * determining class breaks
        * pre-determined/manual
        * dynamic classification (using simplestats.js)
    * mapping class breaks to color scales


## 4. Extending Web Maps with Plugins and Hosting Web Remote Maps

