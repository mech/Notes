# MongoDB

* [MongoDB 2.6 highlights](https://bugsnag.com/blog/mongo-2-6-highlights)
* [Aggregation framework example - Tag count?](http://blog.mongolab.com/2012/07/aggregation-example/)
* [MMS blog](http://blog.mms.mongodb.com/)

If running on single server, use the `--journal` option.

If your database crashes and you were not running with `--journal`, do not use that server's data as-is! `repair` is really a last resort!

Schema-less doesn't mean skipping proper data modelling and satisfying your application business and performance requirements. NoSQL document model is more focused towards querying than to data normalization. That's why your design won't be finished unless it addresses your data querying patterns.

No JOIN because it is not horizontally scalable.

## Querying

* [Query date range](http://cookbook.mongodb.org/patterns/date_range/)
* [Aggregation to filter Trello cards](http://architects.dzone.com/articles/using-mongodb-aggregation)
* [Checkout this pipeline querying](http://vladmihalcea.com/2014/01/17/mongodb-and-the-fine-art-of-data-modelling/)

```
var pipeline = [
  {
    $match: {
      "_id": { $gte: fromDate, $lt: toDate }
    }
  },
  {
    $unwind: "$values"
  },
  {
    $project: {
      timestamp: {
        $subtract: [
          "$_id", {
            $mod: ["$_id", groupDeltaMillis]
          }
        ]
      },
      value: "$values"
    }
  },
  {
    $group: {
      "_id": { "timestamp": "$timestamp" },
      "count": { $sum: 1 },
      "avg": { $avg: "$value" }
    }
  }
];
```

## Replication

Is bad. Not worth it.

* Doesn't help write-throughput, always hits master
* Doesn't give you more working-set RAM
* Gives you more disk heads
* Gives you faster failover (the only reason to use replication)

## Indexes

* Create indexes that cover your queries only
* Do not over-use indexes
* Covered index query

## Tagging

* [Tagging with weight](http://wilker-dev.com/mongoid_taggable/)
* [Tags aren't hard](https://github.com/markbates/mongoid-tags-arent-hard)

## Shell

To find out your build:

```
> use admin
> db.runCommand("buildInfo")
> db.runCommand("compact")
> db.companies.stats()

> var j = db.users.findOne({"name": "mech"})
> j.gender = "male"
> db.users.save(j)
```

