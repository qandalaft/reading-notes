## **Domain modeling**

Domain modeling is the process of creating a conceptual model for a specific problem. And a domain model that's articulated well can verify and validate your understanding of that problem.

![# Domain modeling photo](https://i.ytimg.com/vi/M1e2XwSADDE/maxresdefault.jpg)

to building our own domain models this is some tips to follow:

1. When modeling a single entity that'll have many instances, build self-contained objects with the same attributes and behaviors.

2. Model its attributes with a constructor function that defines and initializes properties.

3. Model its behaviors with small methods that focus on doing one job well.

4. Create instances using the `new` keyword followed by a call to a constructor function.

5. Store the newly created object in a variable so you can access its properties and methods from outside.

6. Use the `this` variable within methods so you can access the object's properties and methods from inside.

 [More about Domain modeling see this video](https://youtu.be/M1e2XwSADDE)

## **Tables in HTML**

Table is used to creating rows and columns on a Web page to arrange data into it.

![# Tables in HTML photo](https://cf2.ppt-online.org/files2/slide/x/x03e9GTk5pRrMdEywnDSZbjBHJ2zoYaFmfuKsh/slide-10.jpg)

The `<table>` tag defines an HTML table for example:

```
<table style="width:100%">
  <tr>
    <th>Firstname</th>
    <th>Lastname</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>50</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>94</td>
  </tr>
</table>
```

- Text in `<th>` elements are bold and centered by default.

- Text in `<td>` elements are regular and left-aligned by default.


# **Function method and object in JavaScript**

each one of these terms refers to JavaScript element

**Function**

![# Function in JavaScript photo](https://s3.ap-south-1.amazonaws.com/s3.studytonight.com/tutorials/uploads/pictures/1587882057-1.png)

> (w3schools.com) A JavaScript function is a block of code designed to perform a particular task.

**Object**

![# Object in JavaScript photo](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQlExxPSWHLOxOnlnz0oNV8D1SyQHhtBpcbJA&usqp=CAU)

Everything in life is an object, for example, a human is an object a computer is an object and a car is an object every object has properties and actions, in a JavaScript object is a block of code that has properties and actions

**Method**

![# Method in JavaScript photo](https://ultimatecourses.com/assets/blog/javascript/private-properties-methods-javascript-classes-d115034832e72871d7f0e465ef68591b8c2776dd6afad6040e2303ac2db7e880.png)

By the simple way to explain method: the method is action that can be performed on the object

Method example:

`name = person.fullName();`

`name` is a variable `person` is an object `fullName()` is a method.