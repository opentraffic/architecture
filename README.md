***The documentation and issues in this repository describe the OTv1 platform. The basic goals remain the same for Open Traffic, although some of the specifics of the OTv2 architecture have changed. For more information, see [opentraffic/otv2-platform](https://github.com/opentraffic/otv2-platform).***

### Concept

Real-time and historical traffic speed data is a critical input for most transportation and transport analysis applications. Currently traffic speed data is absent from OpenStreetMap (OSM), undermining its value as basemap for transport applications. Commercial data sets are available for some locations, however, licensing terms and prices are prohibitive for many potential applications. And many areas of the world, particularly developing countries do not have commercial traffic data sets.

This project aims to develop a non-commercial global traffic speed data set linked to OpenStreetMap and built on open source software. Speed data are derived from GPS probe data pooled from fleet operators and app and device makers. The GPS location data is converted into OSM segment-linked speed measurements and strippped of any identifying information about the source and/or journey. The speed data is archived to support real-time and historical analysis applications.
 
As currently conceived the traffic pool will be operated by a non-profit entity with a mission to improve access to traffic data and with the responsibility for coordinating activities of pool stakeholders.  The exact structure of this entity will be determined in collaboration with stakeholders.

 
### Components

![architecture diagram](https://docs.google.com/drawings/d/1sGqv2nPg9K1uWwD846W7mb1anQO1ZyugMjpKYT_Pl-4/pub?w=878&h=706)
https://docs.google.com/a/conveyal.com/drawings/d/1sGqv2nPg9K1uWwD846W7mb1anQO1ZyugMjpKYT_Pl-4/edit

This project is designed as a data pool that connects entities and individuals with real-time location data with processing, data storage, and routing and analysis applications. A primary design goal is enabling data contributors to share derived traffic statistics without sharing underlying GPS location data or fleet information. Additionally contributors to the pool gain access to routing and analysis tools that enable them to immediately utilize derived traffic data.

The pool consists of several related components:

#### Traffic Engine
The Traffic Engine (TE) translates vehicle location to OSM-linked speed estimates. By design the TE can be run inside a fleet operator allowing internal conversion from GPS location data to to traffic statistics. This ensures that the only data to leave the data provider’s network are fully anonymized traffic statistics.

Similarly, a version of the TE SDK can be embedded into consumer applications or GPS-enabled devices allowing direct calculation and sharing of traffic statics on the device. This helps address privacy concerns for sharing location data and significantly reduces power consumption and data transfer by contributing traffic statistics.

#### Traffic Data Pool
The Traffic Data Pool is a central storage repository for speed observations. The pool is operated by a non-commercial entity ensuring security of the data and continuity of operations. 

The pool collects traffic observations from contributors and provides access to an aggregate real-time snapshot of traffic conditions, as well a historical archive of observation data in support of analytic applications.

#### OSM-linked Traffic Data Set 
The pool will create a static archival snapshot of traffic data and a real-time feed for use by third-party application developers. This will enable developers to incorporate traffic data sets into routing, mapping and analytic applications without restriction for any location where data is available. This data set will include one or more linear referencing methods to link traffic data to OSM or other non-OSM basemaps.

#### Real-time Routing API
The pool provides multiple interfaces to conditions data, including a real-time routing API available for use by pool contributors. This enables contributors to derive direct benefit from shared data by generating routing and arrival time estimates. 
 
#### OSM Trace Data + Map Dust?
In addition to storing GPS-derived traffic data there may be value in storing and analyzing trace data to improve the basemap. These traces could include existing OSM GPX trace data sets as well as new trace data collected via the Traffic Engine to the extent that data privacy considerations allow. These traces could be processed to generate OSM “map dust” (missing links, poorly documented turn/directional restrictions etc.) and incorporated into OSM data improvement workflows.


