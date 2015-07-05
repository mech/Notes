# R

Use R as your calculator and spreadsheet. Anything you can do it in spreadsheet, you can do it more efficiently with R.

`Ctrl-L` to clear the console.
`Ctrl-1` to the editor.

* [Fun statistics with R, Twitter and MongoDB](https://www.mongosoup.de/blog-entry/Fun-Statistics-With-R-Twitter-And-MongoDB.html)
* [R-Bloggers](http://www.r-bloggers.com/)
* [Quick-R](http://www.statmethods.net/)
* [Public heath with R](https://www.youtube.com/watch?v=m3vJJHyL2Os)
* [NYT](https://github.com/TheUpshot/leo-senate-model)
* [Wes Anderson color palette for R](https://github.com/karthik/wesanderson)

```
// If you encounter LC_CTYPE error
defaults write org.R-project.R force.LANG en_US.UTF-8
```

```
install.packages("lattice")
install.packages(c("lattice", "ggplot2"))
```

## Environment

`search()` the global environment.

Exploring a function closure: `ls(environment(<function_name>))`

## Objects

R objects can have attributes, like `names`, `dimnames`, `length`. Attributes of an object can be accessed using the `attributes()` function.

## Variable

```
// x get 2
x <- 2 // Stored as a 1-size vector even if it is scalar
x = 2
class(x)
is.numeric(x)
is.integer(x)
class(TRUE)

NA - Missing data is important in statistic
NULL - Absence of anything

is.na(x)
is.null(x)
```

## Vectors

Array-like. Container to store same type. Only `list` can contain objects of different classes. Empty vectors can be created with the `vector()` function.

```
x <- c(1, 2, 3, 4) # c() is concatenate
x <- 1:10 ## Sequence
x <- 5:-7
length(x)
c(One="a", Two="y", Last="r")
names(x) <- c("a", "b", "c", "d")
x[c(2,4)] <- NA
x <- vector("numeric", length=10)
x <- c(1.7, "a") ## coerce to character
```

```
// Removing NA value

x <- c(1, 2, NA, 4, NA, 5)
bad <- is.na(x) ## logical vector
x[!bad]
```

## Lists

Lists are a special type of vector that can contain elements of different classes.

```
x <- list(1, "a", TRUE, 1 + 4i)
```

## Factors

Factors are used to represent categorical data. Factors can be unordered or ordered. (Male, Female)

```
x <- factor(c("yes", "yes", "no", "yes", "no"), levels=c("yes", "no"))
table(x)
unclass(x)
attr(,"levels")
```

## Loop

```
for (i in seq_along(x)) {}

for (letter in x) {}

for (i in seq_len(nrow(x))) {}
```

## Reading

```
income <- read.csv("income.csv")
con <- url("http://www.", "r")
x <- readLines(con)

data <- read.table("foo.txt")"
```

## Subsetting (Matrix/List)

Extract subsets of R objects.

```
x <- c("a", "b", "c", "c", "d", "a")
x[1]       ## Numeric index
x[1:4]
x[x > "a"] ## Logical index
u <- x > "a"
x[u]
```

## Data Frame

Rectangular data structure, resemble spreadsheet. Spreadsheet-like mixed type structure.

* Factor - category or group
* Factor vector

```
q <- c("Hockey", "Basketball")
df <- data.frame(Firs=x, Second=y, Sport=q)
class(df$Sport) // "factor" unless stringsAsFactors=FALSE
nrow(df)  // row
NROW(df)  // Safety function, not use for data frame
ncol(df)  // column
dim(df)   // both row and column
names(df)
rownames(df)
head(df)
head(df, n=7)
tail(df)
class(df)
df$Sport // Grab a column
df[3, 2] // Third row, second column
df[3, 2:3]
df[c(3, 5), 2] // Build a vector to grab third and fifth row
df[, 3]  // no row selection
df[, 3, drop=FALSE] // force a data frame instead of a vector, show one column
df[2:4,] // Select 2 to 4 row with all columns
df[, c("Sport", "First")] // all row with selected columns
df["Sport"]   // return a data frame that just show a column
df[["Sport"]] // return a vector instead!
df[c("First, Sport")] // return a data frame with 2 columns
```

## Ragged Array

```
weight~group

// Higher-level graphic function
plot(weight[Diet==2]~Time[Diet==2],
  data=ChickWeight,
  main="Diet #1",
  xlab="Time",
  ylab="Weight")
```

## Function

Put your functions into a separate file or package.

```
f <- function(x, y, type = "1", ...) {
  formals
}

// named argument
sd(x = mydata, na.rm = FALSE)

above10 <- function(x) {
  use <- x > 10
  x[use]
}

above <- function(x, n = 10) {
  use <- x > n
  x[use]
}
```

### Generic Functions



## ggplot2

```
library(ggplot2) # No quote
search()
qplot(weight, facets=.~group, geom="density")
```

## Model Expression

## Graphics Device

```
?par
par(mfcol=c(2,2))
```

## Graphical Summary

## Null Hypothesis

## Data Sets

* [figshare](http://figshare.com/)

## Help

```
??csv
?head
help.search("rnorm")
args("rnorm") # Get arguments
rnorm # Print the source
```