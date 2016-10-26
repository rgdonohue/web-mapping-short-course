# Lesson 01. Drawing Data with Web Maps

Intro here bla bla bla.

To begin, clone or [download the course repository](https://github.com/rgdonohue/web-mapping-short-course) to your computer.

Clone or unzip the contents of the files in a known location (i.e., your Desktop or Documents). Briefly examine the contents of the directory named `module-01`. 

## Setting up a development environment (15 min)

There are many resources and tools for getting going with web mapping. But sometimes getting the development environment set up so you can write code and test your map is overlooked. Let's consider the principle components of a web development process:

**A Web Browser**

Web Mapping is an interesting form of Cartography in that we largely make the maps using the same medium with which we develop them. The web browser is a crucial component of our technology stack. Most web map developers use Chrome or Firefox, as you should. Make sure your browser has installed recent updates.

**Web Develper Tools**

Modern web browsers come installed with web developer tools. These tools come loaded with funtionality allowing you to investigate how a web page or application is structured and performing within your browser. Read more about using the [Chrome DevTools](https://developer.chrome.com/devtools), and as always look for the shortcuts to open and close the toolbar in your browser (Cmd + i in Mac OS).

![Opening Chrome's Web Developer Tools'](lesson-images/open-developer-tools.png)  
**Figure 01.** Opening Chrome's Web Developer Tools.

One of the most useful features is the [Console](https://developer.mozilla.org/en-US/docs/Web/API/Console), which allows you to log JavaScript values within the browser. You can type directly into the Console, or log values from a JavaScript file loaded within the browser. We'll be doing both as we build and debug web maps.

Open your web developer toolbar.

**A Text Editor**

We build web maps largely by writing plain text. Text editors designed for web development facilitate this, particular by highlighting different parts of the code syntax. Install and open one of the following:

* [Brackets](http://brackets.io/)
* [Sublime](https://www.sublimetext.com/)
* [Atom](https://atom.io/)

Brackets is particularly handy if you don't have a local host server running or don't know what that is. Its "Live Preview" functionality runs a local host within your web browser, which allows you to see and test your rendered web application.

**A Web Server**

While a web browser application interpret and render the files that comprise our web maps, they don't do this by themselves. They require a "server" to correctly gather the files and deliver them to the browser. 

**Directories, Files, Data, and Media**

The user's web browser assembles and renders the web page and map applicaiton using specific files. Minimally this will include an HTML index file for the direction, typically named **index.html**.

Using your text editor, open the **module-01** directory. A good text editor allows you view and modify the contents of the directory. Again examine the contents of this directory from within the editor.

Open the **index.html** contained with the directory named **leaflet-map-template** and open this file within your browser. Be sure this is done with the Live Preview of Brackets or using another local host server such as [Python's SimpleHTTPServer](http://www.pythonforbeginners.com/modules-in-python/how-to-use-simplehttpserver/).



## Introducing the building blocks of a "hello world" web map (15 min)

Let's begin with a simple working template for making a web map. 



    * HTML (structure)
    * CSS (form)
    * JavaScript (behavior)
	* loading raster tiles into a web map
	
## Scenario: mapping your route from home to campus

For this lesson we're going to make a Leaflet map of your route to or from campus (pick one for now if they are different). The goal of the map is to allow the user to see your starting and ending points, the route between them, as well as a couple places of interest along the way. Perhaps you stop at a cafe or your place of work. We want to capture this geography, convert it to an apppropriate data format, and display it on a web and mobile-friendly map. Additionally, we can allow the user to retrieve specific information about these places through interacting with the map (in this case, hovering over the map or touching on a marker).

To begin, copy the *leaflet-map-template/* directory and rename it to *app*.

### Step 1: Data aquisition and conversion

To get our data and convert it to an appropriate format for web mapping, we're going to use a few web-based tools. 

Let's first use a fantastic (proproritary) mapping resource: [Google Maps](https://www.google.com/maps)!

1. First, search for your primary campus building. For instance, I'll do a simple Google Map search for [Guggenheim Geography](https://www.google.com/maps/place/Guggenheim+Geography,+Boulder,+CO+80302/@40.0081521,-105.2764582,16.98z/data=!4m5!3m4!1s0x876bec31173b714d:0xfe71b5ee5f7fee43!8m2!3d40.0081661!4d-105.2742872).

2. Then use the Directions functionality to determine the route from your home to your building. **BE CAREFUL:** This map is going to end up on the web. Do you want people knowing your exact address? Maybe not! Use an approximate address location instead. Also, be sure to select the mode of travel. Do you drive a car, ride a bus, walk, or ride your bike? If you fly a plane to get to campus, that's incredible!

![Using Google Maps to find a route and mode from home to Campus](lesson-images/google-maps-route.png)  
**Figure XX.** Using Google Maps to find a route and mode from home to Campus.

Google Maps allows you to pick between alternative routes, as well as to drag the route to customize the route you really take. Feel free to adjust this a little bit, but don't worry to much about it. We'll be using another tool to do this later on.

When you have highlighted your desired route in blue on the map, copy the enture URL from the address bar (highlight it, and select *Edit -> Copy* or *Cntr + C*).

3. Next, go to a website named [Maps To GPX](https://mapstogpx.com/), a tool that, "accepts a link to pre-made Google Directions and converts them to a GPX file." This is perfect for us!

Paste your URL from Google Maps into the form and hit "Let's Go." 

![Converting Google Maps Route to GPX](lesson-images/mapstogpx.png)  
**Figure 01.** Converting Google Maps Route to GPX.

The site will make the necessary conversion and prompt the download of the GPX file (with a name something like *mapstogpx20161026_000913.gpx*). Move this file into the *module-01/app/data/* directory.

GPX (the GPS Exchange Format) is a text-based format derived from XML and often used to encode GPS data. You can open this file in your text editor to examine the contents. We're not too interested in particular file, but it looks like this:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<gpx xmlns="http://www.topografix.com/GPX/1/1" xmlns:gpxx="http://www.garmin.com/xmlschemas/GpxExtensions/v3" xmlns:gpxtpx="http://www.garmin.com/xmlschemas/TrackPointExtension/v1" creator="mapstogpx.com" version="1.1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.topografix.com/GPX/1/1 http://www.topografix.com/GPX/1/1/gpx.xsd http://www.garmin.com/xmlschemas/GpxExtensions/v3 http://www.garmin.com/xmlschemas/GpxExtensionsv3.xsd http://www.garmin.com/xmlschemas/TrackPointExtension/v1 http://www.garmin.com/xmlschemas/TrackPointExtensionv1.xsd">
  <metadata>
    <link href="http://www.mapstogpx.com">
      <text>Sverrir Sigmundarson</text>
    </link>
    <!--desc>Map data ©2016 Google</desc-->
    <!--url>https://www.google.co.uk/maps/dir/40.035196,-105.2809662/40.008162,-105.27423/@40.0215947,-105.2933284,14z/data=!3m1!4b1!4m2!4m1!3e1?hl=en</url-->
    <time>2016-10-23T15:57:30Z</time>
  </metadata>
  <wpt lat="40.035196" lon="-105.2809662">
    <name>3315 13th Street</name>
    <desc>3315 13th Street, Boulder, CO 80304, USA</desc>
  </wpt>
```

If you happen to use the popular [Strava](https://www.strava.com/) service, you can also download all your routes in GPX format.

4. Next, we want to convert our data to another format: [GeoJSON](http://geojson.org/). GeoJSON is to web mapping what the Shapefile is to GIS.

Navigate your browser to a website called [geojson.io](http://geojson.io/). You'll want to bookmark this website, as it's an extremely useful online tool.

Open your GPX file in the geojson.io web application. Study the code generated in the right-hand panel. This is a valid GeoJSON encoding of your route. Unlike Shapefiles, GeoJSON can encode multiple geometry types within a single Feature Collection. Note that  Features have both `properties` and `geometry` attributes. The `"LineString"` type contains all the points that make up the route, while the two `"Point"` type Features encode the endpoints of the route.

Take some time to play around with the geojson.io website and your data.

Note that some data attributes have been retained from Google Maps that we don't need. We can remove these, and edit the exisiting data properties as we wish. The web application also allows us to add, remove, and edit geometries. For example you could modify your route.

![Removing unneeded attribute properties in geojson.io](lesson-images/geojson-io-edit.gif)  
**Figure XX.** Removing unneeded attribute properties in geojson.io.

Instead, let's add a couple more places of interest. Using the drawing tools, place a point of interest along your route. Add a property row to the marker, and be sure to use the word "name" as the name of the attribute (just like the other points). Geojson.io also adds some other properties to style the marker. We don't need these, and you can remove them in the editor.

![Adding a placemarker in geojson.io](lesson-images/geojson-io-add-point.gif)  
**Figure XX.** Adding a placemarker in geojson.io.

Once you're done editing your data, choose **Save** and download as a GeoJSON (it will download with the file name *map.geojson*. Save or move this downloaded file into your *module-01/app/data/* directory.

You can open this file in your text editor to see that it's the same as what geojson.io displayed.

```js
{"type":"FeatureCollection","features":[{"type":"Feature","properties":{"name":"Northbrook Drive to Guggenheim Geography"},"geometry":{"type":"LineString","coordinates":[[-105.2601844,40.0446618],[-105.26024,40.04472],[-105.2602362,40.0447162],[-105.26029,40.04469],[-105.26033,40.04466],[-105.26043,40.04458],[-105.26056,40.04451],[-105.26065,40.04448],[-105.2607,40.04447],[-105.26073,40.04447],[-105.26075,40.04446],[-105.26078,40.04443],[-105.2608,40.04439],[-105.26083,40.04438],[-105.26086,40.04437],[-105.26093,40.04436],[-105.2609275,40.0443637],[-105.26094,40.0444],[-105.26095,40.04446]
```

This last step of modifying our data attributes, editing the geometries, and exporting to GeoJSON wraps up our data aquisition and conversion process. Next, let's get the data loaded into the web map.

### Step 2: Loading external data into a web document.

There are various ways to load GeoJSON data into your web map. While the best (and more sophisticated) way is to make an [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming) request, we'll begin with a more simple solution.

First, rename the *map.geojson* file to *route.js*. Then open the *route.js* file in your text editor and assign the entire GeoJSON structure to a variable named *data*:

```js
var data = {"type":"FeatureCollection","features":[{"type":"Feature","properties":{"name":"Northbrook Drive to Guggenheim Geography"},"geometry":{"type":"LineString","coordinates":[[-105.2601844,40.0446618],[-105.26024,40.04472],[-105.2602362,40.0447162],[-105.26029,40.04469],[-105.26033,40.04466],[-105.26043,40.04458],[-105.26056,40.04451],[-105.26065,40.04448],[-105.2607,40.04447],[-105.26073,40.04447],[-105.26075,40.04446],[-105.26078,40.04443],[-105.2608,40.04439],[-105.26083,40.04438],[-105.26086,40.04437],[-105.26093,40.04436],[-105.2609275,40.0443637],[-105.26094,40.0444],[-105.26095,40.04446]
```

Save those changes to the file. GeoJSON is essentially a JavaScript object, and we've simpily assigned it to a JavaScript variable. The variable `data` will now be available to us within our script. 

Next open the *index.html* file within our *module-01/app/* directory.

The script is currently loading the external using the `<script>` element, remote jQuery and Leaflet JavaScript files, before our custom code is executed. Let's load this JavaScript file into our document in the same way, being careful to specify a relative path to our file contained within the *data* directory.

This step saved our GeoJSON file within a JavaScript file, assigned it to a variable, and modified the HTML to load the file on page load.

Now it's time to draw it to our map!

### Step 3: Drawing GeoJSON to the map.







	
