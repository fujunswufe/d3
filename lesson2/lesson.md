###Review of Javascript Arrays and Objects
1. Let's now write some examples of Javascript arrays and objects
  1. For Javascript array, the index start at 0, use '[]' to denote an array
  2. For Javascript object, it consists of key and value, use '{}' to denote an object. It's something __HashMap__ in data structure.
  3. You can try to copy the code below into a html file. And open it chrome with developer tools. And use the below console. Be sure that using a local host to open the file. 
  ```HTML
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Learning D3</title>
		<!-- 	<link rel="stylesheet" href="main.css"> -->
		<script  type="text/javascript" src="https://d3js.org/d3.v4.min.js"></script>
	</head>
	<body>
		<script>
			var data = [132,71,337,93,78,43,20];
			//console.log(data[2]), console.log will print 337 because the index of Javascript start at 0

			var student = {name: "Tom", age: 20}; // this is a single Javascript object
			//console.log(student.name, student.age);

			var students = [
				{name: "Tom", 	 age: 20},
				{name: "Jenny",  age: 19},
				{name: "Mike", 	 age: 17},
				{name: "Lynn",	 age: 16}
			];
			//console.log(students[1].name, student[1].age);
			
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
