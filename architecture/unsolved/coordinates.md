# Coordinates

Which coordinate system should be used, or should the Consumer decide?

Calculating one coordinate system to another is not a difficult task anymore, although it can be resource intensive.
If C-API should define one, which?

Currently, in use in the Netherlands:

- Rijksdriehoekcoördinaten, EPSG:28992
- WGS84, EPSG:4326
- ETRS89, EPSG:4258

RD is mostly limited to in-land in the Netherlands. It can not reach the total marine range of the Netherlands.
INSPIRE defines ETRS89 as preferred coordinate system.

For the time being (and since there is little difference between ETRS89 and WGS84), no coordinate system will be specified and all coordinates are considered to be WGS84.

