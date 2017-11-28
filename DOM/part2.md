# Part 2

Objectives:

-  we will learn about the DOM tree
-  what nodes are, and how to identify the most common node types
-  we'll create a JavaScript program to interactively modify the DOM.

In this tutorial, we will review HTML terminology, which is essential to working with JavaScript and the DOM, and we will learn about the DOM tree, what nodes are, and how to identify the most common node types. Finally, we will move beyond the console and create a JavaScript program to interactively modify the DOM.

let's use that basic CSS that we created a moment ago

##### The simplest way to access an element with JavaScript is by the id attribute. Let's add a nav id to our HTML.

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


We're going to use the `getElementById()` method to access the entire element. In the console, type the following:
`document.getElementById('nav');`

we'll get back:

`<a id="nav" href="index.html">Home</a>`

We have retrieved the entire element using `getElementById()`. Now, instead of typing that object and method every time we want to access nav link, we can store it into a variable.

`let navLink = document.getElementById('nav');`

Now, we can easily modify attributes and values. For example, we can change where the link goes by changing the href attribute:

`navLink.href = 'https://www.wikipedia.org';`

We can also change the text content by reassigning the textContent property:

`navLink.textContent = 'Navigate to Wikipedia';`

`navLink;
Output
<a id="nav" href="https://www.wikipedia.org/">Navigate to Wikipedia</a>`

This is also reflected on the front-end of the website.

![screen shot 2017-11-28 at 3 39 43 am](https://user-images.githubusercontent.com/6153182/33309909-d2cba2c8-d3ed-11e7-988d-c6ba0b0f11e9.png)

### however...
Refreshing the page will revert everything back to their original values. :/ :/ :/

### To recap

-  we know how to use a `document` method to access an element
-  how to assign an element to a variable
-  how to modify properties and values in the element.


# The Dom Tree

### The document itself is a document node, which is the root of all other nodes.


The DOM consists of a tree structure of nested nodes, which is often referred to as the DOM tree. 
You may be familiar with an ancestral family tree, which consists of parents, children, and siblings. The nodes in the DOM are also referred to as parents, children, and siblings, depending on their relation to other nodes.

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
Up until now, we've only seen how to modify the DOM in the console, which we have seen is temporary; every time the page is refreshed, the changes are lost. Let's create an interactive button that does this when clicked.

Let's go back to our index.html file and add a button element with an id. We'll also add a link to a new file in a new js directory js/scripts.js.

## Events
An event in JavaScript is an action the user has taken. 
Examples:
-  when the user hovers their mouse over an element
-  clicks on an element
-  or presses a specific key on the keyboard

In our case, we want our button to listen and be ready to perform an action when a user clicks on it. We can do this by adding an event listener to our button.

Let's first add a button to our HTML
```
<button id ="changeBackground">Change Background Color</button>
```
#### Next
Create scripts.js and save it in the new js directory. Within the file, we'll first find the button element and assign it to a variable.

in our scripts.js add:
```javascript
let button = document.getElementById('changeBackground');
```

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
  document.body.style.backgroundColor = 'indigo';
});
```

# Recap
In this tutorial, we reviewed terminology that will allow us to understand and modify the DOM. 

We learned how the DOM is structured as a tree of nodes.

We created a script that would allow a user to modify a website without having to manually type code into the developer console.
