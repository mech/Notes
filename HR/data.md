# Data

What are some of our key performance metrics?

- Number of prospective profiled.
- Timeliness of dishing out payroll.

> Product Metrics - What your customer is trying to do, and are they succeeding. Very product specific. Hard to find, easy to capture.

---

> Find structure in data

http://blog.interviewing.io/

* [How LinkedIn Recommendation System Work](https://www.quora.com/How-does-LinkedIns-recommendation-system-work)

http://www.cnet.com/how-to/reset-bypass-password-mac-macbook/

http://www.cnet.com/how-to/prevent-your-mac-password-from-being-bypassed/

> All this data can be really powerful, and because digital interfaces have made data collection so easy, we have to make sure we don’t fool ourselves into thinking the collection of good quality data and its interpretation is easier than it actually is. There is a danger that the ease in gathering data also makes it easer to make erroneous conclusions if the data quality is low or the data analysis is flawed. - [Data Aware Approach vs Data-Driven Approach](https://www.oreilly.com/ideas/embrace-a-data-aware-approach-to-designing-great-ux)

---

> It is easy to see how queries built in the query expression style can be composed - you simply add new constraints to your pipeline. 

Having metric does not mean you understand anything. Seeing metric data varying does not mean you understand any situation.

Averages (Bell Curve, Normal Distribution) mask problems. Graph the median instead, or 95th or even 99th percentile.

[Lognormal](https://www.youtube.com/watch?v=533rIdxPF10)

> NBA Final - TNT - Give them stats papers!

Can you visualize your hiring process (ATS) with Network Analysis, Clustering... Modular and Combinatorial.

* [Geckoboard](https://www.geckoboard.com/learn/kpi-examples/sales-kpis/#.Vzw6YpN94UF)

**Data tells a story**, and it's our job to look at data within a narrative structure to piece together, extrapolate, troubleshoot, and optimize that story.

Data is your business. Data-informed, not data-driven.

> Don't draw the wrong conclusion even if you have data.

How data can improve performance. What performance? Please find out from your domain.

To mine data, you need to store metrics, telemetry data. Tiny events that happen in your business processes.

Keywords: Data collection, monitoring, measurement, telemetry, data points, frequency, volumes, data-driven decision

Features:

* Drill-down
* Slices
* Aggregate
* Window function

Self-analyze and self-correct.

Currently, the KPI in Jobline are mostly about counters. Displaying the "how many" of things. Like "how many CV has been profile on this day", "how fast is the processing time", etc. We need to figure what kind of interesting behavior we want to analyze.

First, we need to know what performance problem do we see (from recruiters as well as from client). Poor engagement with client when sending resume? Slow approval from client?

Not a lot of "predictive patterns" to gain ☹️.

> Predict what's going to happen, instead of waiting for it to happen (requires lots of data!)

Too many businesses regard data analytics as pertaining mainly to realizing value from some existing data.

## Types of Values

* **Nominal** - Categorical or identity sets, distinct/disjoint. Most basic value you can have and is distinct. e.g. the value 3 is distinct from the value 5. Production is different from Staging. Cat is different from Dog, etc. hostname="vga1", etc. Mode.
* **Ordinal** - Nominal + Relative ordering. Take a normal value and give it a relative order, a ranking. 43rd > 20th, version=2.4 > version=1.5, etc. Median, Percentile.
* **Interval** - Ordinal + Equality of spacing. The value has ordinality (order) and the space between them has meaning. Something in 15 mins, 1 hours, days, etc. Mean, Standard Deviation, Multivariate Regression, linear correlation math.
* **Ratio** - Interval + Correlation factor. Often computed from interval numbers via simple math. 75% < 85%. Geometric Mean, Logarithmic, Coefficient of Variation.

Do you have a meaningful "zero" points?

Metric collected can be multi-dimensional.

> Your sampling threshold dictates what kind of lies your service tells you.

## Time Series and Autocorrelation

https://onlinecourses.science.psu.edu/stat501/node/357

## Search Filter + Review

Yelp-like

```
Focus - Narrow down
Filter - Tune out noise
Shift
```

## Aggregation? Rollups??

> And assuming you have an index on url_params you could easily do various rollups on it… Such as find the campaigns that have driven the most traffic to you over the past 30 days and which pages received the most benefit:

```sql
SELECT url_params ->> 'utm_campaign',
       page,
       count(*)
FROM visits
WHERE url_params ? 'utm_campaign'
  AND visited_at >= now() - '30 days'::interval
  AND site_id = 'foo'
GROUP BY url_params ->> 'utm_campaign',
         page
ORDER BY 3 DESC;
```

## Tags

* [Organizing Screens in Zeplin](https://medium.com/zeplin-gazette/organizing-screens-in-zeplin-with-tags-128dc3ed0749#.izjifd18v)

## Multidimensional Filtering

https://bugsnag.com/pricing

## Bots and Conversational Commerce?

* [wit.ai](https://wit.ai/)
* [2016 - Year of conversational commerce](https://medium.com/chris-messina/2016-will-be-the-year-of-conversational-commerce-1586e85e3991#.5zynhgozf)
* [Revenge of the clippy](https://medium.com/@saranormous/clippy-s-revenge-39f7387f9aab#.3duuaj5tf)
* [New in Basecamp 3: Chatbots!](https://m.signalvnoise.com/new-in-basecamp-3-chatbots-8526618c0c7d#.pjar8hdr4)
* [BC3 chatbot](https://github.com/basecamp/bc3-api/blob/master/sections/chatbots.md#chatbots)

## Data Collection - Gather the right data

> What success metric to measure?

Consciously map how you use data in each phase of the product lifecycle.

Mostly from FileMaker and into other databases. Running schedule scripts to import data at regular interval. How frequent the interval determine the final resolution.

We do have a stream of "structured data". The schema is well-known.

Looking at the right data is the only way to understand your world.

"Idle job/application" has some bad data that can make it easy to draw the wrong conclusions.

## Log Analysis

**Root-cause analysis** - Imagine candidate submit or upload Timesheet, but FM is logging different timestamp. How come we definitively know when such action occurs. What POSTed request can we inspect to pin-point "when" the action exactly take place.

`navigator.sendBeacon`

Fire off beacon to learn your user's behavior!

## Predictive Model

Predictive model abstracts away the complexity of the world, focusing in on a particular set of indicators that correlate in some way with a quantity of interest (who will churn, or who will purchase).

## Case Studies

* [Training and serving NLP models using Spark MLlib](https://www.oreilly.com/ideas/training-and-serving-nlp-models-using-spark-mllib)
* [Scaling Knowledge at Airbnb](https://medium.com/airbnb-engineering/scaling-knowledge-at-airbnb-875d73eff091#.bglfxzsj1)
* [Information Is Healthcare's Most Valuable Commodity](https://medium.com/introducing-design-to-new-places/information-is-healthcare-s-most-valuable-commodity-2b3d32aaefb3#.yck9ywtba)

## Tools

* [RMarkdown](http://rmarkdown.rstudio.com/)
* [Jupyter](http://jupyter.org/)
* [IPython Notebook](http://ipython.org/notebook.html)
* [IRuby??](https://github.com/SciRuby/iruby)

## Videos

* [Interaction designers vs algorithms](https://vimeo.com/161177402)

## Questions

* Who are the top 10 customers/clients?
* What customer postal code has the most orders?
* How do sales vary between customers with and without accounts?
* Are orders affected by holidays?
* Are they any unpopular items?
* What percentage of sales comes from xxx?
* What are the most frequent combinations of xxx?
* How do vendor requisitions vary by time and location?
* Volumes of purchases from vendors?
* Seasonal pattern?
* Backorder?
* What is our total exposure? Are our premiums high enough?
* How does this recruiter compare to the other recruiter in terms of sales rate? Processing time? Number of CV sent?
* Churn rate for our client. Which clients has the most staffs turnover rate and thus we need to be careful doing business with them.
* What is our recruiters' habits?