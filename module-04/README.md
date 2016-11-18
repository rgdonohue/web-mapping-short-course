# Extending Web Maps with Plugins and Web Hosting

This module introduces you to some additional plugins for extending your thematic web maps. In particular, we'll investigate a couple techniques for dealing with too many point features on a web map.

Plugins extend an existing library, adding additional functionality to it. There are many designed for use with the [Leaflet library](http://leafletjs.com/plugins.html) and [Mapbox.js](https://www.mapbox.com/blog/extend-your-maps-mapboxjs-plugins/) (which wraps Leaflet.js itself and extends it)

Plugins explored in this module:

* [Leafet.markercluster GitHub repo](https://github.com/Leaflet/Leaflet.markercluster)
* [Turf.js](http://turfjs.org/)
* [Leaflet Omnivore](https://github.com/mapbox/leaflet-omnivore)
* [Chroma.js](https://github.com/gka/chroma.js/)


## Leaflet.markercluster.js

Begin by editing the *index.html* file in the *marker-cluster/* directory. Take a moment to examine the *stations.geojson* data file within the *marker-cluster/data* directory. The data are locations of 13,000 electric vehicle refueling stations, drawn from [NREL's Developer Network API](https://developer.nrel.gov/).

First, let's begin by loading our data into our script using the now familiar technique of JQuery's *getJSON()* method:

```javascript
// request geojson data
$.getJSON('data/stations.geojson', function(data) {

    console.log(data)

});
```

We note that the data are loaded as 13,000 Point Features.

We could try drawing these as markers to the map (go ahead!), but we'll likely run into some rendering issues. There are too many points!

```javascript
// request geojson data
$.getJSON('data/stations.geojson', function(data) {

    makeMap(data);

});

function makeMap(data) {

  // too many markers!
  L.geoJson(data).addTo(map);

}
```

To solve this problem we'll use a technique known as "marker clustering." Go to the [Leafet.markercluster GitHub repo](https://github.com/Leaflet/Leaflet.markercluster) and examine the documentation.

We'll want to grab two CSS libraries and one JS lib. Copy the URLs to the CDNs for the CSS and place in the head of your document (along with Leaflet's CSS):


```javascript
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.0.1/dist/leaflet.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster@1.0.0/dist/MarkerCluster.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet.markercluster@1.0.0/dist/MarkerCluster.Default.css" />
```

Then do the same for the JavaScript (adding this to the existing JQuery and Leaflet JS) toward the bottom of our script.

```javascript
<script src="http://code.jquery.com/jquery-3.1.1.min.js"></script>
<script src="https://unpkg.com/leaflet@1.0.1/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet.markercluster@1.0.0/dist/leaflet.markercluster.js"></script>
```

Now that we have the markercluster CSS and JS available to us, we'll first create an empty *markerClusterGroup*. If we dig into the API docs we'll discover that this object extends Leaflet's L.geoJson object.

```javascript
// create new empty markers cluster group
var markers = L.markerClusterGroup();
```

The markercluster requires Leaflet L.marker's added to it. So, we need to iterate through our data, create a new L.marker object for each Point feature, and add it to this new L.markerClusterGroup we've created.

To do so we can use the native JavaScript method *forEach()*:

```javascript
    // for all our data features
    data.features.forEach(function(d, i) {

        // create a new Leaflet marker
        var marker = L.marker(L.latLng(d.geometry.coordinates[1], d.geometry.coordinates[0]));

        // add the marker to the markerClusterGroup
        markers.addLayer(marker);
    });

    // add the makerclusters to the map
    markers.addTo(map);
});
```

Once this is complete, we simply add our L.markerClusterGroup to the map and wa-lah! We have a functioning markercluser map!

```javascript
// add the makerclusters to the map
markers.addTo(map);
```

We can include some additional information about each feature if we'd like, displayed in Leaflet's tooltip. Before we add each marker to the *markers* object, we can include code accessing each feature's properties:

```javascript
// create a new Leaflet marker
var marker = L.marker(L.latLng(d.geometry.coordinates[1], d.geometry.coordinates[0]));

// create info for tooltip
var props = d.properties;
var popupTemplate =
    '<b>station name</b>: ' + props.station_name + '<br>' +
    '<b>city</b>: ' + props.city + '<br>' +
    '<b>hours</b>: ' + props.access_days_time + '<br>' +
    '<b>phone</b>: ' + props.station_phone + '<br>' +
    '<b>address</b>: ' + props.street_address

// bind the tooltip to the marker
marker.bindTooltip(popupTemplate);

// add the marker to the markerClusterGroup
markers.addLayer(marker);
```

Throw a title on the map and ship it! Nice work.

## Turf.js

Next we're going to explore a really fun library (not necessarily a plugin extention particular to Leaflet, but integrates nicely): [Turf.js](http://turfjs.org/). Think of Turf as GIS operations and geoprocessing in JavaScript.

Begin with the index in the *turf-hex/* directory.

Once again, we have some point data we'd like to map. This time, it's some traffic accident data in Denver from 2016, drawn from the [Denver Open Data Catalog](https://www.denvergov.org/opendata). The data are stored as CSV and contain 21,620 lat/lon values for accident locations. Obviously once again, these are too many to draw to the Leaflet map as markers.

As usual, our first step is to get the data into the application. For this, we'll make use of a plugin called [Leaflet Omnivore](https://github.com/mapbox/leaflet-omnivore). Take some time to explore the documentation and examples.

We'll need to load it into our script (there is no CSS for this plugin).

```javascript
<script src="https://api.tiles.mapbox.com/mapbox.js/plugins/leaflet-omnivore/v0.3.1/leaflet-omnivore.min.js"></script>
```

Onmivore will load our CSV data asynchronously and convert it directly into a Leaflet GeoJson object.

```javascript
// async request to load point data and convert to Leaflet GeoJSON layer
var accidents = omnivore.csv('data/accidents.csv')
  .on('ready', function(d) {

      // when data is loaded
      makeMap(data)
  })
  .on('error', function(e) {
      console.log('oh no something terrible has happened!')
  })

function makeMap(accidents) {
    // we have access to the Leaflet GeoJson here
    console.log(accidents);
}
```

Instead of using a marker cluster here, let's consider how we'd make a hexbin map. To do so, we'll use Turf.js. Load Turf.js into our script along with the other JS libs.


```javascript
<script src="http://code.jquery.com/jquery-3.1.1.min.js"></script>
<script src="https://unpkg.com/leaflet@1.0.1/dist/leaflet.js"></script>
<script src="https://api.tiles.mapbox.com/mapbox.js/plugins/leaflet-omnivore/v0.3.1/leaflet-omnivore.min.js"></script>
<script src='https://npmcdn.com/@turf/turf@3.5.1/turf.min.js'></script>
```

Looking at [Turf's API docs for hexGrid](http://turfjs.org/docs/#hexgrid) a bounding box to surround our point features.

```javascript
// get the sw/ne bounds of the accidents data layer
var bounds = accidents.getBounds();

// convert bounds to string rep of bounding coords
var bbox = bounds.toBBoxString();

// convert string to array of numbers for bounding coords
var bbox = bbox.split(',').map(function(coord) {
    return Number(coord)
});

// designate dimension of cell width
var cellWidth = 1;

// designate units for cell width calculation
var units = 'miles';

// create a featurecollection of hex polygons
var hexgrid = turf.hexGrid(bbox, cellWidth, units);
```

Next, we want to use [Turf's inside method](http://turfjs.org/docs/#inside) (which is essentially a point in polygon process). We need our point features converted back into GeoJSON for this (not Leaflet's GeoJson object).

```javascript
// convert the accidents Leaflet layer to GeoJSON
var points = accidents.toGeoJSON();
```

Next we'll use regular JavaScript to loop through all of our polygon features and then all the point features to perform the "inside" test. If a point falls within a polygon, we'll add a count of 1 to that polygon's properties. When we're done, we should have a total count of all points within each polygon stored within its properties.

```javascript
// loop through all the hex polygons
hexgrid.features.map(function(hex) {

    // create a property name for each of 'count'
    if(!hex.properties.count) hex.properties.count = 0;

    // loop through all the points
    points.features.map(function(point) {

      // if a point is inside a hex polygon
      if(turf.inside(point,hex)) {

          // add one to the prop count
          hex.properties.count++
      }

    });
});
```

Test the result with a `console.log()` statement.

Now we want to actually draw our Leaflet GeoJson object to the map using these data. While we're add it, we can style the hexbins minimally, filter out the ones that have no accident counts within them, and keep add the value of each to an array for later thematic drawing purposes:

```javascript
// empty array to store all our counts
var counts = [];

// create a Leaflet GeoJson layer with newly
// processed polygon data
var hexLayer = L.geoJson(hexgrid, {
    style: function(feature) {
      return {
        color: "white",
        weight: .2,
        fillOpacity: 1
      }
    },
    filter: function(feature) {
      // if the poly has data
      if(feature.properties.count > 0) {
        // push that count to the array
        counts.push(feature.properties.count);

        // retain that feature for representation
        return feature;
      }
    }

}).addTo(map);
```

Super! Now we want to make this a thematic map using a similar technique as Module 03's choropleth map. Rather than using Simple Statistics this time to calculate breaks, we'll use another awesome JS library to determine our breaks and create a color generator based on our data. First, load the [Chroma.js](https://github.com/gka/chroma.js/) into the browser.

```javascript
<script src='https://npmcdn.com/@turf/turf@3.5.1/turf.min.js'></script>
<script src="https://unpkg.com/simple-statistics@2.2.0/dist/simple-statistics.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/chroma-js/1.2.1/chroma.min.js"></script>
```

We can use the `counts` Array we've built of all the counts totals to determine the breaks, using the fancy ckmeans method (5 classes here for now).

Then we'll build a color generator function we can then use to color our hexbins.

```javascript
// use chroma.js to determine class breaks
// using ckmeans method
var breaks = chroma.limits(counts, 'k', 5);

// create color generator
var colorize = chroma.scale(chroma.brewer.OrRd).domain(breaks).mode('lab');
```

Next, let's iterate through our existing `hexLayer` (i.e., the Leaflet GeoJson we've drawn to the map as SVG) and update the fill color of each using our color generator.

```javascript
// iterate through the layers
hexLayer.eachLayer(function(layer) {

  // color each one according to count #
  layer.setStyle({
    fillColor : colorize(layer.feature.properties.count)
  });

  // bind tooltip to retrieve specific info
  layer.bindTooltip(String(layer.feature.properties.count))

});
```

Awesome! We can borrow some code from Module 03 as well to toss a legend on the map. We'll call the function to draw a legend at the bottom of our `drawMap()` function body and pass both the `breaks` and the `colorize` function as arguments.

Then, we can write a drawLegend function:

```javascript
function drawLegend(breaks, colorize) {
    // create Leaflet control for legend
    var legend = L.control({
        position: 'bottomleft'
    });

    // create a div for legend and add it to the map
    legend.onAdd = function(map) {

        return L.DomUtil.create('div', 'legend');

    };

    legend.addTo(map);

    // select the legend, add a title
    var legend = $('.legend').html("<h3>Number of Traffic Accidents in 2016</h3>");

    // loop through the Array of classification break values
    for (var i = 1; i < breaks.length; i++) {

        // get a color for the current class break
        var color = colorize(breaks[i]);

        // build legend using breaks and color values
        $('.legend').append(
            '<span style="background:' + color + '"></span> ' +
            '<label>' + (breaks[i - 1]).toLocaleString() + ' &mdash; ' +
            (breaks[i]).toLocaleString() + ' </label>');
    }

}
```

Whoomp there it is. Oh wait, probably need to add some CSS rules to the head of the document:

```css
.legend h3 {
    font-size: 1.4em;
    font-weight: bold;
    line-height: 1em;
    color: #3d3d3d;
    margin: 10px 10px 10px auto;
    text-align: left;
}

.legend span {
    width: 30px;
    height: 20px;
    float: left;
    margin: 0 10px 4px 0;
}

.legend label {
    font-size: 1.1em;
}

.legend label:after {
    content: '';
    display: block;
    clear: both;
}
```


## Serving your web map on GitHub

Web hosting is easy on GitHub. Follow these instructions: [GitHub Pages](https://pages.github.com/)
