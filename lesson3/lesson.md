###lesson 3 Introduction to div and different types of data

#### Binding data
1. At the very first begining, if we want to do data visualization, we need to bind data to d3.js functions. And after that, we will have some mapping properities. We use ```selection.data()``` to bind DOM elements. 
1. What's inside the bind ? 
    1. The data.
    2. Selections of DOM elements.
2. Data
    1. D3 can handle different types of data. These data types contains array of numbers, array of objects, JSON, GeoJSON and even loading csv files.
    
####Example on how to bind data 
1. ```d3.select("body")```: select the DOM element ```body``` and use the chain method we talked in lesson 2.
2. ```.selectAll("p")```: selects all the ```p``` DOM elements in the above ```body``` DOM element. Since there is none ```p``` DOM, this will return an empty selection. Consider this as an empty selection that would be created in the future.
3. ```.data(dataset)```: counts and parses the dataset. Because theare are five values in the dataset, everthing will be executed five times.
4. ```.enter()```. In order to create new, data-bounded DOM elements, we must use ```enter()``` in d3 functions. This method will look at the selected DOM elements. If the number of data in the dataset is bigger than the number of selected DOM elements, ```enter()``` will create a new placeholder element on which you may work on your own. And then points a reference to this new placeholder element to the following next step. 
5. ```.append("p")```: reference the placeholder element created by ```enter()``` and inserts a ```p``` element into the DOM. ```p``` is paragraph element in HTML
6. ```.text("Hello world")```: takes the reference to the new created ```p``` DOM element and inserts ```Hello world```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Learning D3</title>
    <script  type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
</head>
<body>
    <script>
        var dataset = [1, 2, 3, 4, 5];
        
        d3.select("body")
          .selectAll("p")
          .data(dataset)
          .enter()
          .append("p")
          .text("Hello world");
    </script>   
</body>
</html>  

```
