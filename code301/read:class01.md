# About React

 **in this note I will talk about these Topics*

1. What is 'React'?

2. What is a component?

3. What are the charactistics of a component?

4. What are the advantages of using component based architecture?

5. What is props short for?

6. How are props used in React?

7. What is the flow of props?

## What is 'React'?

Its a  JavaScript library for building user interfaces

>React has been designed from the start for gradual adoption, and you can use as little or as much React as you need. Whether you want to get a taste of React, add some interactivity to a simple HTML page, or start a complex React-powered app.

## What is a component?

- A component is a modular, portable, replaceable, and reusable set of well-defined functionality that encapsulates its implementation and exporting it as a higher-level interface.
- A component is a software object, intended to interact with other components, encapsulating certain functionality or a set of functionalities. It has an obviously defined interface and conforms to a recommended behavior common to all components within an architecture.
- A software component can be defined as a unit of composition with a contractually specified interface and explicit context dependencies only. That is, a software component can be deployed independently and is subject to composition by third parties.

## What are the charactistics of a component?

1. Reusability:  − Components are usually designed to be reused in different situations in different applications. However, some components may be designed for a specific task.

2. Replaceable:  Components may be freely substituted with other similar components.

3. Not context specific : Components are designed to operate in different environments and contexts.

4. Extensible : A component can be extended from existing components to provide new behavior.

5. Encapsulated : A component depicts the interfaces, which allow the caller to use its functionality, and do not expose details of the internal processes or any internal variables or state.

6. Independent : Components are designed to have minimal dependencies on other components.

## What are the advantages of using component based architecture?

1. Ease of deployment : As new compatible versions become available, it is easier to replace existing versions with no impact on the other components or the system as a whole.

2. Reduced cost :  The use of third-party components allows you to spread the cost of development and maintenance.

3. Ease of development : Components implement well-known interfaces to provide defined functionality, allowing development without impacting other parts of the system.

4. Reusable : The use of reusable components means that they can be used to spread the development and maintenance cost across several applications or systems.

5. Modification of technical complexity : A component modifies the complexity through the use of a component container and its services.

6. Reliability : The overall system reliability increases since the reliability of each individual component enhances the reliability of the whole system via reuse.

7. System maintenance and evolution : Easy to change and update the implementation without affecting the rest of the system.

8. Independent : Independency and flexible connectivity of components. Independent development of components by different group in parallel. Productivity for the software development and future software development.

## What is props short for?

- “Props” is a special keyword in React, which stands for properties and is being used for passing data from one component to another.

>React is a component-based library which divides the UI into little reusable pieces. In some cases, those components need to communicate (send data to each other) and the way to pass data between components is by using props.

## How are props used in React?

I will be explaining how to use Props step by step.

1. Firstly, define an attribute and its value(data)
2. Then pass it to child component(s) by using Props
3. Finally, render the Props Data

so let's start........

you can see below __ParentComponent__ including another component (child):

```JavaScript
class ParentComponent extends Component {  
  render() {
    return (
      <h1>
        I'm the parent component.
        <ChildComponent />
      </h1>
    );
  }
}
```

And this is our ChildComponent:

```JavaScript
const ChildComponent = () => {  
  return <p>I'm the 1st child!</p>; 
};
```

The problem here is that, when we call the ChildComponent multiple times:


```JavaScript
class ParentComponent extends Component {  
  render() {
    return (
      <h1>
        I'm the parent component.
        <ChildComponent />
        <ChildComponent />
        <ChildComponent />
      </h1>
    );
  }
}
```

It always renders the same string again and again:

![Image](https://miro.medium.com/max/1050/1*rzX4l1-rJn4c4_yeqooFbQ.png)

>But what we like to do here is to get dynamic outputs, because each child component may have different data and let’s see how we can solve this issue by using props…

1st Step: Defining Attribute & Data:

We already know that we can assign attributes and values to HTML tags:
    `<a href="www.google.com">Click here to visit Google</a>;`
  Likewise, we can do the same for React components. We can define our own attributes & assign values with interpolation { }: `<ChildComponent someAttribute={value} anotherAttribute={value}/>`
  Here I’m declaring a “text” attribute to the ChildComponent and then assign a string value: “I’m the 1st child”.
  `<ChildComponent text={“I’m the 1st child”} />`
  Now the ChildComponent has a property and a value. Next, we need to pass it via Props.

  2nd Step: Passing Data using Props

  OK, now let’s take the “I’m the 1st child!” string and pass it by using props.

  >Passing props is very simple. Like we pass arguments to a function, we pass props into a React component and props bring all the necessary data.

  Arguments passed to a React component:

  ```JavaScript
  const ChildComponent = (props) => {  
  return <p>I'm the 1st child!</p>; 
};
```

>Props are arguments passed into React components

Final Step: Rendering Props Data

Alright so far, we have created an attribute and its value, then we passed it through props but we still can’t see it because we haven’t rendered it yet.

Prop is an Object

In the final step, we will render the props object by using string interpolation:`{props}`

 In JavaScript, we can access to object elements with dot(.) notation. So, let’s render our text property with interpolation:

 ```JavaScript
 const ChildComponent = (props) => {  
  return <p>{props.text}</p>; 
};
```

and the result will be like this:
![Image1](https://miro.medium.com/max/1050/1*UuipOqB2yPyC1JPB8MTxpQ.png)

And that’s it! We’ve achieved to render the data coming from the parent component.

Before closing, let’s do the same for other child components:

```JavaScript
class ParentComponent extends Component {  
  render() {
    return (
      <h1>
        I'm the parent component.
        <ChildComponent text={"I'm the 1st child"} />
        <ChildComponent text={"I'm the 2nd child"} />
        <ChildComponent text={"I'm the 3rd child"} />
      </h1>
    );
  }
}
```

![Image3](https://miro.medium.com/max/1050/1*Kd52H-jKv6N1Cwgnaz4tOA.png)

>As we can see, each ChildComponent renders now its own prop data. So this is how we can use Props for passing data and converting static components into dynamic ones.














- 
