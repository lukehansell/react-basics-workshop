# React and JSX

You can use JSX with React, but remember React is not JSX and JSX is not React. When you compile your code the JSX gets parsed down to React classes and methods in vanilla javascript. JSX allows us to declaratively represent our DOM tree within our React components.

You can write react without JSX, and it looks like this ->


```js
import React from “react”

const Component = () => {
  return React.createElement(
    ‘h1’,
    null,
    ‘Hello World’
  )
}

ReactDOM.render(
  React.createElement(Component, null, null),
  document.body
)
```

However, this will soon get very complicated when working with nested components, so is probably best to avoid!
When Babel can transpile to this anyway and JSX gives you such a nice and familiar declarative interface why cut off your nose to spite your face?

---

Now let's look at [passing data around React apps](/props.md)
