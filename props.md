# Props

I’ve [previously mentioned](/react-is.md#data-flow) props, these are how parent components talk to child components.

## Passing data to components

```js
<Component
  id="foo"
  images={["bar.png", "baz.png"]}
  onImageClick={() => alert(‘I was clicked!’)}  
/>
```

Essentially props look like what you currently pass to HTML elements in a HTML document.
They are a method of telling the component something.
Props are **immutable** in the child and should not be modified from within a component.
When the props for a component change React re-renders the child component to represent new data represented in the props.
They are the ultimate source of truth for a component.

You shouldn’t attempt to modify props, nor should you store them in [state](/state) to do so.
If you want the prop to change you have to provide a method from the parent to change the state in the parent component which will then be passed as a property to the child which will cause the re-render.
This prevents a duplication of the source of truth and the potential issues that this causes.

## Reading Props

```js
class Component extends React.Component {

  render() {
    const { name } = this.props
    
    return (
      <h1>Hello {name}</h1>
    )
  }

}
```

Within class components the props are set as an object accessible on an component instance through `this`.

```js
const Component = (props) => {
  
  const { name } = props
    return (
      <h1>Hello {name}</h1>
    )

}

```

In functional components the props are passed as the first argument. You can use desructuring to define the individual props in your function declaration like so:

```js
const Component = ({
  name
}) => {

  return (
    <h1>Hello {name}</h1>
  )

}

```

There is a tradeoff here between readability and code brevity.

## Defining defaults

While a component can’t change the props, it can specify what to use if we don’t receive a prop we expect: we can have default props. Think of this like a login for saying “hello Guest” until it knows your name.

```js
class Component extends React.Component {

  static defaultProps {
    name: "World"
  }

  render() {
    return (
      <h1>Hello {name}</h1>
    )
  }

}
```

In a class component you can define a static attribute for the props.

```js
const Component = (props) => {
  const { name } = props
  
  return (
    <h1>Hello {name}</h1>
  )
}

Component.defaultProps = {
  name: "World"
}
```

In functional components you define it as an attribute on the function. Which I believe can make it easy to overlook.

```js
const Component = ({
  name = 'World'
}) => {

  return (
    <h1>Hello {name}</h1>
  )
  
}
```

Or you can define it in your destructuring either in your function declaration or within your function body.
Doing it within the function body will make debugging easier.

---

So that covers passing data down, but this doesn't allow us to track changes to data. For that we have to use [state](/state).
