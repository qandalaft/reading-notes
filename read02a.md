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












 
