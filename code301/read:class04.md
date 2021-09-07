# Today I will discuss the following Topics:-

1. Forms
2. The Conditional (Ternary) Operator Explained

* HTML form elements work a bit differently from other DOM elements in React, because form elements naturally keep some internal state. For example, this form in plain HTML accepts a single name:


```JavaScript
<form>
  <label>
    Name:
    <input type="text" name="name" />
  </label>
  <input type="submit" value="Submit" />
</form>
```

This form has the default HTML form behavior of browsing to a new page when the user submits the form. If you want this behavior in React, it just works. But in most cases, it’s convenient to have a JavaScript function that handles the submission of the form and has access to the data that the user entered into the form. The standard way to achieve this is with a technique called “controlled components”.

Now What it Controlled Components?

In HTML, form elements such as `<input>, <textarea>`, and `<select>` typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with `setState().`


We can combine the two by making the React state be the “single source of truth”. Then the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a “controlled component”.

For example, if we want to make the previous example log the name when it is submitted, we can write the form as a controlled component:

```JavaScript
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```


Since the value attribute is set on our form element, the displayed value will always be `this.state.value`, making the React state the source of truth. Since handleChange runs on every keystroke to update the React state, the displayed value will update as the user types.


With a controlled component, the input’s value is always driven by the React state. While this means you have to type a bit more code, you can now pass the value to other UI elements too, or reset it from other event handlers.


The textarea Tag

In HTML, a `<textarea>` element defines its text by its children:

```JavaScript
<textarea>
  Hello there, this is some text in a text area
</textarea>
```

In React, a `<textarea>` uses a value attribute instead. This way, a form using a `<textarea>` can be written very similarly to a form that uses a single-line input:

```JavaScript
class EssayForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 'Please write an essay about your favorite DOM element.'
    };

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('An essay was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Essay:
          <textarea value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

Notice that `this.state.value` is initialized in the constructor, so that the text area starts off with some text in it.

__The select Tag__

In HTML, `<select>`creates a drop-down list. For example, this HTML creates a drop-down list of flavors:

```html
<select>
  <option value="grapefruit">Grapefruit</option>
  <option value="lime">Lime</option>
  <option selected value="coconut">Coconut</option>
  <option value="mango">Mango</option>
</select>
```
Note that the Coconut option is initially selected, because of the selected attribute. React, instead of using this selected attribute, uses a value attribute on the root select tag. This is more convenient in a controlled component because you only need to update it in one place. For example:

```JavaScript
class FlavorForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: 'coconut'};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('Your favorite flavor is: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Pick your favorite flavor:
          <select value={this.state.value} onChange={this.handleChange}>
            <option value="grapefruit">Grapefruit</option>
            <option value="lime">Lime</option>
            <option value="coconut">Coconut</option>
            <option value="mango">Mango</option>
          </select>
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```


Overall, this makes it so that `<input type="text">`, `<textarea>`, and `<select>` all work very similarly - they all accept a value attribute that you can use to implement a controlled component.

>Note

You can pass an array into the value attribute, allowing you to select multiple options in a select tag:

`<select multiple={true} value={['B', 'C']}>`

__The file input Tag:__

In HTML, an `<input type="file">` lets the user choose one or more files from their device storage to be uploaded to a server or manipulated by JavaScript via the File API.

`<input type="file" />`

Because its value is read-only, it is an uncontrolled component in React. It is discussed together with other uncontrolled components later in the documentation.

__Handling Multiple Inputs__

When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of event.target.name.

For example:

```JavaScript
class Reservation extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isGoing: true,
      numberOfGuests: 2
    };

    this.handleInputChange = this.handleInputChange.bind(this);
  }

  handleInputChange(event) {
    const target = event.target;
    const value = target.type === 'checkbox' ? target.checked : target.value;
    const name = target.name;

    this.setState({
      [name]: value
    });
  }

  render() {
    return (
      <form>
        <label>
          Is going:
          <input
            name="isGoing"
            type="checkbox"
            checked={this.state.isGoing}
            onChange={this.handleInputChange} />
        </label>
        <br />
        <label>
          Number of guests:
          <input
            name="numberOfGuests"
            type="number"
            value={this.state.numberOfGuests}
            onChange={this.handleInputChange} />
        </label>
      </form>
    );
  }
}
```
Note how we used the ES6 computed property name syntax to update the state key corresponding to the given input name:

```JavaScript
this.setState({
  [name]: value
});
```
It is equivalent to this ES5 code:
```JavaScript
var partialState = {};
partialState[name] = value;
this.setState(partialState);
```
Also, since setState() automatically merges a partial state into the current state, we only needed to call it with the changed parts.



* __Starting With the Basics — The if statement__

Using a conditional, like an `if` statement, allows us to specify that a certain block of code should be executed `if` a certain condition is met.

We have a `person` object that consists of a `name`, `age,` and `driver` property.

```JavaScript
let person = {
  name: 'tony',
  age: 20,
  driver: null
};
```

We want to test if the age of our person is greater than or equal to 16. If this is true, they’re old enough to drive and driver should say 'Yes'. If this is not true, driver should be set to 'No'.

We could use an `if` statement to accomplish this:

```JavaScript
if (person.age >= 16) {
  person.driver = 'Yes';
} else {
  person.driver = 'No';
}
```
But what if I told you we could do the same exact thing in just one line of code? Well, here it is: `person.driver = person.age >=16 ? 'Yes' : 'No';`

This shorter code yields us the same result of `person.driver = 'Yes';`

The Conditional (Ternary) Operator

First, we’ll take a look at the syntax of a typical if statement:
```JavaScript
if ( condition ) {
  value if true;
} else {
  value if false;
}
```
Now, the ternary operator:

`condition ? value if true : value if false`

Here’s what you need to know:
`
The condition is what you’re actually testing. The result of your condition should be `true` or `false` or at least coerce to either boolean value.

