# Introduction
## what is Expressions and operators ?
- Expressions perform specific actions, based on an operator, with one or two operands. An operand can be a constant, a variable or a function result. Operators are arithmetic, logical, and relational. As with C, some operators vary in functionality according to the data type of the operands specified in the expression.
1. **Expressions**
-
An expression is any valid unit of code that resolves to a value.

Every syntactically valid expression resolves to some value but conceptually, there are two types of expressions: with side effects (for example: those that assign value to a variable) and those that in some sense evaluate and therefore resolve to a value.

The expression x = 7 is an example of the first type. This expression uses the = operator to assign the value seven to the variable x. The expression itself evaluates to seven.

The code 3 + 4 is an example of the second expression type. This expression uses the + operator to add three and four together without assigning the result, seven, to a variable.


- **JavaScript has the following kinds of expressions**:
- Arithmetic: evaluates to a number, for example
- String: evaluates to a character string, for example "Fred" or "234"
- Logical: evaluates to true or false
-The special keyword null denotes a null value. In contrast, variables that have not been assigned a value are undefined, and cannot be used without a run-time error.

- **Operators** 
- JavaScript has the following types of operators. This section describes the operators and contains information about operator precedence
- An assignment operator assigns a value to its left operand based on the value of its right operand. The simple assignment operator is equal (=), which assigns the value of its right operand to its left operand. That is, x = y assigns the value of y to x.

- An assignment operator assigns a value to its left operand based on the value of its right operand. The simple assignment operator is equal (=), which assigns the value of its right operand to its left operand. That is, x = y assigns the value of y to x.
- Comparison operators
A comparison operator compares its operands and returns a logical value based on whether the comparison is true. The operands can be numerical, string, logical, or object values. Strings are compared based on standard lexicographical ordering, using Unicode values. In most cases, if the two operands are not of the same type, JavaScript attempts to convert them to an appropriate type for the comparison. This behavior generally results in comparing the operands numerically. The sole exceptions to type conversion within comparisons involve the === and !== operators, which perform strict equality and inequality comparisons. These operators do not attempt to convert the operands to compatible types before checking equality. The following table describes the comparison operators in terms of this sample code:
- var var1 = 3;
- var var2 = 4;
- Arithmetic operators
An arithmetic operator takes numerical values (either literals or variables) as their operands and returns a single numerical value. The standard arithmetic operators are addition (+), subtraction (-), multiplication (*), and division (/). These operators work as they do in most other programming languages when used with floating point numbers (in particular, note that division by zero produces Infinity). For example:
- 1 / 2; // 0.5
1 / 2 == 1.0 / 2.0; // this is true
- In addition to the standard arithmetic operations (+, -, *, /), JavaScript provides the arithmetic operators listed in the following table:

Operator  | Description
------------ | -------------
Remainder (%)	 | Binary operator. Returns the integer remainder of dividing the two operands.
Increment (++)| Unary operator. Adds one to its operand. If used as a prefix operator (++x), returns the value of its operand after adding one; if used as a postfix operator (x++), returns the value of its operand before adding one.
Decrement (--) | Unary operator. Subtracts one from its operand. The return value is analogous to that for the increment operator.
Unary negation (-) | Unary operator. Returns the negation of its operand.
Unary plus (+)| 	Unary operator. Attempts to convert the operand to a number, if it is not already.
Exponentiation operator (**)| 	Calculates the base to the exponent power, that is, base^exponent

## what is loops?
- Loops simpley is
 offer a quick and easy way to do something repeatedly
 - **and we have many types of loops in jacascript**

 1. for statement
 2. do...while statement
3. while statement
4. labeled statement
5. break statement
6. continue statement
7. for...in statement
8. for...of statement  
- *for statement*
A for loop repeats until a specified condition evaluates to false. The JavaScript for loop is similar to the Java and C for loop.

A for statement looks as follows:
for ([initialExpression]; [conditionExpression]; [incrementExpression])
  statement
- *do...while statement*
- The do...while statement repeats until a specified condition evaluates to false.

A do...while statement looks as follows:
do
  statement
while (condition);
- *while statement*
- A while statement executes its statements as long as a specified condition evaluates to true. A while statement looks as follows:
- while (condition)

  statement
  


