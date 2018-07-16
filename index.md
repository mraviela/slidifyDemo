---
title       : OnLine Life Insurance quotes
subtitle    : Final project for course Developing Data Products
author      : Miguel Raviela
job         : Data Scientist in training
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
github:
  user: mraviela
  repo: slidifyDemo
---


## The case

Some years ago I was working for an insurance company, creating new web systems to offer our
clients the option to obtain quotations over internet, the company as many others did have several
backend systems for the different kind of insurance products as automoviles, house and life.  

Some of those where well documented and created in modern languajes as java, with source code available
to review and create the needed integrations, but the system for life policies was and old COBOL development
very hard to integrate and to make it really worst case scenario, without documentation and source code,
at that time was impossible to create an interactive web application for this kind of insurance policies.

Now I challenge my self to create the solution for it, using Data Science tools.

--- .class #id 

## The data

Now a days I no longer work this company, so I find some turn arouds in order to recreate the case.

 1. I recreate the data set, by extracting manually quotations online.  
 2. For the original case the approach is to extract it from database.  
 3. The recreated data set is 52 observations with 3 variables, enought to recreate the case.  


## The model

With the dataset recreated, I tranined a model, the best option was GML, family GAMMA with log link. The feature creation was the real challenge.

```
model <- glm(premium ~ age + coverage + I(age * log(coverage)) + I(age^2 * coverage), 
data=insurance.data, family = Gamma(link="log"))

```  

---

## The app

The app creation was really simple using Shiny package, from those old days I recovered some part of the business rules
insurance products creators use.

 1. The base for life insurance is Age.
 2. Calculation age is obtained by penalizing if the client is a smoker and male.
 3. Coverage known as insurance amount is also in the formula to get the final calculation. 

The app is available at https://mraviela.shinyapps.io/life_insurance/

---
## Motion Chart

AS required next is an interactive graphic to play with the dataset recreated.

<!-- MotionChart generated in R 3.5.0 by googleVis 0.6.2 package -->
<!-- Sun Jul 15 20:35:50 2018 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataMotionChartID177c5272f55fa () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
"18",
128,
50000
],
[
"18",
227,
250000
],
[
"18",
437,
5e+05
],
[
"18",
480,
1e+06
],
[
"20",
184,
1e+05
],
[
"20",
254,
250000
],
[
"20",
444,
5e+05
],
[
"20",
490,
1e+06
],
[
"25",
188,
1e+05
],
[
"25",
256,
250000
],
[
"25",
450,
5e+05
],
[
"25",
510,
1e+06
],
[
"30",
196,
1e+05
],
[
"30",
266,
250000
],
[
"30",
474,
5e+05
],
[
"30",
540,
1e+06
],
[
"35",
210,
1e+05
],
[
"35",
291,
250000
],
[
"35",
499,
5e+05
],
[
"35",
630,
1e+06
],
[
"40",
237,
1e+05
],
[
"40",
380,
250000
],
[
"40",
687,
750000
],
[
"40",
890,
1e+06
],
[
"45",
303,
1e+05
],
[
"45",
596,
250000
],
[
"45",
1025,
750000
],
[
"45",
1340,
1e+06
],
[
"50",
427,
1e+05
],
[
"50",
891,
250000
],
[
"50",
1782,
750000
],
[
"50",
2350,
1e+06
],
[
"55",
659,
1e+05
],
[
"55",
1459,
250000
],
[
"55",
3185,
750000
],
[
"55",
4220,
1e+06
],
[
"60",
1088,
1e+05
],
[
"60",
2361,
250000
],
[
"60",
5892,
750000
],
[
"60",
7830,
1e+06
],
[
"65",
1958,
1e+05
],
[
"65",
4496,
250000
],
[
"65",
13146,
750000
],
[
"65",
16634,
1e+06
],
[
"70",
3660,
1e+05
],
[
"70",
7656,
250000
],
[
"70",
22505,
750000
],
[
"70",
29943,
1e+06
],
[
"75",
4974,
1e+05
],
[
"75",
12238,
250000
],
[
"75",
29712,
750000
],
[
"75",
38673,
1e+06
] 
];
data.addColumn('string','age');
data.addColumn('number','premium');
data.addColumn('number','coverage');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartMotionChartID177c5272f55fa() {
var data = gvisDataMotionChartID177c5272f55fa();
var options = {};
options["width"] = 600;
options["height"] = 400;
options["state"] = "";

    var chart = new google.visualization.MotionChart(
    document.getElementById('MotionChartID177c5272f55fa')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "motionchart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartMotionChartID177c5272f55fa);
})();
function displayChartMotionChartID177c5272f55fa() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartMotionChartID177c5272f55fa"></script>
 
<!-- divChart -->
  
<div id="MotionChartID177c5272f55fa" 
  style="width: 600; height: 400;">
</div>







