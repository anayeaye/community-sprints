## Overview

This document should link to all work happening at the sprint. Links to PR's and proposals
  
## Query
- sorting - change the name of the sort parameter to `sortby` to align with OGC specs, provide a simplified, non-JSON syntax for use by GET
  - https://github.com/radiantearth/stac-spec/pull/513
  - https://github.com/opengeospatial/ogcapi-features/issues/157
  - needs harmonization

## Item
- [Added purpose field to Asset](https://github.com/radiantearth/stac-spec/pull/637) - added field `purpose` as a corollary field to Links `rel`, to describe a common set of usages for specific assets in an item, for example `thumbnail`.  

## Extensions
- [WIP Aerial Extension](https://github.com/radiantearth/stac-spec/pull/639)
- [DateTime Range Extension](https://github.com/radiantearth/stac-spec/pull/638)

## Implementations
- pygeoapi STAC support
  - https://github.com/radiantearth/community-sprints/pull/19/files
  - discussion: https://github.com/geopython/pygeoapi/issues/221
- pygeoapi features
  - discussion around a `search/` endpoint to match the STAC `/search` across collections https://github.com/geopython/pygeoapi/issues/292
  - allowing many:many feature:collection connections: https://github.com/geopython/pygeoapi/issues/293 @mbucknell is working on an implementation for postgres
  - allowing `properties` to be added to a collection: https://github.com/geopython/pygeoapi/issues/294
  - more sophisticated postgres connections: https://github.com/geopython/pygeoapi/pull/283

* [Aligned STAC-specific endpoints more with OAF](https://github.com/radiantearth/stac-spec/pull/632) - also mentioned in a related [OAF issue](https://github.com/opengeospatial/ogcapi-features/issues/154).
* [Franklin](https://github.com/azavea/franklin) work ongoing around filling in OFeat / STAC endpoints and an importer. Endpoint progress is visible in the README, open work is visible in the [PRs](https://github.com/azavea/franklin/pulls)
* [Converted search metadata to context object](https://github.com/radiantearth/stac-spec/pull/633) - consolidated search metadata into a context object that the root level of the FeatureCollection. Slimmed down property names.
* Completed some initial work on Python client for Maxar STAC catalog API
* Begun creating a SpaceNet 2 static STAC catalog with label extension integrated
- Validation Group
  - Created validation Circle CI script (pending PR) 
  - PySTAC implementation to identify object type, verion and extensions from JSON, to be used in CircleCI script (pending PR)
  - Stac-Validator will import and use PySTAC to identify object type, version, and extensions and will use this information to infer paths to schemas on [cdn.staclint.com](cdn.staclint.com). CDN contains schemas for all versions, extensions.
  - Extension schema filenames will be adjusted to consistently infer path to schema during validation `extensions/extension-name/json-schema/extension-name.json`, for example `extensions/eo/json-schema/eo.json`. [Issue 624](https://github.com/radiantearth/stac-spec/issues/624)
  - STAC version and extensions defined on item_collection in support of PySTAC implementation. [PR 640](https://github.com/radiantearth/stac-spec/pull/640)
  - Stac-validator will have an exit on failure mode for CICD implementations.
* KoopJS [provider](https://github.com/koopjs/provider-ogcapi-features) and [output](https://github.com/koopjs/output-ogcapi-features) work ongoing around finishing up the data APIs in the core spec.

  

## Filter (Common Query Language)

* [Cleaned up BNF from OGC Catalgue](https://github.com/opengeospatial/ogcapi-features/blob/master/extensions/cql/schema/cql.bnf)
* [Developed equivalent JSON encoding](https://github.com/opengeospatial/ogcapi-features/blob/master/extensions/cql/schema/cql.json)
* [Developed and alternate equivalent JSON encoding of CQL](https://github.com/tschaub/ogcapi-features/blob/json-array-expression/extensions/cql/jfe/readme.md)
* Examples of each can be found [here](https://github.com/opengeospatial/ogcapi-features/tree/master/extensions/cql/examples) and [here](https://github.com/tschaub/ogcapi-features/blob/json-array-expression/extensions/cql/jfe/examples.md)
* [JSON Filter Expression](https://github.com/opengeospatial/ogcapi-features/pull/283) - Work in progress proposal to use JSON arrays as filter expressions.
* A filter capabilties document was also developed [here](https://github.com/opengeospatial/ogcapi-features/blob/master/extensions/cql/schema/filter-capabilities.json) with an example [here](https://github.com/opengeospatial/ogcapi-features/blob/master/extensions/cql/examples/filter-capabilities-example-full.json)
* Full text search: https://github.com/opengeospatial/ogcapi-features/pull/284
* Trivial point, there is an OGC document number of the CQL extension document: OGC 19-079.

### Transactions

* A detailed outline of the OGC transactions, based on OGC work, was posted [here](https://github.com/opengeospatial/ogcapi-features/blob/master/extensions/transactions/TX_Notes.adoc)

### Collections Summary

* [Collection Summary](https://github.com/opengeospatial/ogcapi-features/pull/287) - Draft proposal to add a collection summary to the Features spec.


* [PySTAC tutorial](https://github.com/azavea/pystac/pull/48) - Fixed the PySTAC SpaceNet tutorial to point to the right places in the re-organized SpaceNet S3 bucket.

### OGC CAT 4.0

* OGC stuff: the charter for the standards working group (SWG) was approved and so work on CAT 4.0 (OGC API - Cataglogue/Records - Part 1: Core) will begin shortly
* There is already an OpenAPI document describing an initial API and examples [here](https://github.com/opengeospatial/CAT4.0/tree/master/core/code).
* There is an initial VERY, VERY, VERY rough implementation developed during the SPRINT [here](http://www.pvretano.com/cubewerx/cubeserv/default/wrs/4.0?f=xml).
** NOTE: pvretano.com is my development machine so it is Heisenberg-stable!
* The CAT 4.0 group met during the sprint to discuss CAT 4.0/STAC relationship.  STAC catalogues the spatial temporal assets.  OGC CAT 4.0 catalogues collections of assets and every else that STAC does not care about (e.g. code lists, coordinate reference system definitions, etc).
* First meeting of the SWG will be announced soon.
