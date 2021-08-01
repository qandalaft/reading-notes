# WHAT IS AN OBJECT? 


* introduction

Objects group together a set of variables and functions to create a model 
of a something you would recognize from the real world. In an object, 
variables and functions take on new names. 

>IN AN OBJECT: VARIABLES BECOME 
KNOWN AS PROPERTIES 
If a variable is part of an object, it is called a 
property. Properties tell us about the object, such as 
the name of a hotel or the number of rooms it has. 
Each individual hotel might have a different name 
and a different number of rooms. 

>IN AN OBJECT: FUNCTIONS BECOME 
KNOWN AS METHODS 
If a function is part of an object, it is called a method. 
Methods represent tasks that are associated with 
the object. For example, you can check how many 
rooms are available by subtracting the number of 
booked rooms from the total number of rooms.

*This object represents a hotel. It has five properties and one method. 
The object is in curly braces. It is stored in a variable called hotel .*

`var hotel = { `

>Like variables and named functions, 
properties and methods have a 
name and a value. In an object, 
that name is called a key. 

>An object cannot have two keys 
with the same name. This is 
because keys are used to access 
their corresponding values. 

>The value of a property can be a 
string, number, Boolean, array, or 
even another object. The value of a 
method is always a function. 

**like the example below :-

```JavaScript
var hotel = {
    name : ' Quay ',
    rooms :40,
    booked :25,
    gym:true,
}
```
>Programmers use a lot of name/value pairs: 
*  HTML uses attribute names and values. 
*  CSS uses property names and values. 
In JavaScript: 
*  Variables have a name and you can assign them a 
value of a string, number, or Boolean. 
*  Arrays have a name and a group of values. (Each 
item in an array is a name/value pair because it 
has an index number and a value.) 
*  Named functions have a name and value that is a 
set of statements to run if the function is called. 
* Objects consist of a set of name/value pairs 
(but the names are referred to as keys). 

## How to create objects in JavaScript.

1. Creating objects using object literal syntax

This is really simple. All you have to do is throw your key value pairs separated by ‘:’ inside a set of curly braces({ }) and your object is ready to be served (or consumed), like below:
```JavaScript
const person = {
  firstName: 'testFirstName',
  lastName: 'testLastName'
};
```
2.  Creating objects using the ‘new’ keyword

* there is a two ways you can use the ‘new’ keyword pattern 

I.  Using the ‘new’ keyword with’ in-built Object constructor function

To create an object, use the new keyword with Object() constructor, like this:

`const person = new Object();`

Now, to add properties to this object, we have to do something like this:

`person.firstName = 'testFirstName';`
`person.lastName = 'testLastName';`

You might have figured that this method is a bit longer to type. Also, this practice is not recommended as there is a scope resolution that happens behind the scenes to find if the constructor function is built-in or user-defined.

II. Using ‘new’ with user defined constructor function

The other problem with the approach of using the ‘Object’ constructor function result from the fact that every time we create an object, we have to manually add the properties to the created object.

What if we had to create hundreds of person objects? You can imagine the pain now. So, to get rid of manually adding properties to the objects, we create custom (or user-defined) functions. We first create a constructor function and then use the ‘new’ keyword to get objects:

```JavaScript
function Person(fname, lname) {
  this.firstName = fname;
  this.lastName = lname;
}
```

Now, anytime you want a ‘Person’ object, just do this:

```JavaScript
const personOne = new Person('testFirstNameOne', 'testLastNameOne');
const personTwo = new Person('testFirstNameTwo', 'testLastNameTwo');
```
3. Using Object.create() to create new objects

This pattern comes in very handy when we are asked to create objects from other existing objects and not directly using the ‘new’ keyword syntax. Let’s see how to use this pattern. As stated on MDN:

>The `Object.create()` method creates a new object, using an existing object as the prototype of the newly created object.

To understand the `Object.create` method, just remember that it takes two parameters. The first parameter is a mandatory object that serves as the prototype of the new object to be created. The second parameter is an optional object which contains the properties to be added to the new object.

