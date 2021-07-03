# **Introduction**
- CSS stands for Cascading Style Sheets
- CSS describes how HTML elements are to be displayed on screen, paper, or in other media
- CSS saves a lot of work. It can control the layout of multiple web pages all at once
- External stylesheets are stored in CSS files
- CSS can be used for very basic document text styling — for example changing the color and size of headings and links. It can be used to create layout — for example turning a single column of text into a layout with a main content area and a sidebar for related information. It can even be used for effects such as animation. Have a look at the links in this paragraph for specific examples.
Why Use CSS?
- CSS is used to define styles for your web pages, including the design, layout and variations in display for different devices and screen sizes


 However, the web would be a boring place if all websites looked like that. Using CSS you can control exactly how HTML elements look in the browser, presenting your markup using whatever design you like.
 ## now the CSS syntax
- CSS is a rule-based language — you define rules specifying groups of styles that should be applied to particular elements or groups of elements on your web page. For example "I want the main heading on my page to be shown as large red text."
- for instance:-
- body {
  background-color: lightblue;
}

h1 {

  color: white;

  text-align: center;
}

p {

  font-family: verdana;

  font-size: 20px;
}
- h1 {

    color: red;

    font-size: 5em;
}

- **CSS Solved a Big Problem**
HTML was NEVER intended to contain tags for formatting a web page!

HTML was created to describe the content of a web page, like:

<h1>This is a heading</h1>

<p>This is a paragraph.</p>

When tags like <font>, and color attributes were added to the HTML 3.2 specification, it started a nightmare for web developers. Development of large websites, where fonts and color information were added to every single page, became a long and expensive process.

To solve this problem, the World Wide Web Consortium (W3C) created CSS.

CSS removed the style formatting from the HTML page!
- **CSS Saves a Lot of Work!**
- The style definitions are normally saved in external .css files.

With an external stylesheet file, you can change the look of an entire website by changing just one file!

# **CSS Selectors**
- A CSS selector selects the HTML element(s) you want to style.
1. The element selector

 selects HTML elements based on the element name.
- for example:- 

 Here, all <p> elements on the page will be center-aligned, with a red text color: 

 p {

  text-align: center;

  color: red;

}

2. The CSS id Selector

The id selector uses the id attribute of an HTML element to select a specific element.

The id of an element is unique within a page, so the id selector is used to select one unique element!

To select an element with a specific id, write a hash (#) character, followed by the id of the element.
- for example:- 

The CSS rule below will be applied to the HTML element with id="para1": 

#para1 {

  text-align: center;

  color: red;
}
 
 3. The CSS class Selector

 The class selector selects HTML elements with a specific class attribute.

To select elements with a specific class, write a period (.) character, followed by the class name.

- for example:- 

.center {
  text-align: center;
  color: red;
}

4. The CSS Universal Selector

The CSS rule below will affect every HTML element on the page: 

* {
  text-align: center;
  color: blue;
}

5. The CSS ID  Selector

The CSS ID selector matches an element based on the value of the element’s id attribute. In order for the element to be selected, its id attribute must match exactly the value given in the selector.
- for example:- 

/* The element with id="demo" */


#demo {

  border: red 2px solid;
}

## *How To Add CSS*
- thier is a Three Ways to Insert CSS
1. External CSS
2. Internal CSS
3. Inline CSS
- **External CSS**
- With an external style sheet, you can change the look of an entire website by changing just one file!

Each HTML page must include a reference to the external style sheet file inside the <link> element, inside the head section.

- for example:- 


- <!DOCTYPE html>

< html>

< head>

< link rel="stylesheet" href="mystyle.css">

< /head>

< body>

< h1>This is a heading</ h1>


< p>This is a paragraph.< /p>


< /body>

< /html>
- An external style sheet can be written in any text editor, and must be saved with a .css extension.

The external .css file should not contain any HTML tags.

Here is how the "mystyle.css" file looks:
- body {
  background-color: lightblue;
}

h1 {
  color: navy;

  margin-left: 20px;

}

2. **Internal CSS**

An internal style sheet may be used if one single HTML page has a unique style.

The internal style is defined inside the <style> element, inside the head section.
- for example:- 

nternal styles are defined within the <style> element, inside the <head> section of an HTML page:

< !DOCTYPE html>

< html>

< head>

< style>

body  {
  background-color: linen;
}

h1 {
  color: maroon;
  margin-left: 40px;
}
< /style>

< /head>

< body>

< h1>This is a heading</h1>

< p>This is a paragraph.</p>

<  /body>

< /html>

3. **Inline CSS**
* An inline style may be used to apply a unique style for a single element.

To use inline styles, add the style attribute to the relevant element. The style attribute can contain any CSS property.

- for example:- 
- <!DOCTYPE html>
<html>
<body>

<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>

</body>
</html>

