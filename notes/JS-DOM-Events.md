<b></b>

### Browser Rendering Process: From HTML Parsing to JavaScript Execution

1. HTML Loading.
2. HTML Parsing and DOM Construction.
3. Rendering.
4. JavaScript Execution.
5. Execution Context and DOM Manipulation.

1. HTML file is loaded in the browser.
2. HTML Parser parses through HTML content and generated DOM tree. Each HTML element is converted into DOM nodes. DOM is implemented in C++ language.
3. After the DOM construction phase, rendering engine computes the layout and renders elements to the screen.
4. After rendering stage is finished, JS execution starts. JS engine parses and executes JS code found in HTML file or linked JS files. JS code execution starts as soon as necessary JS files are loaded.
    - However, the execution of JS code does not necessarily wait for the entire HTML to be parsed. 
    - If we add ```defer``` keyword in the ```<script>``` tag, JS will be loaded asynchronously and executed after HTML has been parsed.
    - If we add ```async``` keyword in the ```<script>``` tag, JS will be loaded and executed asynchronously. It won't wait HTML parsing. Whenever ```<script>``` load is finished, it will be executed, no matter HTML parsing was finished or not.
5. JS engine creates Execution Context and executes JS code. The Execution Context provides access to various APIs, including ```document``` object, which represents DOM. JS code can use the ```document``` object to manipulate the DOM, such as adding or modifying elements, attaching event handlers, etc.
    - As soon as anything changes in DOM, render engine will produce images to the graphics hardware 60 times per second. It is an output of a web browser.

![Browser Rendering Process scheme: From HTML Parsing to JavaScript Execution](/img/rendering.png)


### Terms

- <b>Host defined:</b> Link between queried object and DOM object is called 'host defined'. It means that 'do not anyone else, except us, JavaScript, define where a memory of that will be'.
- <b>Accessor objects:</b> DOM element representations in JS (also called corresponding objects).
- <b>Getter example:</b> '.value' is getter:
```jsInput.value ```
- <b>Setter example:</b> '.textContent' is setter:
```jsDiv.textContent ```