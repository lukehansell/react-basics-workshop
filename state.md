# State

State allows you to keep track of changes within a component. It is held internally within a component. It is not usually exposed to parent components, but can be used as props for child component.
You should at all times attempt to keep your components stateless. If state is required then most of the time it should be represented as a prop from the parent.

By pushing the state as far up the dependency tree as possible you can simplify the reasoning required to understand where data comes from and reduce the risk of multiple sources of truth.

A good practice is to separate state logic from presentation logic and wrap you presentational components in stateful ones. I’ll discuss this later.

There are certain things that shouldn’t go in state: 
- computed data: you should always compute this at the time required, never store this in state as it may become out of date.
- react components: it’s not considered good practice to store these in state.
- duplicates from props: this is perhaps the most important. NEVER store props in state. Not only will this cause two re-renders when the prop changes (changing props causes a re-render and changing state causes a re-render) but it duplicates the source of truth.

## State in classes

```js
class ClickCount extends React.Component {
  constructor(props) {
    super(props)
    
    // setting the default state
    this.state = {
      clickCount: 0  
    }
  }
  
  handleClick = () => {
  
    // modifying the state
    this.setState((currentState) => {
      return {
        clickCount: clickCount + 1
      }
    }
  }
  
  render() {
  
    // reading the state
    const { clickCount } = this.state
    
    return (
      <> // shorthand for <React.Fragment>
        <button onClick={this.handleClick}>click me</button>
        <span>Button was clicked {clickCount}</span>
      </>
    )
    
  }
}

```

State is mutable, you can change it within your component. But to do so you should always use `this.setState(...)`.
**Never** change state directly via `this.state.name = 'Barney'` as this will circumvent the lifecycle methods which allow a component to update on state changes.

### Best practices

#### Pass `setState` a function.
The first argument for this function is the current state object.
When modifying state as above it's often a good idea to use this as it is the most recent version of the state.
Otherwise state changes that are happening asynchronously may not yet be reflected within your component.

#### Separate state logic from presentation
In order to simplify the rendering of your state and to make your components more re-usable you should separate out your presentation logic from your stateful logic.

```js
class ClickCounter extends Component {
  constructor(props) {
    super(props)
    
    this.state = {
      clickCount: 0
    }
  }
  
  handleCountIncrement = () => {
    this.setState(({ clickCount }) => {
      clickCount: clickCount + 1
    })
  }
  
  render() {
    const { children } = this.props
    const { clickCount } = this.state
    
    return (
      <>
        children( {
          count:
          onClick: handleClickCount
        })
      </>
    )
  }
}

const ButtonClicker = ({
  count,
  onClick
}) => {
  return (
    <button onClick={onClick}>Clicked {count} times</button>
  )
}


const ClickCounterButton = () => {
  return (
    <ClickCounter>
      {({
        count,
        onClick
      }) => {
        return (
          <ButtonClicker count={count} onClick={onClick} />
        )
      }
    </ClickCounter>
  )
}
```

The above uses the render prop pattern. There are other ways to achieve this, such as higher order components.
Each of these separates the logic from what is rendered meaning the the Button component and the ClickCounter components can both be used elsewhere independently and are not tied to each others implementation.

## State in functional components

Functional components have historically not catered for instances where state is required, relying instead on other components to manage this and pass it in as props.
However, with `hooks`, these components now have access to stateful structures.

```js

import React, { useState } from 'react'

const ClickCounterButton = () => {

  const [count, setCount] = useState(0)
  
  const onClickHandler = () => {
    setCount(count+1)
  }
  
  return (
    <button onClick={onClickHandler}>Click count: {count}</button>
  )
  
}

```

This allows you to use functional components for most use cases.

For more information about React Hooks and the problems they solve check out [this post by Tyler McGinnis](https://tylermcginnis.com/why-react-hooks).
For more information on the component lifecycle (for class components) check out the [documentation](https://reactjs.org/docs/react-component.html#the-component-lifecycle).

---

Now that you know how to build components, what are the [best practices for implementing them in your projects?](/best-practices.md)
