Part 2
In this tutorial, we will review HTML terminology, which is essential to working with JavaScript and the DOM, and we will learn about the DOM tree, what nodes are, and how to identify the most common node types. Finally, we will move beyond the console and create a JavaScript program to interactively modify the DOM.

let's use that basic CSS that we created a moment ago

The simplest way to access an element with JavaScript is by the id attribute. Let's add the link we have above into our index.html file with an id of nav.

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
& reload

We're going to use the getElementById() method to access the entire element. In the console, type the following: document.getElementById('nav');

we'll get back:

<a id="nav" href="index.html">Home</a>

We have retrieved the entire element using getElementById(). Now, instead of typing that object and method every time we want to access the nav link, we can place the element into a variable to work with it more easily.

let navLink = document.getElementById('nav');

The navLink variable contains our anchor element. From here, we can easily modify attributes and values. For example, we can change where the link goes by changing the href attribute:

navLink.href = 'https://www.wikipedia.org';

We can also change the text content by reassigning the textContent property:

navLink.textContent = 'Navigate to Wikipedia';

Now when we view our element, either in the console or by checking the Elements tag, we can see how the element has been updated.

navLink; Output <a id="nav" href="https://www.wikipedia.org/">Navigate to Wikipedia</a>

This is also reflected on the front-end of the website.

screen shot 2017-11-28 at 3 39 43 am

however...

Refreshing the page will revert everything back to their original values. :/ :/ :/

So to recap
At this point, we should understand how to use a document method to access an element, how to assign an element to a variable, and how to modify properties and values in the element.

The Dom Tree and Nodes
All items in the DOM are defined as nodes. There are many types of nodes, but there are three main ones that we work with most often:

Element nodes
Text nodes
Comment nodes
When an HTML element is an item in the DOM, it is referred to as an element node. Any lone text outside of an element is a text node, and an HTML comment is a comment node. In addition to these three node types, the document itself is a document node, which is the root of all other nodes.

The DOM consists of a tree structure of nested nodes, which is often referred to as the DOM tree. You may be familiar with an ancestral family tree, which consists of parents, children, and siblings. The nodes in the DOM are also referred to as parents, children, and siblings, depending on their relation to other nodes.

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
The html element node is the parent node. head and body are siblings, children of html. body contains three child nodes, which are all siblings — the type of node does not change the level at which it is nested.

Modifying the DOM with Events
Up until now, we've only seen how to modify the DOM in the console, which we have seen is temporary; every time the page is refreshed, the changes are lost. In the Introduction to the DOM tutorial, we used the console to update the background color of the body. We can combine what we've learned throughout this tutorial to create an interactive button that does this when clicked.

Let's go back to our index.html file and add a button element with an id. We'll also add a link to a new file in a new js directory js/scripts.js.

Events

An event in JavaScript is an action the user has taken. When the user hovers their mouse over an element, or clicks on an element, or presses a specific key on the keyboard, these are all types of events. In this particular case, we want our button to listen and be ready to perform an action when the user clicks on it. We can do this by adding an event listener to our button.

Create scripts.js and save it in the new js directory. Within the file, we'll first find the button element and assign it to a variable.

screen shot 2017-11-28 at 4 06 21 am

Using the addEventListener() method, we will tell the button to listen for a click, and perform a function once clicked.

button.addEventListener('click', () => {
  // action will go here
});
Finally, inside of the function, we will write the same code from the previous tutorial to change the background color to fuchsia.

let button = document.getElementById('changeBackground');
button.addEventListener('click', () => {
  document.body.style.backgroundColor = 'fuchsia';
});
Recap
In this tutorial, we reviewed terminology that will allow us to understand and modify the DOM. We learned how the DOM is structured as a tree of nodes that will usually be HTML elements, text, or comments, and we created a script that would allow a user to modify a website without having to manually type code into the developer console.
