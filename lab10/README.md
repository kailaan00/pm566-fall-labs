lab10
================
Kaila An
2022-11-14

``` r
if (!require(RSQLite)) install.packages(c("RSQLite"))
```

    ## Loading required package: RSQLite

``` r
if (!require(DBI))     install.packages(c("DBI"))
```

    ## Loading required package: DBI

``` r
# install libraries
library(RSQLite)
library(DBI)
```

## Setup

``` r
# Initialize a temporary in memory database
con <- dbConnect(SQLite(), ":memory:")

# Download tables
actor <- read.csv("https://raw.githubusercontent.com/ivanceras/sakila/master/csv-sakila-db/actor.csv")
rental <- read.csv("https://raw.githubusercontent.com/ivanceras/sakila/master/csv-sakila-db/rental.csv")
customer <- read.csv("https://raw.githubusercontent.com/ivanceras/sakila/master/csv-sakila-db/customer.csv")
payment <- read.csv("https://raw.githubusercontent.com/ivanceras/sakila/master/csv-sakila-db/payment_p2007_01.csv")

# Copy data.frames to database
dbWriteTable(con, "actor", actor)
dbWriteTable(con, "rental", rental)
dbWriteTable(con, "customer", customer)
dbWriteTable(con, "payment", payment)
dbListTables(con)
```

    ## [1] "actor"    "customer" "payment"  "rental"
