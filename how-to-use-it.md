# How to use it

## ~Using `createClass`~ _(deprecated)_

```js
import React from “react”

const Component = React.createClass({
  render() {
    return (
      <h1>Hello World</h1>
    )
  }
})

ReactDOM.render(<Component />, document.body)
```

This is the basic outline of a component as they were originally written using the createClass method.

I’m not going to talk about this method any further because we shouldn’t be using React that is this old. If you see it, refactor it out.


## Using `class` Components

```js
import React from “react”

class Component extends React.Component {
  render() {
    return (
      <h1>Component</h1>
    )
  }
}

ReactDOM.render(<Component />, document.body)
```

Here is the same using the Javascript class structure.
When React was first developed this wasn’t publicly available. This came as a result of updates.


## Using Functional Components <-- preferred method

```js
import React from “react”

const Component = () => {
  return (
    <h1>Hello World</h1>
  )
}

ReactDOM.render(<Component />, document.body)
```

Here is the same component written as a functional component.

Why is this the preferred method? Well you'll see when we look at `props` that these act as pure functions which make your code easier to comprehend.
For a _stateless_ functional component, given the same `props` you will always receive the same output.

As you can see, in each of these implementations we're using JSX the `<h1>` tags. Let's talk a little about that.

---

[How does React use JSX?](/react-and-JSX.md)
