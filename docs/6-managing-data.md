---
title: Managing Data
parent: Introduction to SAS
layout: default
nav_order: 6
---

## **Managing Data**

### Subsetting Data

To subset data, you use **data** to create a new dataset and specify your conditions for subsetting. To subset by variables, you use *keep* to specify which variables you want in your new dataset.

```

data flights2;
set flights;
keep originstate origin depdelay deststate;
run;
```
You can check which variables are in this dataset using **proc contents**.

```

proc contents data=flights2;
run;
```
To subset by observations, you use **data** to create a new dataset and specify the criteria to keep observations. Here, we indicate that we want to keep observations if “deststate” is Hawaii AND “dayofmonth” is 1.

```

data flights2;
set flights;
if (deststate="Hawaii") and (dayofmonth=1);
run;
```

### Merging Data

To merge, you need to sort your datasets and then merge in the **data** step.

First, we import the airline codes dataset that we want to merge with the flights dataset.

**DATA:** [airlinecodes.csv](https://uoft.me/airlinescsv)

```

proc import file = "filename"
dbms=csv
out=airlinecodes;
run;
```
You can sort the data using **proc sort** and create a new object that we will use to merge. Here, the common variable between the two datasets is “carrier” so we sort *by* “carrier.

```

proc sort data=flights out=flights2;
by carrier;
run;

proc sort data=airlinecodes out=airlinecodes2;
by carrier;
run;
```
To merge “flights2” and “airlinescode2,” we use the **data** step. We will call the new merged dataset “flightsmerged”. And we use the *merge* statement to specify the two datasets to merge.

```

data flightsmerged;
merge flights2 airlinecodes2;
by carrier;
run;
```
 

### Exporting Data

To export data into a csv format, you can use **proc export**. Here, we export “flightsmerged” to the filename we want and specify it is a csv using *dbms*.

```

proc export data=flightsmerged
outfile = "filename"
dbms=csv;
run;
```