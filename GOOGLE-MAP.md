https://developers.google.com/maps/documentation/javascript/coordinates

the Google Maps JavaScript API uses the following coordinate systems:

Latitude and longitude values, which reference a point on the world uniquely. (Google uses the World Geodetic System WGS84 standard.)
World coordinates, which reference a point on the map uniquely.
Pixel coordinates, which reference a specific pixel on the map at a specific zoom level.
Tile coordinates, which reference a specific tile on the map at a specific zoom level.

World coordinates

Whenever the API needs to translate a location in the world to a location on a map, it first translates latitude and longitude values into a world coordinate. The API uses the Mercator projection to perform this tranlsation.
For convenience in the calculation of pixel coordinates (see below) we assume a map at zoom level 0 is a single tile of the base tile size. We then define world coordinates relative to pixel coordinates at zoom level 0, using the projection to convert latitudes and longitudes to pixel positions on this base tile. This world coordinate is a floating point value measured from the origin of the map projection to the specific location. Note that since this value is a floating point value, 
it may be much more precise than the current resolution of the map image being shown. A world coordinate is independent of the current zoom level, in other words.
World coordinates in Google Maps are measured from the Mercator projection's origin (the northwest corner of the map at 180 degrees longitude and approximately 85 degrees latitude) and increase in the x direction towards the east (right) and increase in the y direction towards the south (down). Because the basic Mercator Google Maps tile is 256 x 256 pixels, the usable world coordinate space is {0-256}, {0-256}.

