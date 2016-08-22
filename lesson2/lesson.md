###Review of Javascript Arrays and Objects
1. Let's now write some examples of Javascript arrays and objects
  1. For Javascript array, the index starts at 0, use '[]' to denote an array
  2. For Javascript object, it consists of key and value, use '{}' to denote an object. It's something __HashMap__ in data structure.
  3. We will try to write some filter functions for arrays and objects in the code below
  4. You can try to copy the code below into a html file. And open it in _chrome_ with developer tools. And use the below console. Be sure that using a local host to open the file. 
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
			var data = [132,71,337,40,93,78,90,43,20];
			//console.log(data[2]), console.log will print 337 because the index of Javascript start at 0
			
			var dataGreater50 = data.filter(function(num){
				return num > 50;
			}); // this will create an array with numbers greater than 50
			
			// this is a single Javascript object, name and age are "keys", and Tom and 20 are "values"
			var student = {name: "Tom", age: 20}; 
			// console.log(student.name, student.age);

			var students = [
				{name: "Tom", 	 age: 20},
				{name: "Jenny",  age: 19},
				{name: "Mike", 	 age: 17},
				{name: "Lynn",	 age: 16}
			];
			//console.log(students[1].name, student[1].age);
			
			var studentsAgeGreaterThan18 = students.filter(function(student){
				return student.age > 50;
			});
			
			// use a for loop to print the information in students
			for(var i = 0, len = students.length; i < len; i++){
				console.log(students[i].name, student[i].age);
			}
			// use an anonymous functiom to print each object in students
			students.forEach(function(entry){ 
				console.log(entry.name, entry.age);
			});
		</script>	
	</body>
</html>
  ```
###Introduction to d3 functions
1. Now I will write some basic useful d3 functions. There are too many functions in d3.js and you can't remember them all. The the most efficient way is to use [API](https://github.com/d3/d3/blob/master/API.md) when you need some d3 fucntions. 
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
			var data = [132,71,337,40,93,78,90,43,20];
			// compute the minimum value in an array.
			var dataMin = d3.min(data);
			// compute the maximum value in an array.
			var dataMax = d3.max(data);
			// compute the minimum and maximum value in an array
			var dataLowHigh = d3.extent(data); 
			
			console.log(dataMin, dataMax, dataLowHigh);

			var students = [
				{name: "Tom", 	 age: 20},
				{name: "Jenny",  age: 19},
				{name: "Mike", 	 age: 17},
				{name: "Lynn",	 age: 16}
			];
			// this is an anomynous function, function(d)
			var studentsMinAge = d3.min(students, function(d){
				return d.age;
			});
			var studentsMaxAge = d3.max(students, function(d){
				return d.age;
			});
			var studentsLowHighAge = d3.extent(students, function(d){
				return d.age;
			});
			console.log(studentsMinAge, studentsMaxAge, studentsLowHighAge);
		</script>	
	</body>
</html>
  ```
###Add DOM elements using d3 functions
1. Next we will try to use d3 to create a DOM element. Normally, we should use d3 to create a SVG elements to decorate a visualization object. However, this time we start from an easy example.
2. First we use d3.select method to select an DOM element. In the code below, we select the DOM "body"
3. append a "p" element at the end of select. "p" represents a paragraph in html tag.
4. set the content of that "p" to "Hello World"
5. Cheers. We already use d3 function to create a DOM element.
	```html
	<!DOCTYPE html>
	<html lang="en">
	    <head>
	        <meta charset="utf-8">
	        <title>D3 function</title>
	        <script type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
	    </head>
	    <body>
	        <script type="text/javascript">
				// d3.select("body").append("p").text("Hello World");
	        </script>
	    </body>
	</html>
	```
