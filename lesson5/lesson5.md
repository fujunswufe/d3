###Lesson 5 How to use data and an intro to SVG
####How to use the power of data
1. In lesson 4, we talked about how to draw bar charts with an array of dataset.
2. Now let's now initialize some dataset randomly and use these data to create a barchart.
3. You can open the developer tool of Chrome. Type ```console.log(dataset)``` in javascript console. And finally we can see the generalized random numbers. 
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
####An introduction to SVG
1. SVG element
    1. SVG stands for Scalable Vector Graphics.
    2. SVG defines vector-based graphics in XML format.
    3. SVG graphics do NOT lose any quality if they are zoomed or resized.
    4. SVG could be included within HTML element.
    5. Like other XML based elements, SVG has starting tag and closing tag
    ```SVG
    <html>
        <body>
        
        <h1>An intro to SVG</h1>
        
        <svg width="100" height="100"> // width and height both define the space of an SVG element. the default of the unit is pixels.
          <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
        </svg>
        
        </body>
    </html>
    ```
