###Lesson4 Drawing divs with the power of data
####1. Display a simple bar chart with div 
1. Bar charts are essentially rectangles, and can be drawed with ```<div>``` in HTML. Below is a sample code for drawing a bar chart.
2. Because this is a ```div```, the width and height can be written in ```CSS``` style. The second chunk of code is CSS style for div.
3. We need to assign a bar class for the div, thus the CSS rule will work. Write the html code by hand ```<div class="bar"></div>```.
4. As in ```d3```, we could use ```attr``` to assign a class to an element.
```HTML
<!-- a sample code for drawing a bar chart-->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Learning D3</title>
  <script  type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
</head>
<body>
  <div style="display: inline-block;
          width: 30px;
          height: 100px;
          background-color: black;"></div>
</body>
</html>  
```

```CSS
<!-- CSS style for div-->
div.bar {
    display: inline-block;
    width: 30px;
    height: 100px;
    background-color: black;
}
```
####2. How to set attributes
1. Attributes provide additional information about HTML elements.
2. [HTML attributes](http://www.w3schools.com/html/html_attributes.asp)
    * All HTML elements can have attributes
    * Attributes provide additional information about an element
    * Attributes are always specified in the start tag
    * Attributes usually come in name/value pairs like: name="value"
3. Some examples for attributes and values
    * src is the attribute and "w3schools.jpg" is the value
    * width is the attribute and "104" is the value
    * class is the attribute and "bar" is the value
```HTML
<img src="w3schools.jpg" width="104" height="142">
<div class="bar"></div>
```

####3. Create bar charts using d3
1. Sample d3 code for bar charts. We could use the Chrome inspector to find that there are five bars, each of them generated in ```dataset```.
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Learning D3</title>
    <script  type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
</head>
<body>
    <srcipt>
        var dataset = [ 5, 10, 15, 20, 25 ];
        d3.select("body").selectAll("div")
            .data(dataset)
            .enter()
            .append("div")
            .attr("class", "bar");
    </script>
</body>
</html>  
```
