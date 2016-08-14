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
