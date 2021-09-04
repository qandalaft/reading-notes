# Text
## in this reading we will describe this main topics 
1. Headings and paragraphs
2. Bold, italic, emphasis
3. Superscript & superscript
4. Line Breaks & 
Horizontal Rules
5. Quotations
6. Author Details


**1. Headings and paragraphs**
* Headings 

this tags we can use to make the heading for the main heading we usw this tag `<h1> </h1>`
and insid of it we can put the Text (the main one in this case)

** levels of headings**

> we have 6 levels of headings from `<h1>` to `<h6>`

`<h1>` is used for main headings

`<h2>` is used for subheadings

If there are further sections 

under the subheadings then the 
`<h3>` element is used, and so 
on...

>Browsers display the contents of 
headings at different sizes. The 
contents of an <h1> element is 
the largest, and the contents of 
an <h6> element is the smallest. 
The exact size at which each 
browser shows the headings 
can vary slightly. Users can also 
adjust the size of text in their 
browser. You will see how to 
control the size of text, its color, 
and the fonts used when we 
come to look at CSS.

* paragraphs

this tag we use to ceart a paragraph `<p></p>`
>By default, a browser will show 
each paragraph on a new line 
with some space between it and 
any subsequent paragraphs.

**2. Bold, italic, emphasis**
* Bold & italic
1. Bold 

this tag we use to make the font Bold `<b> </b>`
>The `<b>` element also represents 
a section of text that would be 
presented in a visually different 
way (for example key words in a 
paragraph) although the use of 
the` <b>` element does not imply 
any additional meaning.

2.italic

 this tag we use to make the font italic `<i> </i>`
 >The <i> element also represents 
a section of text that would be 
said in a different way from 
surrounding content — such as 
technical terms, names of ships, 
foreign words, thoughts, or other 
terms that would usually be 
italicized.
 >

3.emphasis

we have tags inside the `HTML` to make some Text important  this tags is `<strong> </strong>` and `<im> </im>`
the `<strong>` tag make the Text inside it Bold but 
the browser know this Text is important and it show it first we the user search for it and the same with the `<im>` it make the Text inside important but in italic style 

**3.Superscript & superscript**
* Superscript

the `<sup> </sup>` tag is used 
to contain characters that 
should be superscript such 
as the suffixes of dates or 
mathematical concepts like 
raising a number to a power.

* superscript 

the `<sub> </sub>` tag  is used to 
contain characters that should 
be subscript. It is commonly 
used with foot notes or chemical 
formulas

** Line Breaks & 
Horizontal Rules**

As you have already seen, the 
browser will automatically show 
each new paragraph or heading 
on a new line. But if you wanted 
to add a line break inside the 
middle of a paragraph you can 
use the line break tag `<br />`.

To create a break between 
themes — such as a change of 
topic in a book or a new scene 
in a play — you can add a 
horizontal rule between sections 
using the `<hr />` tag. like this 
<hr>

>There are a few elements that 
do not have any words between 
an opening and closing tag. They 
are known as empty elements
and they are written differently.

>An empty element usually 
has only one tag. Before the 
closing angled bracket of an 
empty element there will often 
be a space and a forward slash 
character. Some web page 
authors miss this out but it is a 
good habit to get into.

**5. Quotations**

There are two elements 
commonly used for marking up 
quotations:

this tag we use to make quotations is `<blockquote>`
and  `<q>` the

 The `<blockquote>` element is 
used for longer quotes that take 
up an entire paragraph. Note 
how the `<p>` element is still 
used inside the `<blockquote>`
element.

 >Browsers tend to indent the 
contents of the `<blockquote>`
element, however you should not 
use this element just to indent a 
piece of text — rather you should 
achieve this effect using CSS. 

The `<q>` element is used for 
shorter quotes that sit within 
a paragraph. Browsers are 
supposed to put quotes around 
the `<q>` element, however 
Internet Explorer does not — 
therefore many people avoid 
using the `<q>` element.

>Both elements may use the cite
attribute to indicate where the 
quote is from. Its value should 
be a URL that will have more 
information about the source of 
the quotation

**6. Author Details**
* The `<address>` element has 
quite a specific use: to contain 
contact details for the author of 
the page.
It can contain a physical address, 
but it does not have to. For 
example, it may also contain a 
phone number or email address.
 >Browsers often display the 
content of the `<address>`
element in italics

> You may also be interested in 
something called the hCard 
microformat for adding physical 
address information to your 
markup
 

 ## an Example for hole Text section

 ```html

 <html>
<head>
 <title>Text</title>
</head>
<body>
 <h1>The Story in the Book</h1>
 <h2>Chapter 1</h2>
 <p>Molly had been staring out of her window for about 
 an hour now. On her desk, lying between the copies 
 of <i>Nature</i>, <i>New Scientist</i>, and all 
 the other scientific journals her work had 
 appeared in, was a well thumbed copy of <cite>On 
 The Road</cite>. It had been Molly's favorite book 
 since college, and the longer she spent in these 
 four walls the more she felt she needed to be 
 free.</p>
 <p>She had spent the last ten years in this room, 
 sitting under a poster with an Oscar Wilde quote 
 proclaiming that <q>Work is the refuge of 
 people who have nothing better to do</q>. Although 
 many considered her pioneering work, unraveling 
 the secrets of the llama <abbr 
 title="Deoxyribonucleic acid">DNA</abbr>, to be an 
 outstanding achievement, Molly <em>did</em> think 
 she had something better to do.</p>
</body>
</html>

```


# Introducing  CSS
 now we going to talking about these topics

 1. What CSS does 

 2. How CSS works

 3.  Rules, properties, and values
 <hr/>

 *  **Introduction **


 In this section, we will look at how to 
