###Lesson 8 Scales of D3
1. Sometimes, the input datasets are unlikely to correspond exactly to pixel measurements for visualization. 
2. d3 has scale functions. In this lesson, we only talk about linear scale function, which is much common. Once a d3 object is created, you call the scale function, pass it a data value, and it will return a scaled output value. 

####Sold corns and Pixels
1. For example, a farmer sells corns every month. First month, he sold 200 corns and next month, he sold 300. At first, we may use the data values as display values. And you want to make a bar chart to display those values. However, 900 pixels is really big on display. You have to scale these data values to smaller outputs and display them. 
```Javascript 
var dataset = [200, 300, 500, 700, 900];
```

####Domains and Ranges
1. Domains are for __input__ and ranges are for __output__. 
2. The input domain is the range of possible input data values. For example, the input domain would be 200 and 500 (the minimum value of maximum value of input) or 0 and 500.
3. The output range is the range of possible output values. It is normally used as display values in pixel units. Unlike the input domain, we could set the output range by ourself depending on the size of the display. For example, we could set range between 10 and and 50. 
4. If we set the output range between 10 and 50. If we input value 200 to scale, it will return 10 and input value 900 to scale, it will return 900. 

####Normalization
1. Normalization is the process of transforming a numeric to a new one between 0 and 1, based on the input values, mainly minimum and maximum. 
2. For example, ```var dataset = [10, 44, 33, 99, 100, 39, 77, 13]```. 10 would map to 0.1 and 33 would map to 0.33. This is one kind of linear scales. 

####Creating a Scale
1. First, we need to use d3 to call ```scale``` function
2. Second, use whatever scale method you want. In this case, we use ```linear``` scale. 
3. Set domain and range.
4. Try to write your own scale funtions and find out the results.
```Javascript
var scale = d3.scale()
              .linear()
              .domain([200, 900])
              .range([10, 50]);
scale(300); // find out the results by yourself.
scale(500);
```

####Scaling the Scatterplot
1. First we need to find two maximums corresponding to x-axis and y-axis.
2. Create two scale functions for x-axis and y-axis. For the var name, use whatever you want. However, these names should have some meaning for remember. 
3. For those you guys who don't understand why we use ```xMax + 50``` and ```yMax + 50```. This is because that we want to add some flexibility. 
4. Try to read the code below, especially the code between ```<script>``` and ```</script>```.

```Javascript

var dataset = [[5, 20], [480, 90], [250, 50], [100, 33], [330, 95], [410, 12]];
var w = 200;
var h = 300;

// remember the first element of a coordinate array is x-axis and second element is y-axis
var xMax = d3.max(dataset, function(d) {return d[0];});
var yMax = d3.max(dataset, function(d) {return d[1];});

var svg = d3.select("body")
            .append("svg")
            .attr("width", w)
            .attr("height", h);

var xScale = d3.scaleLinear()                        
                .domain([0, xMax + 50])
                .range([0, w]);
var yScale = d3.scaleLinear()        
                .domain([0, yMax + 50])
                .range([0, h]);

svg.selectAll("circle")
  .data(dataset)
  .enter()
  .append("circle")
  .attr("cx", function(d) {
      return xScale(d[0]);  
  })
  .attr("cy", function(d) {
      return yScale(d[1]);
  })
  .attr("r", 5); 

svg.selectAll("text")
  .data(dataset)
  .enter()
  .append("text")
  .text(function(d) {
    return d[0] + "," + d[1]; // "+" is like an append operator
  })
  .attr("x", function(d) { // coordinate for x axis
    return xScale(d[0]);
  })
  .attr("y", function(d) { // coordinate for y axis
    return yScale(d[1]);
  })
  .attr("font-family", "sans-serif") // add some font style for the text
  .attr("font-size", "10px")
  .attr("fill", "blue");
```         

####Refining the Plot
1. We want to refine the coordinate of the plot. It it because that this coordinate system starts at top left corner. Thus, larger y values are towards the bottom and smaller y values are at the top.
2. Reversing the coordinate is super easy for d3. We just need to reverse the output range, from ```range([h, 0])``` to ```range([0,h])```.

```Javascript
var yScale = d3.scaleLinear()        
              .domain([0, yMax + 50])
              .range([h, 0]);
```
3. For some of the text may be cut off. And we can use ```padding``` to solve this problem. This could provide us with 20 pixels of extra space on the left, right, top, and bottom edges of an SVG

```Javascript
var padding = 20;

var xScale = d3.scaleLinear()
               .domain([0, xMax + 50])
               .range([padding, w - padding]);

var yScale = d3.scaleLinear()
               .domain([0, yMax + 50])
               .range(h - padding, padding);
```
4. Refine the radius to length between 1 and 5. 
```Javascript
var rScale = d3.scaleLinear()
               .domain([0, yMax + 50])
               .range([1, 5]);
               
// the scale of radius should be something like 

.attr("r", function(d) {
  return rScale(d[1]);
})
```

####Other Methods and Scales. 
1. This is a [API Reference](https://github.com/d3/d3-scale) for d3 scales
2. Different tyle of scales
    * Continuous (Linear, Power, Log, Identity, Time)
    * Sequential
    * Quantize
    * Quantile
    * Threshold
    * Ordinal (Band, Point, Category)


####Final Code
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
        var dataset = [[5, 20], [480, 90], [250, 50], [100, 33], [330, 95], [410, 12]];
        var w = 200;
        var h = 300;
        var padding = 20;

        // remember the first element of a coordinate array is x-axis and second element is y-axis
        var xMax = d3.max(dataset, function(d) {return d[0];});
        var yMax = d3.max(dataset, function(d) {return d[1];});

        var svg = d3.select("body")
                    .append("svg")
                    .attr("width", w)
                    .attr("height", h);

        var xScale = d3.scaleLinear()                        
                        .domain([0, xMax])
                        .range([padding, w - 2 * padding]); // w - 2 * padding avoid some text being cut off
        var yScale = d3.scaleLinear()        
                        .domain([0, yMax])
                        .range([h - padding, padding]);
        var rScale = d3.scaleLinear()
                        .domain([0, yMax])
                        .range([1, 5]);

        svg.selectAll("circle")
          .data(dataset)
          .enter()
          .append("circle")
          .attr("cx", function(d) {
              return xScale(d[0]);  
          })
          .attr("cy", function(d) {
              return yScale(d[1]);
          })
          .attr("r", function(d) {
              return rScale(d[1]);
          }); 

        svg.selectAll("text")
          .data(dataset)
          .enter()
          .append("text")
          .text(function(d) {
            return d[0] + "," + d[1]; // "+" is like an append operator
          })
          .attr("x", function(d) { // coordinate for x axis
            return xScale(d[0]);
          })
          .attr("y", function(d) { // coordinate for y axis
            return yScale(d[1]);
          })
          .attr("font-family", "sans-serif") // add some font style for the text
          .attr("font-size", "10px")
          .attr("fill", "blue");
  </script>
  </body>
  </html> 
```

