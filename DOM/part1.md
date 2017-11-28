
# Part 1
Objectives:
-  define the DOM/ what the DOM is
-  access the `document` object and update a property on it
-  Differenciate difference between HTML source code and the DOM.



### Introduction

The DOM is an essential part of making websites interactive. It is an interface that allows JavaScript to manipulate the content, structure, and style of a website. 


Almost any time a website performs an action- for example: rotating between a slideshow of images, displaying an error when a user attempts to submit an incomplete form, or toggling a navigation menu, **it is the result of JavaScript accessing and manipulating the DOM**. 


## So first and foremost... what exactly is the DOM?

At its most basic level, a website consists of an HTML document. The web browser that we use to view the website is a program that interprets HTML and CSS and renders the style, content, and structure into the page that you see.

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

Within Chrome, open up index.html. You'll see a plain website with our heading saying "Document Object Model". Right click and hit  "Inspect" to open up the Developer Tools.

### let's go to the DOM

let's type `document` in our console tools and let's see what happens

![screen shot 2017-11-28 at 3 12 45 am](https://user-images.githubusercontent.com/6153182/33308836-1659a0a2-d3ea-11e7-917e-d8ba7d0853c7.png)

Typing document and otherwise working directly in the console is not something that you'll generally ever do outside of debugging, but it helps solidify exactly what the document object is and how to modify it, as we will discover below.


## What is the difference between the DOM and HTML Source Code? (ie they seem to be exactly the same)

A: the DOM can be modified by client side JS whereas HTML source code cannot.

##### Let's show this

Entering `document.body` 

will return

```html
<body>
  <h1>Document Object Model</h1>
</body>
```

In our console, we can change some of the live properties of this body. Let's edit the style attribute, and changing the background color to indigo. Type this into the console:

`document.body.style.backgroundColor = 'indigo';`

After typing and submitting the above code, you'll see our live update to the site, as the background color changes.


Switching to the Elements tab, or typing document.body into the console again, you will see that the DOM has changed.

```html
<body style="background-color: indigo;">
  <h1>Document Object Model</h1>
</body>
```

The JavaScript code we typed, assigning fuchsia to the background color of the body, is now a part of the DOM.

However click on the "Sources" tab. You'll notice  the source of the website does not contain the new style attribute we added via JavaScript! 

### Major key
The source of a website will not change and will never be affected by client-side JavaScript. If you refresh the page, the new code we added in the console will disappear.

### Conclusion
We defined the DOM, accessed the `document` object, and used JavaScript and the console to update a property of the document object, and went over the difference between HTML source code and the DOM.
