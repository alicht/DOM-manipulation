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



