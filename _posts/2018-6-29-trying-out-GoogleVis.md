## Major Sports League Season Timeline


```r
#==============================================================================

library(readxl)
suppressPackageStartupMessages(library(googleVis))

#==============================================================================

sport <- read_excel("C:/Users/Maluwa/Google Drive/Maluwalmk/sports.xlsx")


sport <- sport[order(sport$start), ]

s.timeline <- gvisTimeline(data = sport, 
                           rowlabel = "league",
                           start = "start",
                           end = "end",
                           options= list(timeline = "{groupByRowLabel:false}",
                                        backgroundColor = '#f2f2f2', 
                                        height = 350,
                                        width = "automatic")
                           )
print(s.timeline, tag = "chart")
```

<!-- Timeline generated in R 3.2.3 by googleVis 0.5.10 package -->
<!-- Thu Jan 28 23:05:49 2016 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataTimelineID17841801136 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "MLB",
new Date(2015,3,13,0,0,0),
new Date(2015,9,4,0,0,0) 
],
[
 "EPL",
new Date(2015,7,8,0,0,0),
new Date(2016,4,15,0,0,0) 
],
[
 "NFL",
new Date(2015,8,10,0,0,0),
new Date(2016,0,3,0,0,0) 
],
[
 "NHL",
new Date(2015,9,7,0,0,0),
new Date(2016,3,9,0,0,0) 
],
[
 "NBA",
new Date(2015,9,27,0,0,0),
new Date(2016,3,13,0,0,0) 
],
[
 "NCAA",
new Date(2015,10,13,0,0,0),
new Date(2016,3,4,0,0,0) 
] 
];
data.addColumn('string','league');
data.addColumn('datetime','start');
data.addColumn('datetime','date');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartTimelineID17841801136() {
var data = gvisDataTimelineID17841801136();
var options = {};
options["height"] =    350;
options["timeline"] = {groupByRowLabel:false};
options["backgroundColor"] = "#f2f2f2";

    var chart = new google.visualization.Timeline(
    document.getElementById('TimelineID17841801136')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "timeline";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartTimelineID17841801136);
})();
function displayChartTimelineID17841801136() {
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
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTimelineID17841801136"></script>
 
<!-- divChart -->
  
<div id="TimelineID17841801136" 
  style="width: automatic; height: 350;">
</div>

```r
cat("http://maluwalmk.com")
```

http://maluwalmk.com
