# Part 3
Objectives:
-  How to access elements in the DOM by ID, class, tag, and query selectors.

## How to access elements in the DOM
 

In order to be proficient at accessing elements in the DOM, it is necessary to know about CSS selectors and HTML elements. 

![screen shot 2017-11-28 at 8 32 31 am](https://user-images.githubusercontent.com/6153182/33322269-bd3e437e-d416-11e7-9bfb-2713a539af1f.png)


Let's add this HTML code so we can learn about each one:

``` html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Accessing Elements in the DOM</title>

  <style>
    html { font-family: sans-serif; color: #333; }
    body { max-width: 500px; margin: 0 auto; padding: 0 15px; }
    div, article { padding: 10px; margin: 5px; border: 1px solid #dedede; }
  </style>

</head>

<body>

  <h1>Accessing Elements in the DOM</h1>

  <h2>ID (#demo)</h2>
  <div id="demo">Access me by ID</div>

  <h2>Class (.demo)</h2>
  <div class="demo">Access me by class (1)</div>
  <div class="demo">Access me by class (2)</div>

  <h2>Tag (article)</h2>
  <article>Access me by tag (1)</article>
  <article>Access me by tag (2)</article>

  <h2>Query Selector</h2>
  <div id="demo-query">Access me by query</div>

  <h2>Query Selector All</h2>
  <div class="demo-query-all">Access me by query all (1)</div>
  <div class="demo-query-all">Access me by query all (2)</div>

</body>

</html>
```

Let's render this in a browser

In this HTML file, we have many elements that we will access with different `document` methods. 

## 1) Accessing Elements by ID

The easiest way to access a single element in the DOM is by its unique ID. We can grab an element by ID with the `getElementById()` method of the document object.

`document.getElementById();`

In order to be accessed by ID, the HTML element must have an id attribute. We have a div element with an ID of demo.

`<div id="demo">Access me by ID</div>`

In the Console, let's get the element and assign it to the demoId variable.

``` javascript
const demoId = document.getElementById('demo');
```
Logging demoId to the console will return our entire HTML element.

```
console.log(demoId);

<div id="demo">Access me by ID</div>
```

We can be sure we're accessing the correct element by changing the border property to red.

```
demoId.style.border = '1px solid red';
```

![screen shot 2017-11-28 at 8 43 42 am](https://user-images.githubusercontent.com/6153182/33322765-4d21dc84-d418-11e7-869f-d34b5e91f6b2.png)


### So... IDs are great, but...
Accessing an element by ID is an effective way to get an element quickly in the DOM. However, it has drawbacks; an ID must always be unique to the page, and therefore you will only ever be able to access a single element at a time with the getElementById() method. If you wanted to add a function to many elements throughout the page, your code would quickly become repititious.

# 2) Accessing Elements by Class

The class attribute is used to access one or more specific elements in the DOM. We can get all the elements with a given class name with the getElementsByClassName() method.

```
document.getElementsByClassName();
```
Now we want to access more than one element, and in our example we have two elements with a demo class.

``` html
<div class="demo">Access me by class (1)</div>
<div class="demo">Access me by class (2)</div>
```
Let's access our elements in the Console and put them in a variable called demoClass.

```
const demoClass = document.getElementsByClassName('demo');
```
Let's see if we can modify the elements the same way we did with our ID example. However, if we try to run the following code and change the border property of the class demo elements to orange, we will get an error.

```
demoClass.style.border = '1px solid orange';
```

### why doesnt this work?
The reason this doesn't work is because instead of just getting one element, we have an array-like object of elements.
(ie we have 2 divs)

### So how would we be able to access it?
JavaScript arrays must be accessed with an index number. We can therefore change the first element of this array by using an index of 0.

```
demoClass[0].style.border = '1px solid orange';
```
Generally when accessing elements by class, we want to apply a change to all the elements in the document with that particular class, not just one. We can do this by creating a for loop, and looping through every item in the array.

``` javascript
for (i = 0; i < demoClass.length; i++) {
  demoClass[i].style.border = '1px solid orange';
}
```

![screen shot 2017-11-28 at 8 55 59 am](https://user-images.githubusercontent.com/6153182/33323289-fefa63b2-d419-11e7-9968-ed2700f223da.png)

# 3) Accessing Elements by Tag
A less specific way to access multiple elements on the page would be by its HTML tag name. We access an element by tag with the getElementsByTagName() method.

```document.getElementsByTagName();```

For our tag example, we're using article elements.

``` html
<article>Access me by tag (1)</article>
<article>Access me by tag (2)</article>
```


Just like accessing an element by its class, getElementsByTagName() will return an array-like object of elements, and we can modify every tag in the document with a for loop.

``` javascript
const demoTag = document.getElementsByTagName('article');

for (i = 0; i < demoTag.length; i++) {
  demoTag[i].style.border = '1px solid blue';
}
```

![screen shot 2017-11-28 at 9 00 03 am](https://user-images.githubusercontent.com/6153182/33323470-9385251c-d41a-11e7-934c-17931c84235f.png)

# 4) Query Selectors
If you have any experience with the jQuery API, you may be familiar with jQuery's method of accessing the DOM with CSS selectors.

``` javascript
$('#demo'); // returns the demo ID element in jQuery
```
We can do the same in plain JavaScript with the querySelector() and querySelectorAll() methods.

```
document.querySelector();
document.querySelectorAll();
```

To access a single element, we will use the querySelector() method. In our HTML file, we have a demo-query element

```html
<div id="demo-query">Access me by query</div>
```

The selector for an id attribute is the hash symbol (#). We can assign the element with the demo-query id to the demoQuery variable.

```
const demoQuery = document.querySelector('#demo-query');
```
In the case of a selector with multiple elements, such as a class or a tag, querySelector() will return the first element that matches the query. We can use the querySelectorAll() method to collect all the elements that match a specific query.

In our example file, we have two elements with the demo-query-all class applied to them.

``` html
<div class="demo-query-all">Access me by query all (1)</div>
<div class="demo-query-all">Access me by query all (2)</div>
```
The selector for a class attribute is a period or full stop (.), so we can access the class with .demo-query-all.

```const demoQueryAll = document.querySelectorAll('.demo-query-all');```

Using the forEach() method, we can apply the color green to the border property of all matching elements.

``` javascript
demoQueryAll.forEach(query => {
  query.style.border = '1px solid green';
});
```

![screen shot 2017-11-28 at 9 10 07 am](https://user-images.githubusercontent.com/6153182/33323930-fd31ace6-d41b-11e7-8604-794dbad692b0.png)

With querySelector(), comma-separated values function as an OR operator. For example, querySelector('div, article') will match div or article, whichever appears first in the document. With querySelectorAll(), comma-separated values function as an AND operator, and querySelectorAll('div, article') will match all div and article values in the document.

Using the query selector methods is extremely powerful, as you can access any element or group of elements in the DOM the same way you would in a CSS file. For a complete list of selectors, review CSS Selectors on the Mozilla Developer Network.


#  Conclusion
In this tutorial, we went over 5 ways to access HTML elements in the DOM — by ID, by class, by HTML tag name, and by selector. The method you will use to get an element or group of elements will depend on browser support and how many elements you will be manipulating. You should now feel confident to access any HTML element in a document with JavaScript through the DOM.
