###Setting up Environment###

####Some useful d3.js links
1. [d3js.org](https://d3js.org/)
2. [D3 API Reference](https://github.com/d3/d3/blob/master/API.md)
3. [Mike Bostock's examples](http://bl.ocks.org/mbostock)

####How to set up a localhost web server ? 
1. If you guys want to use d3.js and html to do visualization, you have to set up a localhost first
2. This is very easy for Linux and Mac OS system. Just type ```python -m SimpleHTTPServer 8888``` in the __Terminal__. If want to want a little complex localhost, you can try [MAMP](https://html5hive.org/how-to-setup-a-localhost/)
3. For Windows System, I recommend to install python first. Then type ```python -m SimpleHTTPServer 8888``` in __cmd__ which is DOS terminal. 
4. As you knop ```SimpleHTTPServer``` is for python 2. If you use python 3, please use ```http.server``` instead of ```SimpleHTTPServer```. ```8888``` is only the port number, you can also use ```8000``` and so on.
5. Then open your brower, type ```localhost:8888``` if you use port number ```8888```. Find the HTML files of your visualization projects and click it, then you can show your visulization charts in your browser. 
  
####Web Browser
1. I Strongly recommend you to use Chrome. Firefox is also fine. 
2. For Chrome users, click on top right to find ```more tools``` and click ```Developer Tools```.
3. There is a console in the bottom of the browser, you can use this console to debug your js and d3.js if you have bugs in your code. 
4. here is the screen shot ![screenshot](https://github.com/fujunswufe/d3/blob/master/lesson1/developer.png)

####Fundamentals
1. HTML 
	* Hypertext Markup Language is used to structure content for web browsers
	* A very simple HTML file can be like this 
	
	```html
	<html>
	    <head>
	        <title>Test</title>
	    </head>
	    <body>
	        <h1>Test</h1>
	        <p>Hello world!</p>
	    </body>
	</html>
	```
2. DOM
	1. [The Document Object Model (DOM)](https://en.wikipedia.org/wiki/Document_Object_Model) is a cross-platform and language-independent application programming interface that treats an HTML, XHTML, or XML document as a tree structure wherein each node is an object representing a part of the document.
	2. In the above HTML, head is the parent element to title. All elements on this page are descendants of html.

3. CSS
	* [Cascading Style Sheets (CSS)](https://en.wikipedia.org/wiki/Cascading_Style_Sheets) is a style sheet language used for describing the presentation of a document written in a markup language.
	* A simple css stylesheet looks like this
	```css
	body {
	    background-color: white;
	    color: red;
	}
	```
	* CSS consists of selectors and rules. CSS Selectors find specific elements to which styles would be applied
	```css
	h1          /* Selects level 1 headings              */
	p           /* Selects paragraphs                    */
	.caption    /* Selects elements with class "caption" */
	#subnav     /* Selects element with ID "subnav"      */
	```
	*  CSS selectors and rules use curly brackets
	```css
	p {
	    font-size: 12px;
	    line-height: 14px;
	    color: black;
	}
	```
	* CSS rules can be contained in the head of a document or saved in an external file with a .css file, and referenced in the HTML's head.
4. [SVG](http://www.w3schools.com/svg/default.asp)
	1. SVG stands for Scalable Vector Graphics
	2. SVG is used to define vector-based graphics for the Web
	3. SVG defines the graphics in XML format
	4. SVG graphics do NOT lose any quality if they are zoomed or resized
	5. SVG in HTML 5
	```html
	<!DOCTYPE html>
	<html>
		<body>
		
			<h1>My first SVG</h1>
			
			<svg width="100" height="100">
			  <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
			</svg>
		
		</body>
	</html>
	```
