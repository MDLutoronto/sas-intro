---
title: Importing Data
parent: Introduction to SAS
layout: default
created_date: 2021-09-13
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
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

**Technique:** [Data Visualization](https://mdlutoronto.github.io/tutorials-search/?technique=Data+Visualization), [Searching for maps and data](https://mdlutoronto.github.io/tutorials-search/?technique=Searching+for+maps+and+data) \| **Tools:** [SimplyAnalytics](https://mdlutoronto.github.io/tutorials-search/?tool=SimplyAnalytics) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics), [Vector](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Vector)