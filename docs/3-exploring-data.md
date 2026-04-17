---
title: Exploring Data
parent: Introduction to SAS
layout: default
nav_order: 3
---

## **Exploring Data**

You can create frequency tables and crosstabs using **proc freq** with the statement *tables*. You can specify multiple variables at once to create multiple tables.

Here, we create two separate frequency tables for the “depdelay” and “arrdelay” variables.

```
proc freq data=flights;
tables depdelay arrdelay;
run;
```
If you want to crosstabulate “depdelay” and “arrdelay,” you simply put an asterisk (*) between the two variables.

```
proc freq data=flights;
tables depdelay*arrdelay;
run;
```
If you only want to see percentages in our crosstabulation table, you can add additional options after the forward slash (/).

```
proc freq data=flights;
tables depdelay*arrdelay / norow nocol nofreq;
run;
```
To produce summary statistics such as mean and standard deviation, we use the procedure **proc means** and the *var* statement specifies the variable of interest.

```
proc means data=flights;
var distance;
run;
```
You can get summary statistics by groups in a categorical variable by adding the *class* statement. Here, we get summary statistics for flight distance by the days of the week.

```

proc means data=flights;
class dayofweek;
var distance;
run;
```
If you need detailed summary statistics such as percentiles, median, or mode, you can utilize **proc univariate**.

```

proc univariate data=flights;
var distance;
run;

proc univariate data=flights;
class dayofweek;
var distance;
run;

```