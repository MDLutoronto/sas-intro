---
title: New Variables
parent: Introduction to SAS
layout: default
nav_order: 5
---

## **New Variables**

To create new variables, we must first create a duplicate copy of the flights dataset (here, called “flights2”) and create new variables within the flights2 dataset. This prevents overwriting of the original data. We create a new dataset called “flights2” using **data** and then we use *set* to specify that we are using the “flights” data to create “flights2.”

You can create multiple variables at the same time. The first variable we want to create is “distancemiles” by multiplying the “distance” variable with 0.621. The second variable we want create is a variable called “instate”. It identifies flights that took place within the same state when the “originstate” and “deststate” of the flight are the same. We first create an empty “instate” variable by specifying “instate=.”, then we code instate as “1” or “0” depending on whether the “originstate” and “deststate are the same are not. We specify the condition using the *if* statement. In SAS, not equal is written as “^=”.

```

data flights2;
set flights;
distancemiles=distance*0.621;
instate=.;
if (originstate=deststate) then instate=1;
if (originstate^=deststate) then instate=0;
run;
```
To label variables, you can create a label and then apply it to the data.

Here, we create the label for “instate” by first creating an “instatelabel” with the **proc format** procedure.

```

proc format;
value instatelabel 0 = "Between State"
1 = "Within State";
run;
```
Then, we add the “instatelabel” to the “instate” variable in the “flights2” data – which contains the “instate” variable.

```

proc freq data=flights2;
format instate instatelabel.;
tables instate;
run;
```