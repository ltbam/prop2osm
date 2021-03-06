# `prop2osm` converter

CLI tool to create OSM files from a variety of proprietary street network sources.

Converting arbitrary street data into the OSM data model has the following advantages:

- FOSS routing engines work out-of-the-box with your custom street data (e.g. [Valhalla](https://github.com/valhalla/valhalla), [GraphHopper](https://github.com/graphhopper/graphhopper/), [Openrouteservice](https://github.com/GIScience/openrouteservice) and others)
- the entire OSM software ecosystem can be used for data processing (`osmium`, `osmosis`, `osm2pgsql` etc.)
- Storage-efficient protobuf (PBF) format to store the data which also allows for metadata tags

In case of interest or questions, please contact us on enquiry@gis-ops.com.

> **Disclaimer**
The converter has been designed to only work with street network data and is **not** suitable to produce OSM files for rendering or any other purpose.

## General

#### Supported providers:

- TomTom (including the MNL datasets, i.e. logistics: width/height/hazmat etc.)
- HERE

#### Supported transporation profiles

Generally the software can be used to output data suitable for **any** transportation profile. **Note** however, that most proprietary street datasets are optimized for motorized vehicles.

## Customization

The software was designed to provide least resistance to extensibility, both in terms of extending functionality for already implemented providers and/or implementing a new data provider, other than TomTom or HERE.

Please contact us over enquiry@gis-ops.com in case of questions iwth regards to customization.

## OSM tags supported

The following is a (not comprehensive) list of the general OSM tags we create/use for e.g. TomTom data:

- [name](https://wiki.openstreetmap.org/wiki/Key:name)
- [highway](https://wiki.openstreetmap.org/wiki/Key:highway)
- [oneway](https://wiki.openstreetmap.org/wiki/Key:oneway)
- [maxspeed](https://wiki.openstreetmap.org/wiki/Key:maxspeed) (including `:hgv`, `:forward`, `:backward` and others)
- Access restrictions [motor_vehicle](https://wiki.openstreetmap.org/wiki/Key:motor_vehicle), [motorcar](https://wiki.openstreetmap.org/wiki/Key:motorcar), [bus](https://wiki.openstreetmap.org/wiki/Key:bus), [psv](https://wiki.openstreetmap.org/wiki/Key:psv) etc
- All turn restrictions (except for turn restrictions > 2 way members)
- [bridge](https://wiki.openstreetmap.org/wiki/Key:bridge)
- [tunnel](https://wiki.openstreetmap.org/wiki/Key:tunnel)
- [hazmat](https://wiki.openstreetmap.org/wiki/Key:hazmat) (for truck profiles)
- [maxweight](https://wiki.openstreetmap.org/wiki/Key:maxweight) (for truck profiles)
- [maxheight](https://wiki.openstreetmap.org/wiki/Key:maxheight) (for truck profiles)
- [maxwidth](https://wiki.openstreetmap.org/wiki/Key:maxwidth) (for truck profiles)
- [incline](https://wiki.openstreetmap.org/wiki/Key:incline) (for pedestrian)

## Compatibility

The output OSM files have been validated against:

- Graphhopper
- Valhalla
- OpenRouteService
- JOSM
- QGIS
- osmosis
- osmium
