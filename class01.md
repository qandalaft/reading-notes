# HTML 
## HTML Describes
the Structure 
of Pages
- In the browser window you can see a web page that features exactly 
the same content as the Word document you met on the page 18. To 
describe the structure of a web page, we add code to the words we want 
to appear on the page
- You can see the HTML code for this page below. 
it contans the main elements in HTML
like `body` its called Semantics and we will talk about it in details later on
and also the `tags<>` also we  will talk about it in details later on   
```html
<html>
<body>
 <h1>This is the Main Heading</h1>
 <p>This text might be an introduction to the rest of 
 the page. And if the page is a long one it might 
 be split up into several sub-headings.<p>
 <h2>This is a Sub-Heading</h2>
 <p>Many long articles have sub-headings so to help 
 you follow the structure of what is being written. 
 There may even be sub-sub-headings (or lower-level 
 headings).</p>
 <h2>Another Sub-Heading</h2>
 <p>Here you can see another sub-heading.</p>
</body>
</html>
```
- the `tags<>`

** what is the `tags<>`**

Tags act like containers. They tell you 
something about the information that lies 
between their opening and closing tags

1. The opening `<html>` tag indicates that anything between it and a closing `</html>` tag is HTML code.
2. The `<body>` tag indicates that anything between it and the closing 
`</body>` tag should be shown inside the main browser window
3. Words between `<h1>` and `</h1>` are a main heading
As Kanye West said:

> note: the `<h1>` and `</h1>` its called `tags`
>and we will talk about all of its  later on 

4. A  paragraph of text appears between these `<p>` and `</p>` tags.
5. Words between <h2> and </h2> form a sub-heading.
6. he closing `</body>` tag indicates the end of what should appear in the main browser window.
7. he closing `</html>` tag indicates that it is the end of the HTML code.

### the attributes
- Attributes provide additional information 
about the contents of an element. They appear 
on the opening tag of the element and are 
made up of two parts: a name and a value, 
separated by an equals sign

*for instance*

```html 
<p lang="en-us">Paragraph in English</p>
```
> the word `lang` is an example about attribute `name`
> and the word inside the "" is an example about attribute `value`

The majority of attributes can
only be used on certain 
elements, although a few 
attributes (such as lang) 
can appear on any element

Most attribute values are 
either pre-defined or follow a 
stipulated format. We will look 
at the permitted values as we 
introduce each new attribute.

The value of the lang attribute
is an abbreviated way of 
specifying which language is
used inside the element that
all browsers understand.

### ID attribute 

* Every HTML element can carry 
the id attribute. It is used to 
uniquely identify that element 
from other elements on the 
page. Its value should start with 
a letter or an underscore (not a 
number or any other character).
It is important that no two 
elements on the same page 
have the same value for their id
attributes (otherwise the value is 
no longer unique).
As you will see when you 
come to look at CSS in the next 
section, giving an element a 
unique identity allows you to 
style it differently than any other 
instance of the same element 
on the page. For example, 
you might want to assign one 
paragraph within the page 
(perhaps a paragraph containing 
a pull quote) a different style 
than all of the other paragraphs. 
In the example on the right, the 
paragraph with the id attribute 
whose value is pullquote is 
made uppercase using CSS.
If you go on to learn about 
JavaScript (a language that 
allows you to add interactivity to 
your pages), id attributes can be 
used to allow the script to work 
with that particular element.
The id attribute is known as a 
global attribute because it can 
be used on any element.
### the class attribute
- Every HTML element can 
also carry a class attribute. 
Sometimes, rather than uniquely 
identifying one element within 
a document, you will want a 
way to identify several elements 
as being different from the 
other elements on the page. 
For example, you might have 
some paragraphs of text that 
contain information that is more 
important than others and want 
to distinguish these elements, or 
you might want to differentiate 
between links that point to other 
pages on your own site and links 
that point to external sites. 
To do this you can use the 
class attribute. Its value 
should describe the class it 
belongs to. In the example on 
the left, key paragraphs have a 
class attribute whose value is 
important.
The class attribute on any 
element can share the same 
value. So, in this example, the 
value of important could be 
used on headings and links, too.



