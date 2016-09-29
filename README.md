# Open Source Web Cartography: A Mapping Short Course

The availability of code-free, push-button interfaces for making sophisticated web maps remains an ongoing goal for the web mapping community (e.g., [CARTO's Builder](https://carto.com/builder/), [Mapbox's Studio](https://www.mapbox.com/mapbox-studio/), or [ESRI's Configurable Apps](http://www.esri.com/software/configurable-apps)). However, proficiency in the web scripting languages of HTML, SVG, CSS, and JavaScript allows web cartographers to enhance the user experience of web maps beyond what is provided by such tools. The growing availability of freely distributed, open source code libraries and open Application Programming Interfaces (APIs) provide web mappers with advanced geoprocessing, representation, and interaction capabilities. This short course will introduce students to the design and development practices of building customized web maps and explore a variety of thematic mapping techniques.

## Learning Objectives

By the end of this course, students will be able to:

* Identify and construct the principle technological components of a web mapping development stack.
* Assemble geographic data into appropriate data formats for integration within a web mapping system.
* Demonstrate the ability to load data from local and remote sources and draw geometry features within a client-side web browser.
* Interpret the functionality provided by a web mapping library's Application Programming Interface (API) and adapt examples to specific use cases.
* Construct functional thematic web maps using raster, point, line, and areal symbology.
* Experiment with various plugins designed to extend the core functionality of a web mapping library.
* Utilize a remote web server for hosting and sharing web maps.

## Requirements

### Software Requirements

The course will make use of the following software components, which are freely available on the web:

* A text editor ([Brackets](http://brackets.io/), [Sublime](https://www.sublimetext.com/), or [Atom](https://atom.io/))
* A modern web browser (Chrome or Firefox recommended)
* Web developer tools (built into modern browsers)
* A local web server

The course will introduce and demonstrate use cases for the following open source JavaScript libraries:

* [JQuery](https://jquery.com/)
* [Leaflet](http://leafletjs.com/)
* [Turf](http://turfjs.org/)
* [Simple Statistics](http://simplestatistics.org/)
* [TopoJson](https://github.com/mbostock/topojson/wiki)

Additionally, course materials are made available through the [GitHub](https://github.com) web platform. These may be downloaded as a zip file or cloned through a git command or desktop client interface. GitHub is also used to freely host and serve complete web maps over the Internet.

### Assumed Background Knowledge

The learning curve for web development is steep, and mastering web mapping requires wrestling with an intimidating array of tools and technical jargon. Teaching computer programming and covering the breadth of geospatial technologies is beyond the scope of this short course. Some experience with computer programming or web design is helpful, and supplementary technical learning is encouraged.

That stated, the course is intended as a gentle introduction to web mapping and assumes no expertise in coding or Geographic Information Science. Modules provide code examples and templates for completion of exercises.

Most importantly, the course requires curiosity and a willingness to be confused and frustrated while puzzling through problems.

## Schedule and Location

The course comprises four weekly modules encompassing 2 hours of guided instruction each, Friday afternoons from 3 - 5 pm.

* **October 28th** -- Drawing Data with Web Maps
* **November 4th** -- Thematic Web Mapping: Point Symbology
* **November 11th** -- Thematic Web Mapping: Value by Area
* **November 18th** -- Extending Web Maps with Plugins and Web Hosting

The course will meet in the [Ken Erickson Spatial Data Analysis Lab](http://geography.colorado.edu/research/lab_facility/ken_erickson_spatial_data_analysis_lab) (Guggenheim Rm 6), on the CU-Boulder campus.

## Additional Help and Resources

* Students within the course will be encouraged to join a course [Slack](https://slack.com) channel (name TBD) for asynchronous collaboration and peer help.
* [Stack Overflow](http://stackoverflow.com/)
* [GIS Stack Exchange](http://gis.stackexchange.com/)
* [Leaflet Documentation](http://leafletjs.com/)

## Weekly Module Summary

### 1. Drawing Data with Web Maps

The introductory module acquaints students with the key components of a web mapping technology stack and the process for web map development: write code, refresh results, debug, repeat. The lesson underscores the importance of the GeoJSON data format and demonstrates techniques for its encoding and conversion from the Shapefile format. Students use JQuery to load data into a web script. A popular and mobile-friendly web mapping library, Leaflet, is then used to load a raster basemap, draw GeoJSON point data as marker icons and polyline and polygon data as vector geometries. Basic user interaction operators are used to retrieve specific feature information and toggle the visibility of overlays.

### 2. Thematic Web Mapping: Point Symbology

The second module explores cartographic techniques for representing point features within a web map. Students learn a process for loading Comma Separated Values (CSV) data into a script and converting them to GeoJSON before drawing them to the map. Custom written code then uses the visual variable of size to represent quantitative data attribute values and create a proportional symbol map. Students then extend the point symbol map to encode nominal attribute data using the visual variable of color (or hue) to produce a bi-variate map. The lesson demonstrates user interaction techniques for filtering represented data.

### 3. Thematic Web Mapping: Value by Area

The third module explores techniques for making a value by area (or choropleth) map. Students use web-based tools first to convert areal geometries into the TopoJSON data format, which explicitly encodes spatial topology and reduces redundant shared borders within geometry data. The JavaScript library Turf provides powerful geoprocessing capabilities within the browser, without the need for a desktop GIS. Client-side code dynamically classifies data for encoding areal units by saturation level

### 4. Extending Web Maps with Plugins and Web Hosting

The final module further extends the core functionality of a library's API through the employment of [plugins](http://leafletjs.com/plugins.html), which build upon the open codebase of the Leaflet library. Students are encouraged to play with plugin functionality best-suited to meet the map user's objectives. Finally, the module documents a streamlined approach for easily hosting web maps using GitHub.