# React is not

## A Templating Language

We all know templating languages like handlebars or smarty. These outline html to be rendered based on data. While on the surface they sound similar to React in that they take properties and output html they are limited to this one dimensional relationship.

In React we care about the view as a whole, not just the HTML template.

## A Framework

Conversely, React isn’t prescriptive on anything. We care about more than the HTML, but React doesn’t prescribe that you use any specific libraries or frameworks for your data structure and it doesn’t provide these itself.

Using react components and data handling tools built to work with React, such as Redux, you can create entire apps with React at it’s core, but React itself isn’t holistic: it requires extending with tools.

## Web Components

React is also very similar to Google’s Polymer project and other implementations of Web Components. I find them to be two sides of the same coin: they can both be used to encapsulate functionality. However Web Components are built on standards within the HTML specification such as shadow DOM, HTML Imports etc whereas React is an extension on browser behaviour using Javascript.

A clear distinction is in how they represent the DOM: Web Components use shadow DOM to encapsulate their functionality, whereas React uses virtual DOM.

---
[So what is React?](/react-is.md)