### the history og HTML
* Since the web was first created, there have 
been several different versions of HTML.
1. HTML 4

is was released at 1997 With the exception of a few 
elements added in HTML5 
(which have been highlighted), 
the elements you have seen in 
this book were all available in 
HTML 4. 

Although HTML 4 had some 
presentational elements to 
control the appearance of pages, 
authors are not recommended to 
use them any more. (Examples 
include the `<center>` element 
for centering content on a 
page, `<font>` for controlling 
the appearance of text, and 
`<strike>` to put a line through 
the text — all of these can be 
achieved with CSS instead.)

2. XHTML 1.0 

it was released at 2000

In 1998, a language called XML 
was published. Its purpose 
was to allow people to write 
new markup languages. Since 
HTML was the most widely used 
markup language around, it was 
decided that HTML 4 should be 
reformulated to follow the rules 
of XML and it was renamed 
XHTML. This meant that 
authors had to follow some new, 
more strict rules about writing 
markup. For example
*  Every element needed a 
closing tag (except for empty 
elements such as `<img />`).
*  Attribute names had to be in 
lowercase.
*  All attributes required a value, 
and all values were to be 
placed in double quotes
*  Deprecated elements should 
no longer be used.
*  Every element that was 
opened inside another 
element should be closed 
inside that same element.
>Each new version was designed 
to be an improvement on the 
last (with new elements and 
attributes added and older code 
removed).
3.  HTML5

it was released at 2000 and in this version  web page authors do 
not need to close all tags, and 
new elements and attributes will 
be introduced. At the time of 
writing, the HTML5 specification 
had not been completed, but 
the major browser makers had 
started to implement many of 
the new features, and web page 
authors were rapidly adopting 
the new markup.

Despite the fact that HTML5 
is not yet completed, you can 
safely take advantage of the 
new features of the language as 
long as you endeavour to ensure 
that users with older browsers 
will be able to view your pages 
(even though some of the extra 
features will not be visible to 
them).

**DOCTYPEs**
* Because there have been 
several versions of HTML, each 
web page should begin with a 
DOCTYPE declaration to tell a 
browser which version of HTML 
the page is using (although 
browsers usually display the 
page even if it is not included). 
We will therefore be including 
one in each example for the rest 
of the book
* As you will see when we come to 
look at CSS and its box model on 
page 316, the use of a DOCTYPE 
can also help the browser to 
render a page correctly

Because XHTML was written 
in XML, you will sometimes 
see pages that use the XHTML 
strict DOCTYPE start with 
the optional XML declaration. 
Where this is used, it should be 
the first thing in a document. 
There must be nothing before it, 
not even a space.

and here is an example for each version of the HTML
1. HTML 5
```html
<!DOCTYPE html>
```
2.  HTML 4
```html
<!DOCTYPE html PUBLIC
"-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
```
3. Transitional XHTML 1.0
```html
<!DOCTYPE html PUBLIC
"-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/
 xhtml1-transitional.dtd">
 ```
 4. Strict XHTML 1.0
```html
<!DOCTYPE html PUBLIC
"-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/
 xhtml1-strict.dtd"
```
 **comments in HTML**

 If you want to add a comment 
to your code that will not be 
visible in the user's browser, you 
can add the text between these 
characters: `<!-- comment  -->`

**inline and Block elements**

1. inline elements
* Some elements will always 
appear to continue on the 
same line as their neighbouring 
elements. These are known as 
inline elements.

*Examples of inline elements are 
`<a>`, `<b>`,` <em>`, and `<img>`.*

2.block element
* Some elements will always 
appear to start on a new line in 
the browser window. These are 
known as block level elements
*Examples of block elements are 
`<h1>`,` <p>`,` <ul>`, and `<li>`*












 

