# Elasticsearch

* Full-text search + Analytics + Distributed = Elasticsearch
* Near real-time GET request
* Not just good at search engine. Also a powerful analytics engine.
* Document-oriented using JSON. Nested data searchable also.
* 96 API endpoints
* 672 parameters
* [Elasticsearch as a NoSQL database](https://www.found.no/foundation/elasticsearch-as-nosql/)
* [Elasticsearch in Production](https://www.found.no/foundation/elasticsearch-in-production/)
* [Document relations with Elasticsearch](http://www.youtube.com/watch?v=MXbsJsFfpV4)
* [Using ES to help running the large Hadron Collider of CERN](https://medium.com/@ghoranyi/needle-in-a-haystack-873c97a99983)

Has Nested and Parent/Child relationships.

* index (noun) - database
* type - table
* document - row

/:index/:type/:document

```
/Users/mech/Library/LaunchAgents/homebrew.mxcl.elasticsearch.plist
/usr/local/var/log/elasticsearch/
/usr/local/var/lib/elasticsearch/plugins

/usr/local/Cellar/elasticsearch/1.3.2/config/elasticsearch.yml
/usr/local/opt/elasticsearch/config/elasticsearch.yml

/usr/local/Cellar/elasticsearch/1.3.2


$ cd /usr/local/Cellar/elasticsearch/1.3.2
$ plugin -i elasticsearch/marvel/latest
$ plugin -i polyfractal/elasticsearch-segmentspy
```

## Scoring

* Term frequency - the more often a term appears in a field, the more relevant.
* Inverted document frequency - the more often a term appears in the inverted index, the less relevant.
* Field length norm - the longer the field, the less relevant each term in it is.

Fields are "boostable" to increase relevance.

## Elasticsearch Gem

`Elasticsearch::Model.client` represents all the models.

## Production

* Don't use development setting
* Use uni-cast.
* Change `cluster.name`, `path.data`, `node.name`
* To update/upgrade Elasticsearch/Java/Kernel, always stop shard reallocation first
* 

## Parent-Child Indexing

De-normalized during indexing!

* JOIN at query time - Parent/child
* JOIN at index time - Nested objects (array, inverted index)
* [Document relations with Elasticsearch](http://www.youtube.com/watch?v=MXbsJsFfpV4)

## Query DSL

Query-string search like `_search?q=last_name:Smith` is not as powerful as Query DSL.

JSON over HTTP. Essentially a Abstract Syntax Tree for queries and filters. Can be overwhelming when you see a full page of query JSON. But if you think of it as a tree, you can deconstruct it. It has a easy grammar. Think of it as building blocks.

Query is heavy and Filter is light. Use Query for full-text search, relevance scoring and real data and use Filter for everything else.

* Core queries - match, multi_match, phrase, fuzzy, regexp, wildcard
* Compound queries - filtered, bool, function score
* Core filters - term, range, exists, geo_distance, geo_bbox, script
* Compound filters - bool, and/or/not

Below is an example of a *filtered query* that contains a query and a filter. Whew! We are looking for results that are 2014 and newer.

```
{
  "query": {
    "filtered": {
      "query": {
        "bool": {
        	  "must": {},
        	  "must_not": {}        }              },
      "filter": {
        {"range": {"created_at": {"from": "2014-01-01"}}}      }    }  }}
```

> "I want to find hotels called Renaissance for under $200, within 100m of Central so I am close to RubyConf. The hotel needs to have disability access and ideally provide WIFI and have rooms above ground level."

Under $200 and within 100m of Central are *perceived requirements* and can be flexible. WIFI is a MUST!
Why perceived, because I will be willing to pay $210 or $201 also.
	
Use the right toolset; and know your data.

```
{
  "bool": {
    "must": {},
    "must_not": {},    "should": {}  }}
```
	
```
{
  "bool": {
    "must": {
      "multi_match": { "query": "Renaissance", "fields":["name^2", "company"]},
      "term": { "features": "disability_access" }
    },    "should": {
      "term": { "features": "wifi" },
      "range": { "floor_levels": { "gt": 1 } }      
    }  }}
``````
{
  "gauss": {
    "price": {
      "origin": 0,
      "offset": 100,
      "decay": 20          }  }}```

See [gist](https://gist.github.com/mech/f4002d7031b8541e857a) for full query.

## Range Query

```
curl -XGET 'localhost:9200/products/_search' -d '{
  "query": {
    "has_child": {
      "type": "offer",
      "query": {
        "range": {
          "price": {
            "lte": 50
          }
        }
      }
    }
  }
}'
```


## Lucene

* [Visualizing Lucene's segment merges](http://blog.mikemccandless.com/2011/02/visualizing-lucenes-segment-merges.html)

## Terms

* Cluster
* Shards
* Replicas
* Gateway

## Search Ideas

* Filter by number of stars, number of forks
* Limit by owner or project

## People

* Clinton Gormley