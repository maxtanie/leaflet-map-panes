# leaflet-map-panes
Leaflet JS custom map panes, with CT town labels displayed on top of thematic polygon map

## Demo (designed for zoom levels 10-13)
http://jackdougherty.github.io/leaflet-map-panes/

## Requires
- Leaflet 1.x
- ArcGIS Online account (subscription)

## Create your own

#### Upload simplified polygon map into ArcGIS, remove boundaries, display labels
- Upload polygon map into http://mapshaper.org and create highly simplified view (down to 1 percent) to smooth lines. Export as shapefile. *This is my attempt to reduce extra labels from appearing in selected towns with non-rectangular geography, but am unsure if it helps.*
- Upload shapefile to ArcGIS (I used version 10.2)
- make polygon fill hollow, set lines to 0 width
- label features (town names) with these settings
  - Arial 9 point font (1 pt above default)
  - Placement properties > Place one label per feature *But this does not seem to do what it claims*
  - Conflict detection > default (label weight: high, feature weight: none; buffer: 0)

#### Upload, publish, and share as a tile layer on ArcGIS Online (subscription)
- Based on documentation: Publish Tiles on ArcGIS Online https://doc.arcgis.com/en/arcgis-online/share-maps/publish-tiles.htm#GUID-C467C9D7-443D-48D6-90AB-8204E3B9FD83
- Trinity College subscription site http://trincoll.maps.arcgis.com/home/organization.html
- Upload to ArcGIS Online
- file > log into ArcGIS online subscription account (in my case, http://trincoll.maps.arcgis.com)
- customize > arcmap options > sharing and select Enable ArcGIS Runtime tools (one time only)
- file > share as > tile package, with these settings:
  - tile package > upload to my account (insert file name)
  - tile format: ArcGIS Online/Bing/Google, PNG, up to zoom level 13 or 14 (varies)
  - item description and tags (required)
  - sharing: everyone
- In web browser, go to My Content for your ArcGIS Online site (mine is http://trincoll.maps.arcgis.com/home/content.html)
- click to open the Tile Package that has been uploaded, which opens browser settings
- select Publish (ArcGIS Online will start "Publishing Tiles. . .")
- select Share > Everyone
- after several minutes, ArcGIS Online will create tiles with a URL similar this:
- http://tiles.arcgis.com/tiles/5rblLCKLgS4Td60j/arcgis/rest/services/ConnecticutTownLabelsOnly/MapServer
- Optional: in My Content browser window, keep new "Tile Layer," but able to erase "Tile Package" to reduce storage charges for ArcGis Online

#### In Leaflet map, use esri-leaflet code to display town labels as tile layer http://esri.github.io/esri-leaflet/

#### See Leaflet custom map panes tutorial to display tile layer at different z-levels above polygon http://leafletjs.com/examples/map-panes.html

## Questions for MAGIC
- Can your team create a better ArcGIS tile layer of town names? In my version, some towns display multiple labels (see Torrington and Winchester)
- If yes, can MAGIC host this label-only tile layer on your server? I’m thinking it would be a better long-term public solution than Trinity’s ArcGIS Online account.

## Alternatives considered
- Also tried free CartoDB light labels only layer, but insufficient detail
- Also tried creating labels-only tile layer in Mapbox Studio Classic, and MapBox Studio, but appears to require a subscription beyond free level; this testing example comes from http://googlemapsmania.blogspot.com/2016/02/switching-map-labels-in-leaflet.html

## To Do
- Rebuild geojson data file for pop density
- change from click to hover, and add legend to display colors and hover data
- other minor changes
