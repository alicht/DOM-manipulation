# Part 2


# The Dom Tree

### The document itself is a document node, which is the root of all other nodes.


The DOM consists of a tree structure of nested nodes, which is often referred to as the DOM tree. 
You may be familiar with an ancestral family tree, which consists of parents, children, and siblings. The nodes in the DOM are also referred to as parents, children, and siblings, depending on their relation to other nodes.

### To do:

```html
<!doctype html>
<html>
  <head>
    <title>My home page</title>
  </head>
  <body>
    <h1>My home page</h1>
    <p>Hello, I am (your name) and this is my home page.</p>
    <p>Also, I'm really cool!
      <a href="http://coolperson.com"> see here</a></p>
  </body>
</html>
```

# Moving on

Let's use that basic HTML that we created a moment ago

##### The simplest way to access an element with JavaScript is by the id attribute (we'll talk more about this shortly). Let's add a nav id to our HTML.

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

``` html
<a id="nav" href="index.html">Home</a>
```

We have retrieved the entire element using `getElementById()`. Now, instead of typing that object and method every time we want to access nav link, we can store it into a variable.

``` javascript
let navLink = document.getElementById('nav');
```

Now, we can easily modify attributes and values. For example, we can change where the link goes by changing the href attribute:

`navLink.href = 'https://www.wikipedia.org';`

We can also change the text content by reassigning the textContent property:

``` javascript
navLink.textContent = 'Navigate to Wikipedia';
``` 

``` javascript
navLink;
``` 
``` html
<a id="nav" href="https://www.wikipedia.org/">Navigate to Wikipedia</a>
```

This is also reflected on the front-end of the website.

![screen shot 2017-11-28 at 3 39 43 am](https://user-images.githubusercontent.com/6153182/33309909-d2cba2c8-d3ed-11e7-988d-c6ba0b0f11e9.png)

### however...
Refreshing the page will revert everything back to their original values. :/ :/ :/



## Events
An event in JavaScript is an action the user has taken. 
Examples:
-  when the user hovers their mouse over an element
-  clicks on an element
-  or presses a specific key on the keyboard
-  key up/ key down



# Modifying the DOM with Events
Up until now, we've only seen how to modify the DOM in the console, which we see is temporary- every time the page is refreshed our changes are lost. Let's instead create a button on our web page that does this for us when clicked.

Let's go back to our `index.html` file and create a `button` element with an id. 
```html
<button id ="changeBackground">Change Background Color</button>
```

We'll also need to create a `script.js` file.


#### Next
In our `script.js` file, we'll first find the `button` element and assign it to a variable.

in our `scripts.js` create a button function. (help please!)


#### Next

Using the `addEventListener()` method, we will tell the button to listen for a click, and perform a function once clicked.

``` javascript
button.addEventListener('click', () => {
  // action will go here
});
```

Finally, inside of the function, we will write the same code from the previous tutorial to change the background color to indigo.

``` javascript
let button = document.getElementById('changeBackground');
button.addEventListener('click', () => {
  document.body.style.backgroundColor = 'indigo';
});
```

# Recap

We learned how the DOM is structured as a tree of nodes.

We reviewed terminology that will allow us to understand and modify the DOM. 

We created a script that would allow a user to modify a website without having to manually type code into the developer console.
