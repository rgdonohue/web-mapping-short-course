# Lesson 01. Drawing Data with Web Maps

## Setting up a development environment
    * **exercise:** establish file/dir structure, open files with text-editor, launch local server (`python -m SimpleHTTPServer` or use Brackets)


## Introducing the building blocks of a "hello world" web map
    * HTML (structure)
    * CSS (form)
    * JavaScript (behavior)
	* loading raster tiles into a web map
	
## How we store geographic information
    * various formats: Shapefile, GeoJSON
        * **exercise:** create data on geojson.io
    * flat file vs. cloud-based database
	
## How we load data into a web map
    * On document load
    * async via:
        * JQuery.js
        * Queue.js
          * **exercise:** copy paste data from geojson.io into files and load into script

## drawing the building blocks of vector web mapping
    * points
    * lines
    * polygons
     * **exercise:** draw data with `L.geoJson()` and style
	 
* UI operators: retrieving feature information and toggling overlays
    * * **exercise:** retrieve feature-specific information using Leaflet tooltip and popups
    * * **exercise:** add UI control to toggle on and off layers