# Lesson 01. Drawing Data with Web Maps

Intro here bla bla bla.

To begin, clone or [download the course repository](https://github.com/rgdonohue/web-mapping-short-course) to your computer.

Clone or unzip the contents of the files in a known location (i.e., your Desktop or Documents). Briefly examine the contents of the directory named `module-01`. 

## Setting up a development environment (15 min)

There are many resources and tools for getting going with web mapping. But sometimes getting the development environment set up so you can write code and test your map is overlooked. Let's consider the principle components of a web development process:

*A Web Browser*

Web Mapping is an interesting form of Cartography in that we largely make the maps using the same medium with which we develop them. The web browser is a crucial component of our technology stack. Most web map developers use Chrome or Firefox, as you should. Make sure your browser has installed recent updates.

*Web Develper Tools*

Modern web browsers come installed with web developer tools. These tools come loaded with funtionality allowing you to investigate how a web page or application is structured and performing within your browser. Read more about using the [Chrome DevTools](https://developer.chrome.com/devtools), and as always look for the shortcuts to open and close the toolbar in your browser (Cmd + i in Mac OS).

![Opening Chrome's Web Developer Tools'](lesson-images/open-developer-tools.png)
*Figure 01. Opening Chrome's Web Developer Tools.*

One of the most useful features is the [Console](https://developer.mozilla.org/en-US/docs/Web/API/Console), which allows you to log JavaScript values within the browser. You can type directly into the Console, or log values from a JavaScript file loaded within the browser. We'll be doing both as we build and debug web maps.

Open your web developer toolbar.

*A Text Editor*

We build web maps largely by writing plain text. Text editors designed for web development facilitate this, particular by highlighting different parts of the code syntax. Install and open one of the following:

* [Brackets](http://brackets.io/)
* [Sublime](https://www.sublimetext.com/)
* [Atom](https://atom.io/)

Brackets is particularly handy if you don't have a local host sever running or don't know what that is. Its "Live Preview" functionality runs a local host within your web browser, which allows you to see and test your rendered web application.

*A Web Server*

While a web browser application interpret and render the files that comprise our web maps, they don't do this by themselves. They require a "server" to correctly gather the files and deliver them to the browser. 



*Directories, Files, Data, and Media*

The user's web browser assembles and renders the web page and map applicaiton using specific files. Minimally this will include an HTML index file for the direction, typically named **index.html**.

Using your text editor, open the **module-01** directory. A good text editor allows you view and modify the contents of the directory. Again examine the contents of this directory from within the editor.

Open the **index.html** contained with the directory named **leaflet-map-template** and open this file within your browser. Be sure this is done with the Live Preview of Brackets or using another local host server such as [Python's SimpleHTTPServer](http://www.pythonforbeginners.com/modules-in-python/how-to-use-simplehttpserver/).



## Introducing the building blocks of a "hello world" web map (15 min)
    * HTML (structure)
    * CSS (form)
    * JavaScript (behavior)
	* loading raster tiles into a web map
	
## Scenario: mapping your route from home to campus

For this lesson we're going to make a Leaflet map of your route
	
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