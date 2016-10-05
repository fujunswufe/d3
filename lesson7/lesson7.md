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
                  [410, 12]];
```
2. The Scatterplot
  1. Remember, the datapoint of array __datapoints__ is an array. Thus d is an array of two values, you need to use bracket notation to access its values. For example ```d[0]``` and ```d[1]```.
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Learning D3</title>
    <script  type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
    <style type="text/css">
        div.bar {
            display: inline-block;
            width: 30px;
            height: 70px;
            background-color: black;
            margin-right: 4px;
        }
    </style>
</head>
<body>
    <script>
      var datapoints = [[5, 20], [480, 90], [250, 50], [100, 33], [330, 95], [410, 12]];
      var w = 250;
      var h = 250;
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
          .attr("r", 5); // r is the length of radius
    </script>
</body>
</html> 
```

