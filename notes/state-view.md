## HTML code

1. HTML code will be loaded in the browser.
2. Parsed.
3. Turned into the elements of an object. It will be written in C++. This object is a model of a page (document) - DOM. Elements are called nodes. 
4. That list of elements will be converted and displayed on the screen by layout and render engine.


The output of the render engine is an image, a bitmap image of that particular view, that screen pinged out to the graphics card every 16 milliseconds, 60 times per second.


### WebCore

A set of technologies that do the job of storing a list of elements in C++ to be loaded on the page, and then converting that list into actual pixels.


### CSSOM

DOM also includes link to the CSS stylesheet which will turn on CSS engine.

1. The browser's CSS parser will read CSS code.
2. It will create an object in C++. That object will have two parts: 
    1. Rule Set: contains CSS rules defined in stylesheet.
    2. DOM Mirror: contains mirror of DOM structure. It allows browser to efficiently apply styles to the DOM elements.
3. Once the CSS rules are parsed and the DOM is constructed, the browser's rendering engine applies te styles to the DOM elements.



### Changing data

- Parser runs only one-time through HTML. So with HTML we have one-time addition to the DOM.
- User interaction with page it is reflected in DOM. E.g. when user writes in ```<input>```, in the DOM the ```<input>``` element's value changes from an empty string, to whatever user wrote.
- We can't write code that will manipulate user input, in C++ in the browser directly. We have to use JS for that.
- Data / state / content all are underlying things that we're trying to represent as pixels on the page.