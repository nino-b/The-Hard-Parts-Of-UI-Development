### Example 1

- WebIDL is the description of the DOM API. DOM API describes how can we access DOM object. It is written in its formalized structure through the interface description language for all web browser features, known as Web IDL.

```html
<input>
<div></div>
<script src="app.js"></script>
```

```js
let post = ""; // Data
const jsInput = document.querySelector('input');
const jsDiv = document.querySelector('div');

function dataToView() { // After view
  jsInput.value = post;
  jsDiv.textContent = post;
}

function handleInput() {
  post = jsInput.value;
  if (post == 'Will') {jsDiv.remove()}
}

jsInput.oninput = handleInput;
```
![](/img/VDOM-1-1.svg)
![](/img/VDOM-1-2.svg)
![](/img/VDOM-1-3.svg)




### Example 2

Everything is dependent on the underlying data and it is funneled through one function - a <b>Component</b>.

Because all user actions end up becoming a state, a function that describes the translation of the data to view is a full description of the entire piece of content.

Its underlying data, all possible conditions for what can be displayed are all captured by the description of the relationship between that state and what the user sees. It also attaches the handlers that pass back the user's action as a submission to change that data.


<b>UI Component</b> - a function that fully creates elements and sets up the data to view relationship. 

It combines everything into one function: creates elements, sets the data content, attaches handlers and describes what the user will see, ties data view handlers to how user can change the underlying data and therefore what they can see, because it reruns the updated view with that new data.


```html
<script src="app.js"></script>
```

```js
let post = ""; let jsInput; let jsDiv;

function dataToView() {
  jsInput = document.createElement('input');
  jsDiv = post == 'Will' ? "" : document.createElement('div');

  jsInput.value = post;
  jsDiv.textContent = post;
  jsInput.oninput = handleInput;

  document.body.replaceChildren(jsInput, jsDiv);
}

function handleInput() {
  post = jsInput.value;
}

setInterval(dataToView, 15);
```

![](/img/VDOM-2-1.svg)
![](/img/VDOM-2-2.svg)



### Example 3

```js
let name = 'Jo';

let textToDisplay = 'Hello, ';
textToDisplay = textToDisplay.concat(name);
textToDisplay = textToDisplay.concat('!');
// 'Hello, Jo!'

// Alternative with template literals
textToDisplay = `Hello, ${name}`
// 'Hello, Jo!'
```
![](/img/VDOM-3.png)



### Example 4

```js
let name = "Jo";
const divInfo = ['div', `Hi, ${name}!`];

function convert(node){
 const elem = document.createElement(node[0]);
 elem.textContent = node[1];
 return elem;
}
const jsDiv = convert(divInfo);
```