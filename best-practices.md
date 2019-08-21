# Best Practices

This is by no means an exhaustive list, just my key points for implementing React into an existing application.

## Build small

We should aim to build components small, the smallest they can be, but no smaller.


Typically a component will have a single responsibility, even if this responsibility is to hold the state of a form or compose a few components together. You should always look to make your components and your architecture as simple as possible. If what you’re doing feels complex or is extending to hundreds of lines of code then talk to someone and try and find a simpler way.

## Build composable

Our components should all be reusable.

We’re looking to improve our development speed by not duplicating code.
Each component should serve one purpose, but be applicable in many situations.
It is expected that you could take a component from one place and put in another whilst maintaining same functionality.
If the functionality in the new place isn’t the same as an existing component and it doesn’t match what appears to be expected of that component then it may be that you need a new component!

## Build encapsulated

We are aiming for a separation of concerns. The functionality of a component should be encapsulated within the component itself. It shouldn’t have side-effects which manipulate any DOM outside of it’s dependents and should clean up after itself when it is removed (remove event handlers and timers etc).

This improves the reusability of components and allows us to be confident in reusing the component in various situations.

This also makes testing easy either form a black box or white box perspective. If all the functionality is encapsulated and we’re not relying on external code or creating side effects then our code is inherently easier to test.

A React component should take in props and spit out DOM. At that level of simplicity it’s difficult to make testing difficult!

## Build from the bottom up

When refactoring out existing UI start from the smallest component, the bottom of your DOM tree.
This stops you from falling out of sync with master. For example:

```
          [1]
          / \
        [2] [3]
       /    / \
     [4]  [5] [6]
     / \
   [7] [8]
```

Imagine this is your DOM tree. One main element at the top which has several layers of children.
If we want to [...]
