# Open Source Cartography: A Web Mapping Short Course

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

## Additional Help and Resources

* [Stack Overflow](http://stackoverflow.com/)
* [GIS Stack Exchange](http://gis.stackexchange.com/)
* [Leaflet Documentation](http://leafletjs.com/)

## Weekly Module Summary

### 1. Drawing Data with Web Maps

The introductory lesson acquaints students with the key components of a web mapping technology stack and the development environment. Students will learn how to use Leaflet, a popular and mobile-friendly web mapping library, to build a simple web map using data converted to GeoJSON format. The class will explore techniques for drawing (or representing) geographic features such as points and lines on various available basemaps, styling these features, and adding basic user interaction to retreive specific information about meaningful places on the map.

### 2. Thematic Web Mapping: Point Symbology

The second lesson explores cartographic techniques for representing point features within a web map. Students learn a process for loading Comma Separated Values (CSV) data into a script and converting them to GeoJSON before drawing them to the map. Students are taught a technique for programmatically re-sizing circles based on quantitative data attribute values to create a proportional symbol map. Students then extend the point symbol map to encode nominal attribute data using color to produce a bi-variate map. The lesson concludes by introducing user interaction techniques for filtering represented data.

### 3. Thematic Web Mapping: Value by Area

The third lesson explores techniques for making the popular choropleth map. Students use web-based tools first to convert polygons such as census tracks into appropriate data formats before writing code to dynamically classify data for representing different values. The lesson also introduces the popular JavaScript library Qjuery, to assist in loading data from external sources.

### 4. Extending Web Maps with Plugins and Web Hosting

The final module further extends the core functionality of a library's API through the employment of [plugins](http://leafletjs.com/plugins.html), which build upon the open codebase of the Leaflet library. Students are encouraged to play with plugin functionality best-suited to meet the map user's objectives. Finally, the module documents a streamlined approach for easily hosting web maps using GitHub.