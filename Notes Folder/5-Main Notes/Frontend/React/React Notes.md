---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - "#react"
  - "#webdev"
excalidraw-open-md: true
---
# [[React Notes]]

![[React Notes.svg]]


```jsx
ReactDOM.render(<h1>Hello, everyone </h1>, documentGetElementById("root"))
```

JSX -> JavaScript XML; It's a flavour of JavaScript that looks really similar to html. It's one of the main factors contributing to making react a declarative language instead of an imperative one.

It's similar to a function which when run will create a JavaScript object which the computer can understand 

![[jsx-to-js_object.png]]


The html can be saved as a page which can then be rendered via ReactDOM

```JSX
import React from "react" //defines the jsx syntax (not required anymore)
import ReactDOM from "react-dom" //defines the variable ReactDOM used to render the pages
const page =(
	<div>
		<h1>This is the title</h1>
		<p>This is the paragraph</p>
	</div>
)
ReactDOM.render(
	page,
	document.getElementById("root")
)
```

Challenge: Try to create a navigation bar (use d as the parent wrapper)there should be a header element and an unordered list with 3 list items

```JSX
const navbar = (
	<nav>
		<h1>Title</h1>
		<ul>
			<li>Pricing</li>
			<li>About</li>
			<li>Contact</li>
		</ul>	
	</nav>
)

ReactDOM.render(
	nav,
	document.getElementById("root")
)
```


Reminder: JSX will always return a JavaScript object which can be seen by using append and JSON.stringify. Only when we try to render a JSX using the ReactDOM.render method does the object be converted to the visuals we can see(something that can be interpreted by the browser).
```JSX
const page = (
	<>
		<nav>
			<ul>
				<li>Home</li>
				<li>About</li>
				<li>Contact</li>
			</ul>
		</nav>
		<div>
			<h1>This is the main title of the page</h1>
			<p>This section provides a brief description about the page</p>
		</div>
	</>
)

document.getElementById("root").append(page)
document.getElementById("root").append(JSON.stringify(page))

```

![[append_instead_of_ReactDom.png]] 
![[stringifyJSON.png]]



```JSX
function Reasons(){
	return(
		<>
			<div>
				<p>This is the paragraph</p>
			</div>
		</>
	)
}

ReactDOM.render(<Reasons />, document.getElementById("root"))
```


Components can be added to a function to keep calling them whenever required and they can then be added to different files to be imported and exported to improve readability and maintainability.

### Conventions to follow
- File name for components should have the same name and capitalisation as the header 
- Don't use camel case for component names but instead use Pascal-Case where the first letter is also capitalised




how props work and how to map data using the javascript function .map
![[Pasted image 20250115134212.png]]


![[Pasted image 20250115134232.png]]


**Can also be done like this**
![[Pasted image 20250115134611.png]]

![[Pasted image 20250115134642.png]]
## Drawing
```compressed-json
N4IgLgngDgpiBcIYA8DGBDANgSwCYCd0B3EAGhADcZ8BnbAewDsEAmcm+gV31TkQAswYKDXgB6MQHNsYfpwBGAOlT0AtmIBeNCtlQbs6RmPry6uA4wC0KDDgLFLUTJ2lH8MTDHQ0YNMWHRJMRZFADZFAHYyJE9VGEYwGgQAbQBdcnQoKABlALA+UEl8PGzsDT5GTkxMch0YIgAhdFQAayKuRlwAYXpMenwEEABiADMx8ZAAX0mgA
```
%%

