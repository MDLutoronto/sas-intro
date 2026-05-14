---
title: Importing Data
parent: Introduction to SAS
layout: default
nav_order: 2
---

## **Importing Data**

**DATA:** [flights.csv](https://uoft.me/flightscsv)

To import a csv file into SAS, we use the procedure **proc import**. A line of code in SAS ends with a semi-colon. The same line of code can be broken up into multiple lines if the line is long. Here, we specify that the importing file is in the csv format with the *dbms* statement, and we are creating an output object called “flights” with the statement *out*. We will call the “flights” object in all the subsequent codes where we analyze this “flights” dataset.

```
proc import file = "filename"
dbms=csv 
out=flights;
run;
```