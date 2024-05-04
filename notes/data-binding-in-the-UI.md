### Example 1

```html
<input>
<div></div>
<script src="app.js"></script>
```

```js
let post = "";
const jsInput = document.querySelector('input');
const jsDiv = document.querySelector('div');
jsInput.value = "What's up?";

function handleInput() {
    post = jsInput.value; //getter
    jsdev.textContent = post; //setter
}

function handleClick() {
  jsInput.value = '';
}
jsInput.oninput = handleInput;
jsInput.onclick = handleClick;
```
![](/img/example-2.svg)





### Example 2

There should be no content that user sees that is not traceable back to the data in JavaScript. This guarantees us to know what is displaying on the page. This is also called <b>State-Driven Views</b>.

```html
<input>
<div></div>
<script src="app.js"></script>
```

```js
let post = undefined;
const jsInput = document.querySelector('input');
const jsDiv = document.querySelector('div');

function dataToView() {
  jsInput.value = 
    post == undefined ? "What's up?" : post;
    jsDiv.textContent = post;
}

function handleClick() {
  post = '';
  dataToView();
}

function handleInput() {
  post = jsInput.value;
  dataToView();
}

jsInput.onclick = handleClick;
jsInput.oninput = handleInput;
dataToView();
```
![](/img/ex-2_1.svg)