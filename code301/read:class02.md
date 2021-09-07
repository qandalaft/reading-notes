# I will discuss these Main  Topics in this read.

1. Component Lifecycle Events in React

2. What's the difference between props and state in React?

* React lets you define components as classes or functions. The methods that you are able to use on these are called lifecycle events. These methods can be called during the lifecycle of a component, and they allow you to update the UI and application states.
like :-
![image1](https://miro.medium.com/max/2000/0*0saPKFiTUk6W3FYp)

>Mounting, Updating, and Unmounting are the three phases of the component lifecycle.

**Mounting*

When an instance of a component is being created and inserted into the DOM it occurs during the mounting phase. Constructor, static getDerivedStateFromProps, render, componentDidMount, and UNSAFE_componentWillMount all occur in this order during mounting.

**Updating*

Anytime a component is updated or state changes then it is rerendered. These lifecycle events happen during updating in this order.

**Unmounting*

The final phase of the lifecycle if called when a component is being removed from the DOM. componentWillUnmount is the only lifecycle event during this phase.

**constructor()*
The constructor for a React component is called before it is mounted.If the component is a subclass you should call super(props), or the props will be undefined. constructors can be used to assign state using this.state or to bind event handle methods to an instance. Let’s take a look at some example code.

```JavaScript
class FishTableRow extends React.Component {
constructor() {
super(props); //gives us access to props
//Don’t call this.setState() here
this.state = { //intitialize local state
showDescription: false
}; }
```

>Avoid using this.setState() in the constructor because it can lead to side effects, and it is unnecessary. Doing this will ignore all updates to props, so it shouldn’t be done unless it is intentional.


* Let's compare props and state. Here's a definition of each:

1. "props" (short for "properties") is an object of arbitrary inputs a React function component accepts as the first argument.

2. "state" is data that changes over the lifetime of a specific instance of a React component..

Let's dive into each.

__Props__

Think of props as arguments to a function. React components are functions which return JSX (or more generally something that's renderable like React elements, null, a string, etc.). Typically when you have a piece of code that you would like to reuse, you can place that code into a function and any dynamic values that code used before can be accepted as arguments (for example const five = 2 + 3 could be extracted to a function and accept arguments like so const five = `add(2, 3)).`

The same is true of a piece of JSX, except instead of calling it like a normal function (add(2, 3)) you use JSX syntax `(<Add n1={2} n2={3} />).` The "attributes" supplied in the JSX are what are called props and they are placed together in a single object and passed to the Add component function as the first argument like so:
```JavaScript
function Add(props) {
  return (
    <div>
      {props.n1} + {props.n2} = {props.n1 + props.n2}
    </div>
  )
}
```
If I were to use this like so: `<Add n1={2} n2={3} />`
Here's how that would be rendered: 2 + 3 = 5

>NOTE: Props can be anything. In our example they're numbers, but they can also be (and often are) strings, arrays, objects, functions, etc.

Let's say we want to default the n2 to 0 in the event someone doesn't provide it `(like <Add n1={2} />).` One limit to props is that you're not allowed to change them. So you couldn't do something like this:
```JavaScript
function Add(props) {
  if (typeof props.n2 === 'undefined') {
    props.n2 = 0
  }
  return (
    <div>
      {props.n1} + {props.n2} = {props.n1 + props.n2}
    </div>
  )
}
```
If we try to do this, we'll get the following error:`TypeError: Cannot add property n2, object is not extensible`

This is simple enough to solve though:
```JavaScript
function Add(props) {
  let n2 = props.n2
  if (typeof n2 === 'undefined') {
    n2 = 0
  }
  return (
    <div>
      {props.n1} + {n2} = {props.n1 + n2}
    </div>
  )
}
```
Or, often, you'll find people use destructuring syntax with default values as well (this is my personal preference):
```JavaScript
function Add({n1, n2 = 0}) {
  return (
    <div>
      {n1} + {n2} = {n1 + n2}
    </div>
  )
}
```

__State__

State is data that changes over time, and that's perfect for our situation:

```JavaScript
function AddWithInput(props) {
  const [n2, setN2] = React.useState(0)
  function handleInputChange(event) {
    const input = event.target
    const newN2 = Number(input.value)
    setN2(newN2)
  }
  return (
    <div>
      {props.n1} +{' '}
      <input type="number" value={n2} onChange={handleInputChange} /> ={' '}
      {props.n1 + n2}
    </div>
  )
}
```

That will work, and this is precisely what React state is intended to be used for. It's intended to track data values over the lifetime of the component (so long as the component exists on the page).

However, users of the AddWithInput component can no longer set the initial value of n2 anymore. With the way that component is implemented currently, it's not referencing props.n2 at all. But we can make this work by using props when we initialize our state:

```JavaScript
function AddWithInput(props) {
  const [n2, setN2] = React.useState(props.n2)
  // ... etc...
}
```
So our props are "arguments" or "inputs" that we can pass to a component, and state is something that is managed within the component and can change over time.

Let me just clean this component up a little bit and I'll explain my changes:
```JavaScript
function AddWithInput({n1, initialN2 = 0}) {
  const [n2, setN2] = React.useState(initialN2)
  function handleInputChange(event) {
    const input = event.target
    const newN2 = Number(input.value)
    setN2(newN2)
  }
  return (
    <div>
      {n1} + <input type="number" value={n2} onChange={handleInputChange} /> ={' '}
      {n1 + n2}
    </div>
  )
}
```
I changed to destructuring with defaults for the props, and I changed the prop from n2 to initialN2. When I'm using a prop value to initialize a state value, I typically like to give it the prefix initial to communicate that changes in that prop will not be taken into account. If that's what you want, then you'll want to Lift State Up.






















