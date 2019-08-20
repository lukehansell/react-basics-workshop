# React is

## Just the UI

React cares specifically about what is to be rendered. A key concept of React is that “UI is a representation of state”. When you render a component you are communicating your apps current state. We pass props to component which encapsulate a moment in time within the app and we return HTML which represents that moment.

By using a declarative representation of components and properties we can easily compose components to represent the state of an entire system and hence build entire apps.

## Virtual DOM

React holds two states of DOM internally: the previous state’s DOM (what is currently Rendered) and the current state’s DOM (what should be rendered). Using these two DOM representations and a very clever diffing algorithm React generates a series of DOM mutators to change the previous state’s DOM into the current state’s expected DOM. It then applies these mutators to the actual DOM in the browser. This way React only ever affects DOM that has changed. This provides a performance boost when re-rendering between states when compared to other similar libraries.

## Data Flow

Whilst React is non-prescriptive on many things it is prescriptive on a unidirectional data flow. What this means is that a parent component can talk to a child component (via props) but a child cannot talk back to it’s parent. All the functionality that a component requires should be encapsulated inside of the component. The props supported dictate a specific integration which a parent must abide by to communicate with the child.

A parent may pass as a property a function for the child to call, but the child cannot directly manipulate the parent.

Consider an incremental click counter. The parent would hold the state of how many times the button had been clicked and would pass this to the component as the value of the state to be rendered. The parent could also pass an onChange handler which the click counter component would decide how and when to call. When the child is clicked it would call this onChange handler with the new value. The parent then stores the new value and again sends it back to the child as the new state to be rendered.

---
[So how do I use it?](/how-to-use-it.md)
