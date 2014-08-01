# Elasticsearch

* Near real-time GET request
* [Elasticsearch as a NoSQL database](https://www.found.no/foundation/elasticsearch-as-nosql/)
* [Elasticsearch in Production](https://www.found.no/foundation/elasticsearch-in-production/)
* [Document relations with Elasticsearch](http://www.youtube.com/watch?v=MXbsJsFfpV4)

## Production

* Don't use development setting
* Use uni-cast.
* Change `cluster.name`, `path.data`, `node.name`
* 

## Parent-Child Indexing

De-normalized during indexing!

* JOIN at query time - Parent/child
* JOIN at index time - Nested objects (array, inverted index)
* [Document relations with Elasticsearch](http://www.youtube.com/watch?v=MXbsJsFfpV4)

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