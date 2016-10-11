###Lesson 8
1. Sometimes, the input datasets are unlikely to correspond exactly to pixel measurements for visualization. 
2. d3 has scale functions. In this lesson, we only talk about linear scale function, which is much common. Once a d3 object is created, you call the scale function, pass it a data value, and it will return a scaled output value. 

####Sold corns and Pixels
1. For example, a farmer sells corns every month. First month, he sold 200 corns and next month, he sold 300. At first, we may use the data values as display values. And you want to make a bar chart to display those values. However, 900 pixels is really big on display. You have to scale these data values to smaller outputs and display them. 
```Javascript 
var dataset = [200, 300, 500, 700, 900];
```

####Domains and Ranges
1. Domains are for __input__ and ranges are for __output__. 
2. The input domain is the range of possible input data values. For example, the input domain would be 200 and 500 (the minimum value of maximum value of input) or 0 and 500.
3. The output range is the range of possible output values. It is normally used as display values in pixel units. Unlike the input domain, we could set the output range by ourself depending on the size of the display. For example, we could set range between 10 and and 50. 

####Normalization

####Creating a Scale

####Scaling the Scatterplot

####Refining the Plot

####Other Methods and Scales. 