A ? separates our conditional from our true value.

 Anything between the ? and the : is what is executed if the condition evaluates to true.

Finally a : colon. If your condition evaluates to false, any code after the colon is executed.
Example — Driver Age
We’ll take a moment to revisit the initial example in this article:
```JavaScript
let person = {
  name: 'tony',
  age: 20,
  driver: null
};
```
`person.driver = person.age >=16 ? 'Yes' : 'No';`

The most important thing to note is the order of operations. 

Lets add some parenthesis to help you visualize the order in which code is executing:
`person.driver = ((person.age >=16) ? 'Yes' : 'No';)`
As you can hopefully now visualize, the very first thing that happens is our conditional is checking to see `if person.age >=16` is true or false.
Since 20 is greater than 16, this evaluates to true. Here’s where we are now:
`person.driver = (true ? 'Yes' : 'No';)`
Since the condition of our conditional is true, the value between the ? and : is returned. In this case, that is 'Yes'.
Now that we have our return value, the final thing to do is to set it equal to our variable:
person.driver = 'Yes';
Awesome! Now lets move on to some more complex examples.
Example — Student Pricing
In this example, we’re coding for a movie theater. The movie theatre offers two ticket prices: $12 for the general public, and $8 for students.
Lets create a variable to keep track of whether a patron is a student or not:
`let isStudent = true;`
With this variable we can now use a ternary operator to change the price accordingly:
```JavaScript
let price = isStudent ? 8 : 12
console.log(price);
// 8
```


Since our isStudent boolean is true, the value of 8 is returned from the ternary to the price variable.

Example — Nested Ternary

But what if our movie theater from above gives a discount to students and seniors?
We can nest ternary operators to test multiple conditions.
For this scenario assume tickets are: $12 for the general public, $8 for students, and $6 for seniors.
Here’s what the code for a Senior citizen would look like:
```JavaScript
let isStudent = false;
let isSenior = true;
let price = isStudent ? 8 : isSenior ? 6 : 10
console.log(price);
// 6
```

There’s a lot going on in this code, so lets break it down:
First we check to see if our patron is a student. Since isStudent is false, only the code after the first : is executed. After the : we have a new conditional:
Our second conditional tests isSenior — since this is true, only the code after the ? but before the : is executed.
price is then assigned the value of 6 which which we later log to the screen.
Example — Multiple operations
It is also possible to run multiple operations within a ternary. To do this, we must separate the operations with a comma. You can also, optionally, use parenthesis to help 
group your code:
```JavaScript
let isStudent = true;
let price = 12;
isStudent ? (
  price = 8,
  alert('Please check for student ID')
) : (
  alert('Enjoy the movie')
);
```
In the above example, the price of our movie is already set to $12. If isStudent is true, we adjust the price down to $8, then send an alert to have the cashier check for student ID. If isStudent is false, the above code is skipped, and we simply alert to enjoy the movie.