make your web pages more attractive, 
controlling the design of them using CSS.
>CSS allows you to create rules that specify how the content of 
an element should appear. For example, you can specify that 
the background of the page is cream, all paragraphs should 
appear in gray using the Arial typeface, or that all level one 
headings should be in a blue, italic, Times typeface.

* CSS Associates Style 
rules with HTML 
elements

CSS works by associating rules with HTML elements. These rules govern 
how the content of specified elements should be displayed. A CSS rule 
contains two parts: a `selector` and a `declaration`

**Selectors :** indicate which 
element the rule applies to. 
The same rule can apply to 
more than one element if you 
separate the element names 
with commas.

**Declarations : ** indicate how 
the elements referred to in 
the selector should be styled. 
Declarations are split into two 
parts (a property and a value), 
and are separated by a colon.

**CSS Properties Affect 
How Elements Are 
Displayed**

* CSS declarations sit inside curly brackets and each is made up of two 
parts: a property and a value, separated by a colon. You can specify 
several properties in one declaration, each separated by a semi-colon.

like this 
```css
h1, h2, h3 {
 font-family: Arial;
 color: yellow;}`
 ```
 `Properties` "in red color" indicate the aspects 
of the element you want to 
change. For example, color, font, 
width, height and border

`Values`"in blue color" specify the settings 
you want to use for the chosen 
properties. For example, if you 
want to specify a color property 
then the value is the color you 
want the text in these elements 
to be.

**and Example**
```html
<!DOCTYPE html>
<html>
<head>
 <title>Introducing CSS</title>
 <link href="css/example.css" type="text/css" 
 rel="stylesheet" />
</head>
<body>
 <h1>From Garden to Plate</h1>
 <p>A <i>potager</i> is a French term for an 
 ornamental vegetable or kitchen garden ... </p>
 <h2>What to Plant</h2>
 <p>Plants are chosen as much for their functionality 
 as for their color and form ... </p>
</body>
</html>
```
and this is the css code 
```css
body {
font-family: Arial, Verdana, sans-serif;}
h1, h2 {
color: #ee3e80;}
p {
color: #665544;}
```

>the numbers after `#` it call hexadecimel color numbers and we will talk about it later on 

**CSS Selectors**
* There are many different types 
of CSS selector that allow you to 
target rules to specific elements 
in an HTML document. 
The table below
introduces the most commonly 
used CSS selectors.

Selector  | Meaning | Example
------------ | ---------------------------------------------- | -------------
Universal Selector	 | Applies to all elements in the document | `* {}`
Type Selector	 | Matches element names document | `h1, h2, h3 {}`
 

# basic Javascript instructions
* new we will take about read and write 
JavaScrip
> like any new language, there are new 
words to learn (the vocabulary) and rules 
for how these can be put together (the 
grammar and syntax of the language)

1. STATEMENTS
* A script is a series of instructions that a computer can follow one-by-one. 
Each individual instruction or step is known as a statement. 
Statements should end with a semicolon.

an Example for JavaScrip code 
```JAVASCRIPT
var today= new Date(); 
var hourNow = today.getHours() ; 
var greeting;
```


>**JAVASCRIPT IS CASE SENSITIVE** 

>JavaScript is case sensitive so hourNow means 
something different to HourNow or HOURNOW.

*COMMENTS*

You should write* comments* to explain what your code does. 
They help make your code easier to read and understand. 
This can help you and others who read your code.
and the commint in JavaScrip written in tis way 

one line *comment*
`// one line comment`
multi line comment 
```
/*this is comment on multi 
line 
line
more line 
.......ect
way*/
```
* the VARIABLE in JavaScrip

A script will have to temporarily 
store the bits of information it 
needs to do its job. It can store this 
data in variables. 
>When you write JavaScript, you have to tell the 
interpreter every individual step that you want it to 
perform. This sometimes involves more detail than 
you might expect.
>When you write JavaScript, you have to tell the 
interpreter every individual step that you want it to 
perform. This sometimes involves more detail than 
you might expect.

* how to declare a variables in JavaScrip

 we must know some keyword to declare a variables in JavaScrip like `var`
 and `let` and many other key word 
 now if you want to make the declaration you must to write the key word and the `name` of the variable like belw Example:

 `var name;`
 > do not forget the `;` its called semicolon

 * now you must give the variable a value 

 you can do it by this symbol `=` in programming field its calls assignment operator 
 like the example below

 `var age = 3`

 * data taype is JavaScrip

 JavaScript distinguishes between numbers, 
strings, and true or false values known as 
Booleans. 

NUMERIC DATA TYPE 
The numeric data type handles 
numbers. 
>For tasks that involve counting 
or calculating sums, you will 
use numbers 0-9. For example, 
five thousand, two hundred and 
seventy-two would be written 
5272 (note there is no comma 
between the thousands and 
the hundreds). You can also 
have negative numbers (such 
as -23678) and decimals (three 
quarters is written as 0.75).

STRING DATA TYPE 
The strings data type consists of 
letters and other characters
Note how the string data type is 
enclosed within a pair of quotes. 
These can be single or double 
quotes, but the opening quote 
must match the closing quote. 
Strings can be used when 
working with any kind of text. 
They are frequently used to add 
new content into a page and they 
can contain HTML markup. 

BOOLEAN DATA TYPE 
Boolean data types can have one 
of two values: true or false.
>It might seem a little abstract at 
first, but the Boolean data type is 
actually very helpful. 
You can think of it a little like a 
light switch - it is either on or off. 
As you will see in Chapter 4, 
Booleans are helpful when 
determining which part of a 
script should run.









`









         




























 
