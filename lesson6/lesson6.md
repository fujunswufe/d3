###Lesson 6 Make a simple bar chart using d3.js
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
