want to start off slow so as not to overwhelm 

# Part 1

### Introduction

The DOM is an essential part of making websites interactive. It is an interface that allows a programming language to manipulate the content, structure, and style of a website. JavaScript is the client-side scripting language that connects to the DOM in an internet browser.


Almost any time a website performs an action- for example: rotating between a slideshow of images, displaying an error when a user attempts to submit an incomplete form, or toggling a navigation menu, **it is the result of JavaScript accessing and manipulating the DOM**. 

In this section we will learn:
-  what the DOM is 
-  how to work with the document object, 
-  the difference between HTML source code and the DOM.

## So first and foremost... what excatly is the DOM?

At the most basic level, a website consists of an HTML document. The web browser that we use to view the website is a program that interprets HTML and CSS and renders the style, content, and structure into the page that you see.

In addition to parsing the style and structure of the HTML and CSS, the browser **creates a representation of the document known as the Document Object Model**. 

This model allows JavaScript to access the text content and elements of the website document as objects.

## Let's create a very basic `index.html` file and save it

```html
<!DOCTYPE html>
<html lang="en">

  <head>
    <title>Learning the DOM</title>
  </head>

  <body>
    <h1>Document Object Model</h1>
  </body>

</html>
```

Within Chrome, open up index.html. You'll see a plain website with our heading saying "Document Object Model". Right click anywhere on the page and select "Inspect". This will open up Developer Tools.

### let's go to the DOM

let's type `document` in our console tools and let's see what happens

