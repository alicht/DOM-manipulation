Introduction

The DOM is an essential part of making websites interactive. It is an interface that allows a programming language to manipulate the content, structure, and style of a website. JavaScript is the client-side scripting language that connects to the DOM in an internet browser.


Almost any time a website performs an action- for example: rotating between a slideshow of images, displaying an error when a user attempts to submit an incomplete form, or toggling a navigation menu, **it is the result of JavaScript accessing and manipulating the DOM**. 

In this section we will learn:
-  what the DOM is 
-  how to work with the document object, 
-  the difference between HTML source code and the DOM.

# So first and foremost... what excatly is the DOM?

At the most basic level, a website consists of an HTML document. The web browser that we use to view the website is a program that interprets HTML and CSS and renders the style, content, and structure into the page that you see.

In addition to parsing the style and structure of the HTML and CSS, the browser **creates a representation of the document known as the Document Object Model**. 

This model allows JavaScript to access the text content and elements of the website document as objects.

## Let's create a very basic `index.html` file and save it

`<!DOCTYPE html>
<html lang="en">

  <head>
    <title>Learning the DOM</title>
  </head>

  <body>
    <h1>Document Object Model</h1>
  </body>

</html>`

