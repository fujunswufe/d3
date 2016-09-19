###Lesson 6 Make a simple bar chart using d3.js
####Old chart of div
1. In lesson 4, we attempted to make a bar chart using ```div```. However, ```div``` has some limitations compared to ```SVG```. Here is the following code.
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
        var dataset = [1, 2, 3, 4, 5];
        d3.select("body").selectAll("div")
            .data(dataset)
            .enter()
            .append("div")
            .attr("class", "bar")
            .style("height", function(d) {
                return d * 20 + "px";
            });
    </script>
</body>
</html>  
```
####New chart of svg
1. In this lesson, I would write the details for how to make a bar chart using svg step by step. 
    * First, we need to create an empty ```SVG``` with defined height and width, and add it to the DOM. The newly create emtpy SVG is in body.
    ```Javascript
    var w = 500; // predefined width
    var h = 100; // predefined height
    var svg = d3.select("body")
                .append("svg") // append an empty SVG DOM
                .attr("width", w)
                .attr("height", h);
    ```
    * Instead of using div, we create ```rect``` and add each of them. Every rect has its coordinate (x, y) and corresponding width and height.
    ```Javascript
    svg.selectAll("rect") // select all rect inside SVG. However, there isn't any rect, empty object will be returned. 
        .data(dataset) // the dataset has 20 data points
        .enter() // enter() will be called 20 times, this will return a place holder section for each of rect
        .append("rect") // for each of the place holder, this will add a rect and add it to DOM.
        .attr("x", 0) // each of the rect's x coordinate would be 0. This will create overlapping bars, we will improve it later
        .attr("y", 0) // each of the rect's y coordinate would be 0
        .attr("width", 20)
        .attr("height", 100);
    ```
    * For improvement. Remember that the (0,0) of SVG is the upper-left corner. So we need to flip the (0, 0) coordinate to lower-left corner. And for x coordinate, we will assign a dynamic value related to index of the data and the overall svg's width
    ```Javascript
    svg.selectAll("rect")
        .data(dataset)
        .enter()
        .attr("x", function(d, i) { // i is the index of each value in dataset
            return i * (w / dataset.length);
        })
        .attr("y", function(d) {
            return h - d; // for each bar's y coordinate, it will start at h - d
        })
        .attr("width", w / dataset.length - padding) // minus padding means that we need to leave some space between bars
        .attr("height", function(d){
            return d; // Although, each bar will look like a little short
        });
    ```

    ```HTML
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Learning D3</title>
        <script  type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
    </head>
    <body>
        <script>
            var dataset = [5, 10, 15, 20, 25, 12, 8, 17, 22, 7, 27, 30, 13, 11, 19, 20, 29, 33, 31, 22];
            var padding = 2;
            var w = 500;
            var h = 100;
            var svg = d3.select("body")
                        .append("svg")
                        .attr("width", w)
                        .attr("height", h);
            
            svg.selectAll("rect")
                .data(dataset)
                .enter()
                .append("rect")
                .attr("x", function(d, i) {
                    return i * (w / dataset.length);
                })
                .attr("y", function(d) {
                    return h - d * 3; // we want to make the y coordinate start at h - d * 3
                })
                .attr("width", w / dataset.length - padding)
                .attr("height", function(d) {
                    return d * 3; // Because the y coordinate starts at h - d * 3, the height will be d * 3. Please make sure that d * 3 is smaller than the height of the whole SVG
                });
        </script>
    </body>
    </html> 
    ```
####Add colors and labels to bar chart
1. Color. We want to change the black bar chart to other colors, and the shape's color would reflect the corresponding data value. So, if the value is bigger, it will show deep blud bar, otherwise, light blue bar.
    ```Javascript
    svg.selectAll("rect")
        .data(dataset)
        .enter()
        .append("rect")
        .attr("x", function(d, i) {
            return i * (w / dataset.length);
        })
        .attr("y", function(d) {
            return h - d * 3;
        })
        .attr("width", w / dataset.length - padding)
        .attr("height", function(d) {
            return d * 3; 
        })
        .attr("fill", function(d) {
            return "rgb(0, 0, " + (d * 5) + ")";
        });
    ```

2. label
