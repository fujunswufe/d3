###Review of Javascript Arrays and Objects
1. Let's now write some examples of Javascript arrays and objects
  1. For Javascript array, the index start at 0, use '[]' to denote an array
  2. For Javascript object, it consists of key and value, use '{}' to denote an object. It's something __HashMap__ in data structure. 
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

			var Student = {name: "Tom", age: 20};
			//console.log(.key, donut.value);

			var donuts = [
				{key: "Glazed", 	value: 132},
				{key: "Jelly", 		value: 71},
				{key: "Holes", 		value: 337},
				{key: "Sprinkles",	value: 93}
			];
			//console.log(donuts[1].key, donuts[1].value);

			for(var i = 0, len = donuts.length; i < len; i++){
				console.log(donuts[i].key, donuts[i].value);
			}

			donuts.forEach(function(entry){
				console.log(entry.key, entry.value);
			});
		</script>	
	</body>
</html>
  ```