![screen shot 2017-11-28 at 3 12 45 am](https://user-images.githubusercontent.com/6153182/33308836-1659a0a2-d3ea-11e7-917e-d8ba7d0853c7.png)

Typing document and otherwise working directly in the console is not something that you'll generally ever do outside of debugging, but it helps solidify exactly what the document object is and how to modify it, as we will discover below.


## What is the Difference Between the DOM and HTML Source Code? (ie they seem to be exactly the same)

A: the DOM can be modified by client side JS whereas HTML source code cannot.

###### Let's show this

`document.body` 

will return

```html
<body>
  <h1>Document Object Model</h1>
</body>
```

In the console, we can change some of the live properties of the body object on this website. We'll edit the style attribute, changing the background color to fuchsia. Type this into the console:

`document.body.style.backgroundColor = 'fuchsia';`

After typing and submitting the above code, you'll see the live update to the site, as the background color changes.

### add image here

Switching to the Elements tab, or typing document.body into the console again, you will see that the DOM has changed.

```html
<body style="background-color: fuchsia;">
  <h1>Document Object Model</h1>
</body>
```

The JavaScript code we typed, assigning fuchsia to the background color of the body, is now a part of the DOM.

However, right click on the page and select "View Page Source". You will notice that the source of the website does not contain the new style attribute we added via JavaScript. The source of a website will not change and will never be affected by client-side JavaScript. If you refresh the page, the new code we added in the console will disappear.

### Conclusion
In this tutorial, we defined the DOM, accessed the document object, used JavaScript and the console to update a property of the document object, and went over the difference between HTML source code and the DOM.

========= 

# Part 2

In this tutorial, we will review HTML terminology, which is essential to working with JavaScript and the DOM, and we will learn about the DOM tree, what nodes are, and how to identify the most common node types. Finally, we will move beyond the console and create a JavaScript program to interactively modify the DOM.

let's use that basic CSS that we created a moment ago

##### The simplest way to access an element with JavaScript is by the id attribute. Let's add the link we have above into our index.html file with an id of nav.

```html
<!DOCTYPE html>
<html lang="en">

  <head>
    <title>Learning the DOM</title>
  </head>

  <body>
      <h1>Document Object Model</h1>
      <a id="nav" href="index.html">Home</a>
  </body>

</html>
```

& reload

We're going to use the `getElementById()` method to access the entire element. In the console, type the following:
`document.getElementById('nav');`

we'll get back:

`<a id="nav" href="index.html">Home</a>`

We have retrieved the entire element using `getElementById()`. Now, instead of typing that object and method every time we want to access the nav link, we can place the element into a variable to work with it more easily.

`let navLink = document.getElementById('nav');`

The navLink variable contains our anchor element. From here, we can easily modify attributes and values. For example, we can change where the link goes by changing the href attribute:

`navLink.href = 'https://www.wikipedia.org';`

We can also change the text content by reassigning the textContent property:

`navLink.textContent = 'Navigate to Wikipedia';`

Now when we view our element, either in the console or by checking the Elements tag, we can see how the element has been updated.

`navLink;
Output
<a id="nav" href="https://www.wikipedia.org/">Navigate to Wikipedia</a>`

This is also reflected on the front-end of the website.

![screen shot 2017-11-28 at 3 39 43 am](https://user-images.githubusercontent.com/6153182/33309909-d2cba2c8-d3ed-11e7-988d-c6ba0b0f11e9.png)

### however...
Refreshing the page will revert everything back to their original values. :/ :/ :/

-  So to recap

At this point, we should understand how to use a `document` method to access an element, how to assign an element to a variable, and how to modify properties and values in the element.


# The Dom Tree and Nodes

All items in the DOM are defined as nodes. There are many types of nodes, but there are three main ones that we work with most often:

-  Element nodes
-  Text nodes
-  Comment nodes


When an HTML element is an item in the DOM, it is referred to as an element node. Any lone text outside of an element is a text node, and an HTML comment is a comment node. In addition to these three node types, the document itself is a document node, which is the root of all other nodes.

The DOM consists of a tree structure of nested nodes, which is often referred to as the DOM tree. You may be familiar with an ancestral family tree, which consists of parents, children, and siblings. The nodes in the DOM are also referred to as parents, children, and siblings, depending on their relation to other nodes.

``` html
<!DOCTYPE html>
<html>

  <head>
    <title>Learning About Nodes</title>
  </head>

  <body>
    <h1>An element node</h1>
    <!-- a comment node -->
    A text node.
  </body>

</html>
```

The html element node is the parent node. head and body are siblings, children of html. body contains three child nodes, which are all siblings — the type of node does not change the level at which it is nested.

# Modifying the DOM with Events
Up until now, we've only seen how to modify the DOM in the console, which we have seen is temporary; every time the page is refreshed, the changes are lost. In the Introduction to the DOM tutorial, we used the console to update the background color of the body. We can combine what we've learned throughout this tutorial to create an interactive button that does this when clicked.

Let's go back to our index.html file and add a button element with an id. We'll also add a link to a new file in a new js directory js/scripts.js.

## Events
An event in JavaScript is an action the user has taken. When the user hovers their mouse over an element, or clicks on an element, or presses a specific key on the keyboard, these are all types of events. In this particular case, we want our button to listen and be ready to perform an action when the user clicks on it. We can do this by adding an event listener to our button.

Create scripts.js and save it in the new js directory. Within the file, we'll first find the button element and assign it to a variable.

![screen shot 2017-11-28 at 4 06 21 am](https://user-images.githubusercontent.com/6153182/33311016-8f0cb56e-d3f1-11e7-9e1e-cc70cbe38ef3.png)


Using the addEventListener() method, we will tell the button to listen for a click, and perform a function once clicked.

``` javascript
button.addEventListener('click', () => {
  // action will go here
});
```

Finally, inside of the function, we will write the same code from the previous tutorial to change the background color to fuchsia.

``` javascript
let button = document.getElementById('changeBackground');
button.addEventListener('click', () => {
  document.body.style.backgroundColor = 'fuchsia';
});
```

# Recap
In this tutorial, we reviewed terminology that will allow us to understand and modify the DOM. We learned how the DOM is structured as a tree of nodes that will usually be HTML elements, text, or comments, and we created a script that would allow a user to modify a website without having to manually type code into the developer console.

==========

# Part 3
## How to access elements in the DOM

In Understanding the DOM Tree and Nodes, we went over how the DOM is structured as a tree of objects called nodes, and that nodes can be text, comments, or elements. Usually when we access content in the DOM, it will be through an HTML element node.

In order to be proficient at accessing elements in the DOM, it is necessary to have a working knowledge of CSS selectors, syntax and terminology as well as an understanding of HTML elements. In this tutorial, we will go over several ways to access elements in the DOM: by ID, class, tag, and query selectors.

![screen shot 2017-11-28 at 8 32 31 am](https://user-images.githubusercontent.com/6153182/33322269-bd3e437e-d416-11e7-9bfb-2713a539af1f.png)

It is important when studying the DOM to type the examples on your own computer to ensure that you are understanding and retaining the information you learn.

Let's add this HTML code:

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

## 1 Accessing Elements by ID

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
Output
<div id="demo">Access me by ID</div>
```

We can be sure we're accessing the correct element by changing the border property to red.

```
demoId.style.border = '1px solid purple';
```

![screen shot 2017-11-28 at 8 43 42 am](https://user-images.githubusercontent.com/6153182/33322765-4d21dc84-d418-11e7-869f-d34b5e91f6b2.png)


### So... IDs are great, but...
Accessing an element by ID is an effective way to get an element quickly in the DOM. However, it has drawbacks; an ID must always be unique to the page, and therefore you will only ever be able to access a single element at a time with the getElementById() method. If you wanted to add a function to many elements throughout the page, your code would quickly become repititious.

# Accessing Elements by Class

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

# Accessing Elements by Tag
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

# Query Selectors
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




