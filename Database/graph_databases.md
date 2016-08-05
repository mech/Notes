# Graph Databases

* [Analyzing the Panama Papers with Neo4j: Data Models, Queries & More](http://neo4j.com/blog/analyzing-panama-papers-neo4j/)
* [**UnitGraph**](https://github.com/keithwhor/UnitGraph)

Ironically, relational DBs can't handle relationship well.

Vertical after vertical discovers the transformative power of connected data. Without the connections/relationships, there is no point to it. When you have a lot of connected things, you have a graph-based problem.

While we could easily fit the discrete data in relational tables, the connected data was more challenging to store and tremendously slow to query.

Facebook, for example, was founded on the idea that while there's value in discrete information about people - their names, what they do, etc. - there's even more value in the relationships between them.

* Facebook - Social Graph
* Google - Web Graph

3 graph models:

1. Labeled property graph
2. Resource Description Framework (RDF) triples
3. Hypergraphs

We want to connect data as the domain dictates, allowing structure and schema to emerge in tandem with our growing understanding of the problem space, rather than being imposed upfront, when we know least about the real shape and intricacies of the data. Graphs are naturally additive, meaning we can add new kinds of relationships, new nodes, new labels, and new subgraphs to an existing structure without disturbing existing queries and application functionality.

Ironically, relational databases deal poorly with relationships. Relationships exist only at modeling time for RDBMS, as a means of joining tables.

But friendship isn't always symmetric. What if we'd like to ask "who is friends with Bob?" rather than "Who are Bob's friends?".

## Graphs vs Trees

## Analysis

* [Graph-mining system](http://www.cs.cmu.edu/~pegasus/)

