This project is a custom fork of the MongoDB river plugin for ElasticSearch

The goal is to improve the realibility and managability of the mongodb river plugin

Changelog
-------

#### 2.0.4
- Update versions ES 1.4.0
- Bug fix for initial import of sharded collections

#### 2.0.2
- Update versions ES 1.3.5, MongoDB 2.6.5, MongoDB driver 2.12.4, Java 7
- Improved scaling for running multiple rivers and numerous bug fixes by @ankon of Collaborne B.V.
- Improved TokuMX support by @kdkeck of Connectifier, Inc.
- Support for collection names with period by @qraynaud

#### 2.0.1
- Update versions ES 1.2.2, MongoDB 2.6.3, MongoDB driver 2.12.3
- Support for TokuMX by @kdkeck of Connectifier, Inc.

#### 2.0.0
- Update versions ES 1.0.0, MongoDB 2.4.9, MongoDB driver 2.11.4
- Detection of stale river

#### 1.7.4
- Make include_fields work for nested fields
- Fix ensuring river status indicates failures

#### 1.7.3
- Update versions ES 0.90.7
- Optimization of oplog.rs query. The current query was too complex and not efficient in MongoDB. oplog.rs query now uses only $ts filter.
- New ```options/import_all_collections``` parameter can be used to import all collection of a database (see issue [#177](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/177))
- Version, commit data and commit id are displayed in the log when the river starts.
- New ```options/store_statistics``` parameter can be used to store statistic each time bulk processor is flushed. Data are store in _river/{river.name}
- Default value for ```index/bulk/concurrent_bulk_requests``` has been changed to the number of cores available.
- Capture failures from bulk processor and set status to IMPORT_FAILED when found.
- Fix issues in document indexed counter in administration.
- Refactoring to use 1 bulk processor per index/type.

#### 1.7.2
- Update versions MongoDB 2.4.8
- Optimization of oplog.rs filter (see issue [#123](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/123))
- ```options/drop_collection``` will also track ```dropDatabase``` (see issue [#133](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/133))
- Add filter in the initial import by @bernd (see issue [#157](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/157))
- MongoDB default port is 27017 (if not specific in configuration) (see issue [#159](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/159))
- Allow alias in place of index (see issue [#163](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/163))
- Initial import supports existing index (see issue [#167](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/167))
- New parameter ```options/skip_initial_import``` to skip initial import using collection data. Default value is false.
- Stop properly the river when deleted (see issue [#169](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/169))
- Administration updates: stopped river can be deleted from the administration, auto-refresh.
- Switch to BulkProcessor API to provide more flexible configuration during bulk indexing. (see [commit](https://github.com/richardwilly98/elasticsearch-river-mongodb/commit/973dba973f6c1c353a38ed060754967504485769))

#### 1.7.1
- Update versions ES 0.90.5, MongoDB driver 2.11.3
- Initial import using the collection by @benmccann. (see issue [#47](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/47))
- Add unit test to validate Chinese support (see issue [#95](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/95))
- Ensure MongoDB cursor is closed (see issue [#comment-24427369](https://github.com/richardwilly98/elasticsearch-river-mongodb/pull/106#issuecomment-24427369))
- River administration has been improved. (see issue [#109](https://github.com/richardwilly98/elasticsearch-river-mongodb/pull/109))
- Allow fields ```ts``` or ```op``` to be used in user collection. (see pr [#136](https://github.com/richardwilly98/elasticsearch-river-mongodb/pull/136))
- Use of OPLOG_REPLAY to query oplog.rs

#### 1.7.0
- Update versions ES 0.90.3, MongoDB 2.4.6
- Ability to index documents from a given datetime (see issue [#102](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/102))
- Fix for ```options/exclude_fields``` by @ozanozen (see issue [#103](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/103))
- Fix for ```options/drop_collection``` (see issue [#105](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/105))
- New advanced transformation feature.  (see issue [#106](https://github.com/richardwilly98/elasticsearch-river-mongodb/pull/106))
- Add site to the river. Initial implementation (only start / stop river or display river settings).  (see issue [#109](https://github.com/richardwilly98/elasticsearch-river-mongodb/pull/109))
- Implement include fields (see issue [#119](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/119))
- Refactoring of the river definition (new class MongoDBRiverDefinition).

#### 1.6.11
- Add SSL support by @alistair (see [#94](https://github.com/richardwilly98/elasticsearch-river-mongodb/pull/94))
- Add support for $set operation (see issue [#91](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/91))
- Add Groovy unit test (for feature [#87](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/87))
- Update versions ES 0.90.2, MongoDB 2.4.5 and MongoDB driver 2.11.2
- Fix for ```options/drop_collection``` option (issue [#79](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/79))
- New ```options/include_collection``` parameter to include the collection name in the document indexed. (see [#101](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/101))

#### 1.6.9
- Allow the script filters to modify the document id (see [#83](https://github.com/richardwilly98/elasticsearch-river-mongodb/pull/83))
- Support for Elasticsearch 0.90.1 and MongoDB 2.4.4
- Improve exclude fields (support multi-level - see [#76](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/76))
- Fix to support ObjectId (see issue [#85](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/85))
- Add logger object to script filters
- Provide example for Groovy script (see issue[#87](https://github.com/richardwilly98/elasticsearch-river-mongodb/issues/87))

#### 1.6.8 
- Implement exclude fields (see issue #76)
- Improve reconnection to MongoDB when connection is lost (see issue #77)
- Implement drop collection feature (see issue #79). The river will drop all documents from the index type.

#### 1.6.7 
- Issue with sharded collection (see issue #46)

#### 1.6.6 
- Support for Elasticsearch 0.90.0 and MongoDB 2.4.3
- MongoDB driver 2.11.1 (use of MongoClient)  

