# handlebars-virtual-dom
> Compile Handlebars templates to [virtual-dom](https://github.com/Matt-Esch/virtual-dom/) (Node.js)

Compile this:
```handlebars
<div>
	value1
	{{variable1}}
	{{#if variable2}}<span>value2</span>{{else}}nothing{{/if}}
	<span data-attr="{{#if variable3}}value3{{/if}} value4">value5</span>
</div>
```
into this:
```js
h("div", [
	"value1",
	this.props.variable1,
	this.props.variable2 ? h("span", [
		"value2"
	]) : "nothing",
	h("span", {"data-attr":(this.props.variable3 ? "value3" : "") + " value4"}, [
		"value5"
	])
);
```

## Usage
### Server/Browserify
```js
var handlebarsVirtualDom = require("handlebars-virtual-dom");
var result = new handlebarsVirtualDom(options).compile("<h1>{{title}}</h1>");
```
### AMD/etc
Accessible via `define()` or `windows.handlebarsVirtualDom`.

## Options
See [handlebars-html-parser](https://github.com/stevenvachon/handlebars-html-parser).

