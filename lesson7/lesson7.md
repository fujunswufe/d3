###Lesson 7 Make a Scatterplot using d3.js

####What is a Scatterplot
1. When we have two sets of data to draw against each other, we need two dimensions. The scatterplot is a common way of representing two sets of corresponding data on two different axes: x and y.

####Data for Scatterplot
1. Each data point should contain two values, representing x and y. In Javascript, this data point should be an array. Thus we have an array of arrays. 
```javascript
var datapoints = [[5, 20],  // we separate each array by commas
                  [480, 90], 
                  [250, 50], 
                  [100, 33], 
                  [330, 95], 
                  [410, 12]]
```
2. The Scatterplot
```javascript
var w = 200;
var h = 200;
var svg = d3.select("body")
            .append("svg")
            .("width", w)
            .("height", h);
            
    svg.selectAll("circle")
        .data(datapoints)
        .enter()
        .append("circle")
        .attr("cx", function(d) { // cx and cy are the coordinates of the circle
            return d[0];
        })
        .attr("cy", function(d) {
            return d[1];
        })
        .attr("r", 5);
```
