# Redis

* [Latency](http://redis.io/topics/latency)
* [Readthis - a new Redis gem](https://github.com/sorentwo/readthis)
* [High Performance Caching With Readthis](http://sorentwo.com/2015/07/20/high-performance-caching-with-readthis.html)
* [Optimizing Redis Usage For Caching](http://sorentwo.com/2015/07/27/optimizing-redis-usage-for-caching.html)

Clustering (Redis 3), Replication, Sentinel (monitoring)

* Powerful data types and powerful commands to leverage them. Hashes, Sorted Sets, Lists, and more.
* Persistence to disk, by default
* Transactions with optimistic locking (WATCH/MULTI/EXEC)
* Pub/Sub
* Values up to 512MB in size (Memcached limited to 1MB per key)
* Lua scripting (as of 2.6)
* Built in clustering (as of 3.0)
* Extremely fast
* Sentinel - an HA story to tell

```
redis://[password@]host[port][/db-number][?option=value]
```

```
▶ redis-cli monitor | grep -E ' "(g|s)et" '
```

## Instances

http://sorentwo.com/2015/07/27/optimizing-redis-usage-for-caching.html

Use dedicated Redis instances for distinct workloads. Do not use databases (`/0`, `/1`, `/2`) to partition workloads.

```
SIDEKIQ_REDIS_URL=redis://host1:6379/0
CACHE_REDIS_URL=redis://host2:6379/0
```

Use RDB for caching instance and AOF for background job instance.

Rather than set a expiring key which cost memory, we can just use LRU.

```
allkeys-lru
```

## Data Types

* Lists - Can be used for shared queue
* Pub/Sub - Messaging broker
* Hashes - Storing sessions
* Sorted Sets - High score tracking

## Persistence

While we tend to regard the data in caches as volatile and transient, persisting data to disk can be quite valuable in caching scenarios. Having the cache's data available for loading immediately after restart allows for much shorter cache warm-up and removes the load involved in repopulating and recalculating cache contents from the primary data store.

AOF logs every write operations.

## Config

```
save 60 1000
appendonly yes
```

## Eviction

Memcached employs a Least Recently Used (LRU) algorithm while Redis has 6 eviction policies to choose from.

## Caching

* [Layering Api Defenses With Caching](http://sorentwo.com/2015/10/19/layering-api-defenses-with-caching.html)

Avoid personalizing cached endpoints whenever possible. It is drastically slower.
