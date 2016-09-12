###Lesson 5 How to use data and an intro to SVG
####How to use the power of data
1. In lesson 4, we talked about how to draw bar charts with an array of dataset.
2. Now let's now initialize some dataset randomly and use these data to create a barchart.
```html
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
        var dataset = [];
        for (i = 0; i < 25; i++) {
            var num = Math.random() * 20 // this would create some decimal point values
            // var num = Math.round(Math.random() * 20) // this would create only integers
            dataset.push(num)
        }
        d3.select("body").selectAll("div")
            .data(dataset)
            .enter()
            .append("div")
            .attr("class", "bar")
            .style("height", function(d) {
                return d * 10 + "px";
            });
    </script>
</body>
</html>
```
