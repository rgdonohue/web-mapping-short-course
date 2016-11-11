# Lesson 02. Thematic Web Mapping: Choropleth Mapping

This lesson guides you through a process of creating a choropleth map. Choropleth maps are another common type of thematic map that use enumeration units such as states or counties to show how much of a particular phenomenon each contains by proportional shading. These are among the most familiar of thematic map types to the general public, especially for making election maps.

Choropleth maps are best used to map continuous areal (or area-based) phenomena and represent a statistical surface for enumeration units (i.e., polygons). The map symbology applies a sequence of shaded values (often using color schemes) to symbolize the density or ratio for each enumeration unit on the map. The intensity of the color indicates how much of some phenomenon is within a given area (greater intensity or darker color generally means more of something).

To make a choropleth map, we need to establish two more pieces of information. First, we need to know the entire range of the particular data value we're encoding. Second, we need to determine the precise values with which we will classify that data range into discrete chunks. We could do some of this analysis prior to creating our GeoJSON file, either through analyzing the data tables within a conventional spreadsheet application such as OpenOffice Calc or Microsoft Excel. We could also run scripts written in JavaScript, Ruby, Python, or R to process our data and create attribute values that are normalized. However, for this module, we are going to do this analysis and determine the class breaks client-side at runtime using JavaScript.

## Step 01: get the data

Note that within the *module-03/app/data/* directory there is a CSV file named *2016CountyHealthRankings.csv*. This data was downloaded from [County Health Rankings & Roadmaps](http://www.countyhealthrankings.org/rankings/data) and edited to preserve some of the data attribute columns already normalized as a rate or percentage. Within the data we see there are US county FIPS codes, but there is no geometry data included.

To get good polygons useful for mapping, go to[Cartographic Boundary Shapefiles - Counties] (https://www.census.gov/geo/maps-data/data/cbf/cbf_counties.html) and download the [cb_2015_us_county_20m.zip](cb_2015_us_county_20m.zip) Shapefile. Open these Shapefiles and explore on your machine.

Next, drag or upload the entire zipped shapefile package into the web interface of [MapShaper](http://mapshaper.org/). You can explore various options for simplifying the data and editing the data tables within this tool. For now, simply download your file as a GeoJSON file and save within your *data/* directory. Save it as *counties.json*.

## Step 02: load the data

We can again use JQuery's getJSON method to load the data asynchronously. Load the data and verify that is correct.

```JavaScript
$.getJSON('data/counties.json', function(counties) {
    console.log(counties)
}
```

To be finished ....
