# Lists

* in this part we will going to talk about the lists the numbered lists,bullet lists, Definition lists


- **  the types of the lists im HTML**
1.  **Ordered lists**
> are lists where each item in the list is 
numbered. For example, the list might be a set of steps for 
a recipe that must be performed in order, or a legal contract 
where each point needs to be identified by a section 
number.
2. **Unordered lists**
> are lists that begin with a bullet point 
(rather than characters that indicate order)
 3.  **Definition lists**
 > are made up of a set of terms along with the 
definitions for each of those terms

1.  *Ordered lists*

The ordered list is created with 
the `<ol>` element

>Each item in the list is placed 
between an opening `<li>` tag 
and a closing `</li>` tag. (The li
stands for list item.)
Browsers indent lists by default.
Sometimes you may see a type
attribute used with the `<ol>`
element to specify the type of 
numbering (numbers, letters, 
roman numerals and so on). It 
is better to use the CSS liststyle-type property covered 
on pages 333-335.

2. *Unordered lists*

The unordered list is created 
with the` <ul>` element.

>Each item in the list is placed 
between an opening `<li>` tag 
and a closing `</li>` tag. (The li
stands for list item.)
Browsers indent lists by default.
Sometimes you may see a type
attribute used with the `<ul>`
element to specify the type of 
bullet point (circles, squares, 
diamonds and so on). It is better 
to use the CSS list-styletype property covered on pages 
333-335

3. *Definition Lists*

The definition list is created with 
the `<dl>` element and usually 
consists of a series of terms and 
their definitions.
Inside the `<dl>` element you will 
usually see pairs of `<dt>` and 
`<dd>` elements.
* `<dt>`

This is used to contain the term 
being defined (the definition 
term).
* `<dd>`
This is used to contain the 
definition
>Sometimes you might see a list 
where there are two terms used 
for the same definition or two 
different definitions for the same 
term.

## **nested listes**
* You can put a second list inside 
an `<li>` element to create a sublist or nested list.
Browsers display nested lists 
indented further than the parent 
list. In nested unordered lists, 
the browser will usually change 
the style of the bullet point too.

and this is an example 

```HTML
<ul>
<li>Mousses</li>
<li>Pastries
 <ul>
 <li>Croissant</li>
 <li>Mille-feuille</li>
 <li>Palmier</li>
 <li>Profiterole</li>
 </ul>
</li>
<li>Tarts</li>
</ul>
```







