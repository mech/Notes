# Search

> If a user is reading a recipe, where might they want to go next? We should anticipate how they might want to explore based on the recipe they are reading, and not leave it up to them to peck through a hierarchical menu or come up with a search term. And we certainly should not leave them with a few “related recipes” and consider our work done. They might want to see all the recipes that the chef has posted. Or maybe they want to see more recipes that use swiss chard, pivoting by ingredient?

> Just a recipe recommendation is not enough. Have a link to all the recipe keywords.

> If we are thinking object-orientedly, we will experiment with ways that each object might relate to other objects, looking beyond the obvious. Maybe chefs have favorite ingredients? In the object-oriented design below, a user can continually explore instances of these three objects (recipe, chef, ingredient) without ever hitting a dead end. The content is the navigation, and it’s all in context.

* [Twigkit](http://twigkit.com/)
* [Designing the search experience](http://designingthesearchexperience.com/)
* [Next-level searching in Slack](https://slackhq.com/next-level-searching-in-slack-1ce56aa8adee#.75osmjbxt)

## Query Questions

* Aggregate over certain metric. SUM, AVG
* Revenue over a quarter broken down by demographic
* Top publishers by clicks over the last month
* Number of CA visitor broken down by any dimension
* Viewing habits

We are looking at some filter of the total data set.

Pre-compute query result. May be costly!

## Aggregated Fields

* [How to leverage Aggregated fields to solve common search requirements with Search API](https://www.codeenigma.com/build/blog/drupal-and-search-api-unleash-power-aggregated-fields)

# Design

Search is a journey. Search is an exploration. The journey itself may be more important than the destination. Either you are exploring or you know precisely and exactly what you want to find.

> It should be less about searching and more about finding.

Information seeking behavior, information foraging and sense-making.

The "Dimensions" of search experience:

* Who is doing the search? The User.
* What they are trying to achieve? The Goal. Precise or uncertain.
* Under what circumstances? The Context.
* How they are going about it? The Search Mode.

Are we querying body of text or metadata?

```
"perfect pitch" -baseball +music
```

The search box is also a CLI. You can issue commands to it.

Search is the world's most popular teacher. As designers, we must expand our vision beyond finding to incorporate learning.

We simply fail to search. We live uninformed without seeing what we miss, for the cost of the unsearched is an unseen drag on commerce and culture, as invisible as it is incalculable.

Far from being static, search is an interactive, iterative process in which the answer can change the question.

> What we find changes what we seek

Search is not a quest for the perfect document but a conversation that helps us understand the right questions to ask.
