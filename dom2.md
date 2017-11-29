These methods work fine, but they're often too specific and a bit clunky to work with. Especially if you're looking 
for a node inside a node inside a node. More recently, two new catchall methods have come along to solve pretty much 
all our targeting needs. Query Selector, which returns the first instance that matches the specified selectors, 
and Query Selector All which returns a node list of all elements that match the specified selectors. 
These selectors are one or more comma separated CSS selectors.


A better way of adding new DOM elements is by breaking them into their individual components and adding them to the DOM tree.
-  create the element itself. 
-  create the Text Node that goes inside the element. 
-  Add the Text Node to the element. 
-  Add the element to the DOM tree.

To do this we need 3 new elements:
-  createElement(); 
-  createTextNode(); 
-  appendChild(); // place one child node into another

## What are DOM events?



The formula for building JavaScript functionality around events is called event handling and it typically takes this form.

First, identify the DOM node the interactive behavior will be attached to, for example, a call to action button. 

Second, identify the event you want to detect like click and bind that to the DOM node.

Third, create a function that is triggered when the event fires. A mobile window pops up to cover the screen.

![screen shot 2017-11-29 at 1 10 10 am](https://user-images.githubusercontent.com/6153182/33360534-17a93db0-d4a2-11e7-84c8-bd9313e32fd0.png)

## Next

![screen shot 2017-11-29 at 1 12 00 am](https://user-images.githubusercontent.com/6153182/33360595-605d4f88-d4a2-11e7-9fa7-74feda368b27.png)


![screen shot 2017-11-29 at 1 13 55 am](https://user-images.githubusercontent.com/6153182/33360649-9a1fb0f8-d4a2-11e7-8a31-5519e2b2c825.png)

### css transition events too

More often than not, the things we want to do with JavaScript are associated with some sort of event. The easiest way to connect such an event to a function is to create what's known as an event handler.




