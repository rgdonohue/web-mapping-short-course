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
**Figure 01. Opening Chrome's Web Developer Tools.**

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

### Step 1: Get the Data

To get our data and convert it to an appropriate format for web mapping, we're going to use a few web-based tools. 

Let's first use a fantastic (proproritary) mapping resource: [Google Maps](https://www.google.com/maps)!

1. First, search for your primary campus building. For instance, I'll do a simple Google Map search for [Guggenheim Geography](https://www.google.com/maps/place/Guggenheim+Geography,+Boulder,+CO+80302/@40.0081521,-105.2764582,16.98z/data=!4m5!3m4!1s0x876bec31173b714d:0xfe71b5ee5f7fee43!8m2!3d40.0081661!4d-105.2742872).

2. Then use the Directions functionality to determine the route from your home to your building. **BE CAREFUL:** This map is going to end up on the web. Do you want people knowing your exact address? Maybe not! Use an approximate address location instead. Also, be sure to select the mode of travel. Do you drive a car, ride a bus, walk, or ride your bike? If you fly a plane to get to campus, that's incredible!

![Using Google Maps to find a route and mode from home to Campus](lesson-images/)  
**Figure XX.** Using Google Maps to find a route and mode from home to Campus.

Google Maps allows you to pick between alternative routes, as well as to drag the route to customize the route you really take. Feel free to adjust this a little bit, but don't worry to much about it. We'll be using another tool to do this later on.

When you have highlighted your desired route in blue on the map, copy the enture URL from the address bar (highlight it, and select *Edit -> Copy* or *Cntr + C*).

Next, go to a website named Maps To 


https://mapstogpx.com/
	
