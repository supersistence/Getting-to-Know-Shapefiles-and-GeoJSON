# Getting to Know Shapefiles and GeoJSON

2017-11-15

**Author:** Hunter Heaivilin


__*Project Description:*__ Understanding the structure of the shapefile and GeoJSON geospatial file formats. Exploring conversion methods from shapefile to GeoJSON.

Project includes
- descriptions of .shp and .geojson files
- feedback on online .shp to .geojson conversion tools





### Getting to Know Shapefiles

The shapefile (.shp) is a very common vector data file format, for use in geospatial analysis with Geographic Information Systems (GIS), developed by [Esri](http://www.esri.com/about-esri), which also created [ArcGIS](https://www.arcgis.com/features/index.html).

GIS systems commonly use both vector and raster data formats. Vector data uses points with lat/long coordinates, lines (pairs of points), and areas/polygons (groups of points) to represent discrete features and boundaries.



The [ESRI Shapefile Technical Description](https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf) offers the following key bits:

- **The shapefile (.shp) is a spatial data format that "stores nontopological geometry and attribute information for the spatial features in a data set.**
- **Shapefiles handle single features that overlap or that are noncontiguous.**
- **Shapefiles can support point, line, and area features.**


An ESRI shapefile consists of:
- A **main file** (suffix .shp) which is a direct access, variable-record-length file in which each record describes a shape with a list of its vertices.  
- An **index file** (suffix .shx.) within which each record contains the offset of the corresponding main file record from the beginning of the main file.
- A **dBASE table** (suffix .dbf.) that contains feature attributes with one record per feature. The one-to-one relationship between geometry and attributes is based on record number. Attribute records in the dBASE file must be in the same order as records in the >main file.
- **The main file, the index file, and the dBASE file have the same prefix.** For example, counties.shp, counties.shx, and counties.dbf. The prefix must start with an alphanumeric character (a–Z, 0–9), followed by zero or up to seven characters (a–Z, 0–9, _, -).
- There can also be projection files. (suffix .prj)

---

### Getting to know JSON & GeoJSON


JSON is a "lightweight, text-based,language-independent data interchange format" ([JSON spec](https://tools.ietf.org/html/rfc7159)). JSON structures data following a set formatting rules.

GeoJSON is a "geospatial data interchange format based on JSON" and it defines several types of JSON objects and the manner in which they are combined to represent data about geographic features, their properties, and their spatial extents" ([GeoJSON Spec](https://tools.ietf.org/html/rfc7946)).


- GeoJSON uses the World Geodetic System 1984 (WGS 84) geographic coordinate reference system (CRS)
- Latitute and longitude are represented in decimal degrees, as opposed to degrees &deg; , minutes, and seconds
    - Lat and long are [ordered differently](https://macwright.org/lonlat/) in different file types
    - Both GeoJSON and Shapefiles use the order: long lat
- GeoJSON has 7 different "geometry types", each represented as case-sensitive strings:
   - "Point", "MultiPoint", "LineString", "MultiLineString", "Polygon", "MultiPolygon", and "GeometryCollection".

##### More Learning
A far more informed take on GeoJSON file formats can be found [here](https://macwright.org/2015/03/23/geojson-second-bite.html).

### Attempting to Convert a Shapefile to GeoJSON
I tried a few different online tools to convert some [public data shapefiles](http://planning.hawaii.gov/gis/download-gis-data-expanded/) to GeoJSON.

#### [Mapshaper](http://mapshaper.org/)
- Mapshaper quickly uploaded my data
- Upon upload it showed the polygons of the entire dataset and could be zoomed into and around
- When I attempted to export my data as a GeoJSON file, the file downloaded as a .json file.

#### [MyGeodata Converter](https://mygeodata.cloud/converter/)
- MyGeodata Converter uploaded my data fairly quickly.
- Handily it has a viewer with a bounding box of the spatial extent the file overlaid a basemap
- Unhandily it has a paywall and would only export a sample of the file
- Importantly it did export the file as .geojson

#### [ogr2ogr web client](https://ogre.adc4gis.com/)
- Never got this to work right


---
