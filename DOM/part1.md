
Part 1
Introduction

The DOM is an essential part of making websites interactive. It is an interface that allows a programming language to manipulate the content, structure, and style of a website. JavaScript is the client-side scripting language that connects to the DOM in an internet browser.

Almost any time a website performs an action- for example: rotating between a slideshow of images, displaying an error when a user attempts to submit an incomplete form, or toggling a navigation menu, it is the result of JavaScript accessing and manipulating the DOM.

In this section we will learn:

what the DOM is
how to work with the document object,
the difference between HTML source code and the DOM.
So first and foremost... what excatly is the DOM?

At the most basic level, a website consists of an HTML document. The web browser that we use to view the website is a program that interprets HTML and CSS and renders the style, content, and structure into the page that you see.

In addition to parsing the style and structure of the HTML and CSS, the browser creates a representation of the document known as the Document Object Model.

This model allows JavaScript to access the text content and elements of the website document as objects.

Let's create a very basic index.html file and save it

<!DOCTYPE html>
<html lang="en">

  <head>
    <title>Learning the DOM</title>
  </head>

  <body>
    <h1>Document Object Model</h1>
  </body>

</html>
Within Chrome, open up index.html. You'll see a plain website with our heading saying "Document Object Model". Right click anywhere on the page and select "Inspect". This will open up Developer Tools.

let's go to the DOM

let's type document in our console tools and let's see what happens

screen shot 2017-11-28 at 3 12 45 am

Typing document and otherwise working directly in the console is not something that you'll generally ever do outside of debugging, but it helps solidify exactly what the document object is and how to modify it, as we will discover below.

What is the Difference Between the DOM and HTML Source Code? (ie they seem to be exactly the same)

A: the DOM can be modified by client side JS whereas HTML source code cannot.

Let's show this

document.body

will return

<body>
  <h1>Document Object Model</h1>
</body>
In the console, we can change some of the live properties of the body object on this website. We'll edit the style attribute, changing the background color to fuchsia. Type this into the console:

document.body.style.backgroundColor = 'fuchsia';

After typing and submitting the above code, you'll see the live update to the site, as the background color changes.

add image here

Switching to the Elements tab, or typing document.body into the console again, you will see that the DOM has changed.

<body style="background-color: fuchsia;">
  <h1>Document Object Model</h1>
</body>
The JavaScript code we typed, assigning fuchsia to the background color of the body, is now a part of the DOM.

However, right click on the page and select "View Page Source". You will notice that the source of the website does not contain the new style attribute we added via JavaScript. The source of a website will not change and will never be affected by client-side JavaScript. If you refresh the page, the new code we added in the console will disappear.

Conclusion

In this tutorial, we defined the DOM, accessed the document object, used JavaScript and the console to update a property of the document object, and went over the difference between HTML source code and the DOM.
