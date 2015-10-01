# OSM Statistics

An experimental project for getting OSM statistics report based on administrative boundaries. 

Based on osmosis and osmconvert.

Osmconvert used to convert and process OSM data so that we can get OSM statistics such as the number of nodes, ways, and relations on a region.

Osmosis used to filter OSM data based on tags (key and value) in each objects such as building, road, school, etc.

This project has been successfully executed using the administrative boundaries in Indonesia. See the project in openstreetmap.id website (http://openstreetmap.id/en/data-openstreetmap-indonesia/)

## How to run it 

These steps are used for Windows version. 

1. Install osmconvert (http://wiki.openstreetmap.org/wiki/Osmconvert) and osmosis (http://wiki.openstreetmap.org/wiki/Osmosis) on your laptop. 

2. Download the latest OSM data in website geofabrik (http://download.geofabrik.de/) in .osm.pbf format. For example, we use Indonesia data (indonesia-latest.osm.pbf)

3. To get an administrative boundary as cutter, we are using overpass-turbo.eu website to filter the administrative boundaries with .osm format. For example, Aceh administrative boundary.

4. Then we have to convert the administrative boundaries with .osm format into .poly format. We can convert using JOSM but we have to install the poly plugin first. 

5. After the data was collected, make sure the poly file, the OSM data in .osm.pbf format, osmosis driver, and osmconvert driver are in the same folder.

6. Open command prompt, run this formula ```osmconvert indonesia-latest.osm.pbf -B=Aceh.poly -o=Aceh.pbf``` to convert and cut the OSM data using the poly data then generate a pbf file base on the poly file. 

7. To calculate the statistics, run this formula ```osmconvert Aceh.pbf --out-statistics``` to get all statictics data (nodes, ways, and relations) in Aceh province. 

8. Then run this formula ```osmosis --read-pbf Aceh.pbf --tf accept-ways building=* --tf reject-nodes --tf reject-relations --write-pbf Aceh_building.pbf``` to filter OSM data based on the tag (key and value) is desired. For example, this formula only filter building data. 

9. To calculate the statistics, run this formula ```osmconvert Aceh.pbf --out-statistics``` to get the building statistics data (only ways) in Aceh province.