We will not deep dive into prototypes and inheritance chains now to keep our focus on the topic. But as a quick point, you can think of prototypes as objects from which other objects can borrow properties/methods they need.

Imagine you have an organization represented by `orgObject`

`const orgObject = { company: 'ABC Corp' };`

And you want to create employees for this organization. Clearly, you want all the employee objects

```JavaScript
const employee = Object.create(orgObject, { name: { value: 'EmployeeOne' } });

console.log(employee); // { company: "ABC Corp" }
console.log(employee.name); // "EmployeeOne"
```

4. Using `Object.assign()` to create new objects

What if we want to create an object that needs to have properties from more than one object?

 `Object.assign()` comes to our help.

 >The `Object.assign()` method is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.

 `Object.assign` method can take any number of objects as parameters. The first parameter is the object that it will create and return. The rest of the objects passed to it will be used to copy the properties into the new object. Let’s understand it by extending the previous example we saw.

Assume you have two objects as below:

```JavaScript
const orgObject = { company: 'ABC Corp' }
const carObject = { carName: 'Ford' }
```
Now, you want an employee object of ‘ABC Corp’ who drives a ‘Ford’ car. You can do that with the help of `Object.assign` as below:

`const employee = Object.assign({}, orgObject, carObject);`

Now, you get an `employee` object that has `company` and `carName` as its property

`console.log(employee); // { carName: "Ford", company: "ABC Corp" }`
 
 5. Using ES6 classes to create objects

 You will notice that this method is similar to using ‘new’ with user defined constructor function. The constructor functions are now replaced by classes as they are supported through ES6 specifications. Let’s see the code now.

 ```JavaScript
 class Person {
  constructor(fname, lname) {
    this.firstName = fname;
    this.lastName = lname;
  }
}

const person = new Person('testFirstName', 'testLastName');

console.log(person.firstName); // testFirstName
console.log(person.lastName); // testLastName
```


# DOM (Document Object Model)

* Introduction: 

The Document Object Model (DOM) is a programming interface for HTML and XML(Extensible markup language) documents. It defines the logical structure of documents and the way a document is accessed and manipulated. 

>Note: It is called a Logical structure because DOM doesn’t specify any relationship between objects.

DOM is a way to represent the webpage in a structured hierarchical way so that it will become easier for programmers and users to glide through the document. With DOM, we can easily access and manipulate tags, IDs, classes, Attributes, or Elements using commands or methods provided by the Document object.

**Structure of DOM:**

DOM can be thought of as a Tree or Forest(more than one tree). The term structure model is sometimes used to describe the tree-like representation of a document. One important property of DOM structure models is structural isomorphism: if any two DOM implementations are used to create a representation of the same document, they will create the same structure model, with precisely the same objects and relationships

**Why called an Object Model?**

Documents are modeled using objects, and the model includes not only the structure of a document but also the behavior of a document and the objects of which it is composed of like tag elements with attributes in `HTML`.

**Properties of DOM:**

Let’s see the properties of the document object that can be accessed and modified by the document object. 

1. Window Object: Window Object is always at top of the hierarchy
2. Document object: When an HTML document is loaded into a window, it becomes a document object.
3. Form Object: It is represented by form tags.
4. Link Objects: It is represented by link tags.
5. Anchor Objects: It is represented by a href tags.
6. Form Control Elements:: Form can have many control elements such as text fields, buttons, radio buttons, and checkboxes, etc.

**Methods of Document Object:**

1. write(“string”): writes the given string on the document.
2. getElementById(): returns the element having the given id value.
3. getElementsByName(): returns all the elements having the given name value.
4. getElementsByTagName(): returns all the elements having the given tag name.
5. getElementsByClassName(): returns all the elements having the given class name.

## Example:

```html
<Table>
<ROWS>
	<TR>
		<TD>Car</TD>
		<TD>Scooter</TD>
	</TR>
	<TR>
		<TD>MotorBike</TD>
		<TD>Bus</TD>
	</TR>
</ROWS>
</Table>
```






 



