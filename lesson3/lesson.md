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
7. The next step is to load the below html page in your browser. Remember to start your localhost server. Wow, you would see five paragraphs. 

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
####Different types of data
1. variables
    1. A variable is the smallest building block of data
    2. In javascript, we need to use ```var``` to declare variable
    ```javascript
    var visited = false
    var num = 50
    var digitNum = 3.1415926
    var text = "Hello world"
    // how to change value of a variable ins Javascript
    var value = 100
    value = true
    value = 1.1111
    value = "Let's learn d3.js"
    ```
2. arrays
    1. Use hard brackets __[]__ indicate an array
    2. An array is a list of values. In javascript, index of javascript starts at 0.
    3. An array can contain different types of values, for example strings and objects. 
    ```javascript
    var nums = [1, 10, 100, 1000]
    nums[0] // this will return 1
    nums[3] // this will return 1000
    
    var strs = ["Windows", "Mac OS", "Linux", "Unix"]
    ```
3. objects
    1. Use curly brackets {} to indicate an object. 
    2. Inside the brackets, we include indices and values.
    3. To get each value, we use dot notation with the name of the index
    ```javascript
    var student = {
        age: 21,
        gender: "male",
        major: "Computer Science",
        full_time: true
    };
    // reference the value of the object
    student.age // return 21
    student.gender // return "male"
    student.major // return "Computer Science"
    student.full_time // return true
    ```
4. Objects + Arrays
    1. We can use the above two data structures to create arrays of objects.
    2. We use hard brackets [] on the outside to indicate an array,  and followed by curly brackets {} to indicate an object and each object separated by a comma.
    ```javascript
    var students = [
        {
            age: 21,
            gender: "male",
            major: "Computer Science",
            full_time: true
        }, 
         {
            age: 18,
            gender: "female",
            major: "Fiance",
            full_time: false
        },
        {
            age: 24,
            gender: "male",
            major: "Statistics",
            full_time: true
        }
    ];
    
    students[0] // return first object of the students array
    students[1].age // return 18
    students[1].gender // return female
    students[1].major  // return Finance
    students[1].full_time // return false
    ```
5. JSON
    1. JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate.
    2. If you want to learn more details about JSON, go to this [website](http://www.json.org)
    3. The only difference between JSON and an javascript object is that the indices are surrounded by double quotation marks ```""```, making them as string values.
    ```JSON
    var studentJSON = {
        "age": 24,
        "gender": "male",
        "major": "Statistics",
        "full_time": true
    };
    ```
6. GeoJSON
    1. GeoJSON is a format for encoding a variety of geographic data structures. A GeoJSON object may represent a geometry, a feature, or a collection of features. GeoJSON supports the following geometry types: Point, LineString, Polygon, MultiPoint, MultiLineString, MultiPolygon, and GeometryCollection. Features in GeoJSON contain a geometry object and additional properties, and a feature collection represents a list of features. _Reference_ from [geojson.org](http://geojson.org/geojson-spec.html)
    2. A simple GeoJSON data is below. We will use GeoJSON to create our choropleth. 
    ```javascript
    var geodata = {
        "type": "FeatureCollection",
        "features": [
            {
                "type": "Feature",
                "geometry": {
                    "type": "Point",
                    "coordinates": [ 150.1282427, -24.471803 ]
                },
                "properties": {
                    "type": "town"
                }
            }
        ]
    }; 
    ```
