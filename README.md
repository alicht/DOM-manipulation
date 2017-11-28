
## Objectives: 
-  Explain what the DOM is
-  Explain how the DOM came to be
-  Select DOM elements

### more advanced

-  Explain the DOM: its value and its structure
-  Access DOM Elements using relative selection
-  Access DOM Elements using query selectors
-  Create, Read (access), Update (content and attributes), and Destroy DOM elements

In this lesson, we will discuss the difference between HTML and something new: the Document Object Model. HTML that constructs any website that we visit. In fact, let's learn how we can see the HTML of any site.

### What is the Document Object Model, and how is it different than the HTML for the page?

The best way to understand the Document Object Model, is to see and interact with it. Let's get to it.

1. Open the console

### TELL IT TO ME IN BULLET POINTS
The Document Object Model is a representation of the current view of the browser, and can be manipulated without reloading a page.

The HTML is the text in a file first used to display the page.

### Great, but what does this have to do with Javascript?

Well, with Javascript we can 
-  (1) view a current representation of our Document Object Model. 
-  (2) using Javascript we can  select specific portions of the DOM, manipulate them, and show the changes in a browser window.

## For me to do: 
### 1 Use Javascript to view the current representation of the DOM
Open up your console, type the word `document` and press Enter. You'll get a `#document` returned. Click the Triangle and you'll see the DOM! If you followed along above, you'll see a `head` tag, but no `body` tag. So by typing in `document` it looks like our body tag is gone. The page displays our body as gone. However, if we view page source, the HTML is unchanged. Remember, this is the difference between the DOM (current representation of the page) and the HTML (The initial representation of the page).

### 2 Use Javascript to manipulate our DOM

`document.querySelector('body')`

As you know, the HTML never changes after it is first rendered. Instead, we accessed the Document Object Model, altered the model and that altered the appearance of our web page. This is the same as we did before, but with code. To get the body back, just hit refresh

#### SUMMARY
We learned a lot in this section. This is what we learned.
-  HTML is a markup language used to display content in a browser. When we change the appearance of a webpage, what we are really changing is the Document Object Model, which directly determines the appearance displayed in the browser.
-  We can view and manipulate the Document Object Model by opening our developer tools, but when we do so the HTML is not changed.
-  We can also view our Document Object Model by opening the console and typing in the word document.
-  We can select a specific piece of the DOM by using Javascript, such as `document.querySelector('body')`, and we can also use Javascript to alter our DOM with `document.querySelector('body').remove()`
-  To get your body back, just hit refresh

Next, we'll take a deeper look at how to select elements!

## intro


Think about Gmail for a second. When you're looking at your inbox, there are a MILLION actions you can take. You favorite an email and the star turns yellow without a new page loading. You add a tag to an email and the tag also appears without the page reloading. Even opening an email just replaces the inbox content with the email content without loading a new page. All of this is done using JavaScript. But how was the code able to manipulate the HTML? By using, traversing and manipulating the DOM.

When a web page is loaded, the browser creates a Document Object Model of the page, which is an object oriented representation of an HTML document, that acts as an interface between JavaScript and the document itself and allows the creation of dynamic web pages:

The DOM, which stands for Document Object Model, provides a way of manipulating HTML and XML documents. The DOM provides a structural representation of the document in tree form, enabling you to modify its content and visual presentation by using a scripting language such as JavaScript.

-  JavaScript can add, change, and remove all of the HTML elements and attributes in the page.
-  JavaScript can change all of the CSS styles in the page.
-  JavaScript can react to all of the existing events in the page.
-  JavaScript can create new events within the page.

### Relationship of the HTML to the dom
blueprint => HTML, finished building => DOM
recipe ingredients => HTML, finished dish => DOM


2) The DOM allows you to get content.

3) The DOM allows you to set content.

4) add effects/ animationd turned into the DOM

5) create event listeners

The DOM is an object-oriented representation of the web page, which can be modified with a scripting language such as JavaScript.

#####
Q: is the HTML you write the DOM?
A. not really... but the HTML you write is parsed by the browser and turned into the DOM.



