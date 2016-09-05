###Lesson4 Drawing divs with the power of data
#### Display a simple bar chart with div 
1. Bar charts are essentially rectangles, and can be drawed with ```<div>``` in HTML. Below is a sample code for drawing a bar chart.
2. Because this is a ```div```, the width and height can be written in ```CSS``` style. The second chunk of code is CSS style for div.
3. We need to assign a bar class for the div, thus the CSS rule will work. Write the html code by hand ```<div class="bar"></div>```.
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

