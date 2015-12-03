# Linked Data

* [Intro to Linked Data](https://voicethread.com/myvoice/#thread/5669601/28932684/31215885)
* [Fostering intelligence by enabling it](http://ruben.verborgh.org/blog/2015/02/25/fostering-intelligence-by-enabling-it/)
* [JSON-LD and why I hate the Semantic Web](http://manu.sporny.org/2014/json-ld-origins-2/)

The world is a graph databases.

Part of the problem is information is hard to ingest. If you're not expecting it, you won't necessarily know where to put it. Databases expect schema and relationship they you know about.

It is better to shift your thinking and assume you're not going to know about everything and have proper schema all the way.

Different "terms" mean different to different people, concept, environment, context, etc.

A graph is an eminently learnable and extensible data structure. If you learn some fact, you just hang it off a node.

```
# N-Trible Serialization of the Facts
<https://w3id.org/people/mech>
  <http://xmlns.com/foaf/0.1/birthday> "06-12" .
<https://w3id.org/people/mech>
  <http://xmlns.com/foaf/0.1/name> "mech" .
<https://w3id.org/people/mech>
  <http://www.w3.org/1999/02/22-rdf-syntax-ns#type>
  <http://xmlns.com/foaf/0.1/Person> .
```

Data want to live where data want to be. Some data want to live inside FileMaker, some want to live inside spreadsheet, some want to be inside PDF, some want to be in proper RDBMS. What happen if we don't care about data storage and still be able to linked data together?

## Re-shape the data for query

## People

* [Ruben Verborgh](http://ruben.verborgh.org/)