# Video and Audio APIs
* HTML5 comes with elements for embedding rich media in documents — `<video>` and `<audio>` — which in turn come with their own APIs for controlling playback, seeking, etc. This article shows you how to do common tasks such as creating custom playback controls.

* and the sytx of audio and video is like this 
```
<video controls>
  <source src="rabbit320.mp4" type="video/mp4">
  <source src="rabbit320.webm" type="video/webm">
  <p>Your browser doesn't support HTML5 video. Here is a <a href="rabbit320.mp4">link to the video</a> instead.</p>
</video>

```
## The HTMLMediaElement API

Part of the HTML5 spec, the `HTMLMediaElement` API provides features to allow you to control video and audio players programmatically — for example `HTMLMediaElement.play(),` `HTMLMediaElement.pause()`, etc. This interface is available to both `<audio>` and `<video>` elements, as the features you'll want to implement are nearly identical. Let's go through an example, adding features as we go.

**for example**
```html
<div class="player">
  <video controls>
    <source src="video/sintel-short.mp4" type="video/mp4">
    <source src="video/sintel-short.webm" type="video/webm">
    <!-- fallback content here -->
  </video>
  <div class="controls">
    <button class="play" data-icon="P" aria-label="play pause toggle"></button>
    <button class="stop" data-icon="S" aria-label="stop"></button>
    <div class="timer">
      <div></div>
      <span aria-label="timer">00:00</span>
    </div>
    <button class="rwd" data-icon="B" aria-label="rewind"></button>
    <button class="fwd" data-icon="F" aria-label="fast forward"></button>
  </div>
</div>
```
* The whole player is wrapped in a `<div>` element, so it can all be styled as one unit if needed.
* The controls HTML is probably the most interesting:
1. We have four `<button>`s — play/pause, stop, rewind, and fast forward.
2. Each `<button>` has a class name, a data-icon attribute for defining what icon should be shown on each button (we'll show how this works in the below section), and an aria-label attribute to provide an understandable description of each button, since we're not providing a human-readable label inside the tags. The contents of aria-label attributes are read out by screenreaders when their users focus on the elements that contain them.
3. There is also a timer `<div>`, which will report the elapsed time when the video is playing. Just for fun, we are providing two reporting mechanisms — a `<span>` containing the elapsed time in minutes and seconds, and an extra `<div>` that we will use to create a horizontal indicator bar that gets longer as the time elapses


**Exploring the CSS**
Now open the CSS file and have a look inside. The CSS for the example is not too complicated, but we'll highlight the most interesting bits here. First of all, notice the .controls styling:
```css
.controls {
  visibility: hidden;
  opacity: 0.5;
  width: 400px;
  border-radius: 10px;
  position: absolute;
  bottom: 20px;
  left: 50%;
  margin-left: -200px;
  background-color: black;
  box-shadow: 3px 3px 5px black;
  transition: 1s all;
  display: flex;
}

.player:hover .controls, player:focus .controls {
  opacity: 1;
}
```

* We start off with the visibility of the custom controls set to hidden. In our JavaScript later on, we will set the controls to visible, and remove the controls attribute from the `<video>` element. This is so that, if the JavaScript doesn't load for some reason, users can still use the video with the native controls.

* We give the controls an `opacity of 0.5` by default, so that they are less distracting when you are trying to watch the video. Only when you are hovering/focusing over the player do the controls appear at full opacity.

* We lay out the buttons inside the control bar using Flexbox `(display: flex)`, to make things easier.

*Next, let's look at our button icons:*

```css 
@font-face {
   font-family: 'HeydingsControlsRegular';
   src: url('fonts/heydings_controls-webfont.eot');
   src: url('fonts/heydings_controls-webfont.eot?#iefix') format('embedded-opentype'),
        url('fonts/heydings_controls-webfont.woff') format('woff'),
        url('fonts/heydings_controls-webfont.ttf') format('truetype');
   font-weight: normal;
   font-style: normal;
}

button:before {
  font-family: HeydingsControlsRegular;
  font-size: 20px;
  position: relative;
  content: attr(data-icon);
  color: #aaa;
  text-shadow: 1px 1px 0px black;
}
```

First of all, at the top of the CSS we use a `@font-face` block to import a custom web font. This is an icon font — all the characters of the alphabet equate to common icons you might want to use in an application.

Next we use generated content to display an icon on each button:

* We use the `::before` selector to display the content before each `<button>` element.

* We use the `content` property to set the content to be displayed in each case to be equal to the contents of the `data-icon` attribute. In the case of our play button, data-icon contains a capital "P".

* We apply the custom web font to our buttons using `font-family`. In this font, "P" is actually a "play" icon, so therefore the play button has a "play" icon displayed on it.
 
*Last but not least, let's look at the CSS for the timer:*

```css
.timer {
  line-height: 38px;
  font-size: 10px;
  font-family: monospace;
  text-shadow: 1px 1px 0px black;
  color: white;
  flex: 5;
  position: relative;
}

.timer div {
  position: absolute;
  background-color: rgba(255,255,255,0.2);
  left: 0;
  top: 0;
  width: 0;
  height: 38px;
  z-index: 2;
}

.timer span {
  position: absolute;
  z-index: 3;
  left: 19px;
}
```
## Implementing the JavaScript

We've got a fairly complete HTML and CSS interface already; now we just need to wire up all the buttons to get the controls working.

1. Create a new JavaScript file in the same directory level as your index.html file. Call it custom-player.j
2. At the top of this file, insert the following code:

```javascript
const media = document.querySelector('video');
const controls = document.querySelector('.controls');

const play = document.querySelector('.play');
const stop = document.querySelector('.stop');
const rwd = document.querySelector('.rwd');
const fwd = document.querySelector('.fwd');

const timerWrapper = document.querySelector('.timer');
const timer = document.querySelector('.timer span');
const timerBar = document.querySelector('.timer div');
```
Here we are creating constants to hold references to all the objects we want to manipulate. We have three groups:
* The `<video>` element, and the controls bar.
* The play/pause, stop, rewind, and fast forward buttons.
* The outer timer wrapper `<div>`, the digital timer readout `<span>`, and the inner `<div>` that gets wider as the time elapses.

3. Next, insert the following at the bottom of your code:

```javascript
media.removeAttribute('controls');
controls.style.visibility = 'visible';
```
These two lines remove the default browser controls from the video, and make the custom controls visible.

**Playing and pausing the video**

Let's implement probably the most important control — the play/pause button.
1. First of all, add the following to the bottom of your code, so that the `playPauseMedia()`

```javascript
play.addEventListener('click', playPauseMedia);
```
2. Now to define `playPauseMedia()` — add the following, again at the bottom of your code:
```javascript
function playPauseMedia() {
  if(media.paused) {
    play.setAttribute('data-icon','u');
    media.play();
  } else {
    play.setAttribute('data-icon','P');
    media.pause();
  }
}
```
Here we use an `if` statement to check whether the video is paused. The `HTMLMediaElement`.paused property returns true if the media is paused, which is any time the video is not playing, including when it is set at 0 duration after it first loads. If it is paused, we set the data-icon attribute value on the play button to "u", which is a "paused" icon, and invoke the HTMLMediaElement.`play()` method to play the media.

**Stopping the video**

1. Next, let's add functionality to handle stopping the video. Add the following addEventListener() lines below the previous one you added:

```javascript
stop.addEventListener('click', stopMedia);
media.addEventListener('ended', stopMedia);
```

The click event is obvious — we want to stop the video by running our `stopMedia() `function when the stop button is clicked. We do however also want to stop the video when it finishes playing — this is marked by the ended event firing, so we also set up a listener to run the function on that event firing too.

2. Next, let's define `stopMedia() `— add the following function below playPauseMedia():
```javascript
function stopMedia() {
  media.pause();
  media.currentTime = 0;
  play.setAttribute('data-icon','P');
}
```

*there is no stop() method on the HTMLMediaElement API — the equivalent is to pause() the video, and set its currentTime property to 0. Setting currentTime to a value (in seconds) immediately jumps the media to that position.

All there is left to do after that is to set the displayed icon to the "play" icon. Regardless of whether the video was paused or playing when the stop button is pressed, you want it to be ready to play afterwards.

# images in CSS

* Controlling the size and alignment of 
your images using CSS keeps rules that 
affect the presentation of your page in 
the CSS and out of the HTML markup.

You can also achieve several interesting effects using 
background images. In this chapter you will learn how to:

* Specify the size and alignment of an image using
* Add background images to boxes
* Create image rollovers in CSS

**Controlling sizes of images in CSS**
>You can control the size of an 
image using the width and 
height properties in CSS, just 
like you can for any other box. 
Specifying image sizes helps 
pages to load more smoothly 
because the HTML and CSS 
code will often load before the 
images, and telling the browser 
how much space to leave for an 
image allows it to render the rest 
of the page without waiting for 
the image to download.
You might think that your site 
is likely to have images of all 
different sizes, but a lot of sites 
use the same sized image across 
many of their pages. 
For example, an e-commerce site 
tends to show product photos 
at the same size. Or, if your site 
is designed on a grid, then you 
might have a selection of image 
sizes that are commonly used on 
all pages, such as:
Small portrait: 220 x 360
Small landscape: 330 x 210
Feature photo: 620 x 400
Whenever you use consistently 
sized images across a site, 
you can use CSS to control 
the dimensions of the 
images, instead of putting the 
dimensions in the HTML.

First you need to determine the 
sizes of images that will be used 
commonly throughout the site, 
then give each size a name.
For example:
small
medium
large
Where the `<img>` elements 
appear in the HTML, rather 
than using width and height
attributes you can use these 
names as values for the class
attribute. 
In the CSS, you add selectors for 
each of the class names, then 
use the CSS width and height
properties to control the image 
dimensions

**aligning img with CSS**

>In the last chapter, you saw how 
the float property can be used 
to move an element to the left or 
the right of its containing block, 
allowing text to flow around it.
Rather than using the <img>
element's align attribute, web 
page authors are increasingly 
using the float property to align 
images. There are two ways that 
this is commonly achieved:
1: The float property is added 
to the class that was created to 
represent the size of the image 
(such as the small class in our 
example).
2: New classes are created with 
names such as align-left or 
align-right to align the images 
to the left or right of the page. 
These class names are used in 
addition to classes that indicate 
the size of the image.
In this example you can see the 
align-left and align-right
classes used to align the image.
It is also common to add a 
margin to the image to ensure 
that the text does not touch their 
edges

**Background Images**
>The background-image
property allows you to place 
an image behind any HTML 
element. This could be the entire 
page or just part of the page. By 
default, a background image will 
repeat to fill the entire box.
The path to the image follows 
the letters url, and it is put 
inside parentheses and quotes.
>If you search online, you will 
find lots of resources that offer 
background textures that you 
can use on your pages
>Background images are often 
the last thing on the page to 
load (which can make a website 
seem slow to load). As with any 
images you use online, if the 
size of the file is large it will take 
longer to download

**background-position**
>When an image is not being 
repeated, you can use the 
background-position
property to specify where in the 
browser window the background 
image should be placed. 
This property usually has a pair 
of values. The first represents 
the horizontal position and the 
second represents the vertical

**Contrast of background images**

>f you want to overlay text on a background image, the image must be low 
contrast in order for the text to be legible.

*an example*

```html
<!DOCTYPE html>
<html>
<head>
 <title>Images</title>
 <style type="text/css">
 body {
 color: #665544;
 background-color: #d4d0c6;
 background-image: url("images/backdrop.gif");
 font-family: Georgia, "Times New Roman", serif;
 text-align: center;}
 .wrapper {
 width: 720px;
 margin: 0px auto;}
 .header {
 margin: 40px 0px 20px 0px;}
 .entry {
 width: 220px;
 float: left;
 margin: 10px;
 height: 198px;
 background-image: url("images/shadow.png");
 background-repeat: no-repeat;
 background-position: bottom;}
 figure {
 display: block;
 width: 202px;
 height: 170px;
 background-color: #e7e3d8;
 padding: 9px;
 text-align: left;}
 figure img {
 width: 200px;
 height: 150px;
 border: 1px solid #d6d6d6;}
 figcaption {
 background-image: url("images/icon.png");
 padding-left: 20px;
 background-repeat: no-repeat;}
 </style
 ```
 # Practical Information

 *  Search engine optimization
 * Using analytics to understand visitors
 * Putting your site on the web

 To wrap up the book we are going to look 
at some practical information that will 
help you launch a successful site.

>There are entire books written about each of the topics 
covered in this chapter but I will introduce you to the key 
themes that each subject deals with and give you pointers for 
what you need to be considering. You will see

1. The basics of search engine optimization
2.  Using analytics to understand how people are using your 
site after it has launched
3. Putting your site on the web

**Search EngineOptimization (SEO)** 
>SEO is a huge topic and several books have been written on the subject. 
The following pages will help you understand the key concepts so you can 
improve your website's visibility on search engines

* The Basics
Search engine optimization (or 
SEO) is the practice of trying 
to help your site appear nearer 
the top of search engine results 
when people look for the topics 
that your website covers.
At the heart of SEO is the idea of 
working out which terms people 
are likely to enter into a search 
engine to find your site and then 
using these terms in the right 
places on your site to increase 
the chances that search engines 
will show a link to your site in 
their results.
In order to determine who comes 
first in the search results, search 
engines do not only look at what 
appears on your site. They also 
consider how many sites link 
to you (and how relevant those 
links are). For this reason, SEO 
is often split into two areas: 
on-page techniques and off-page 
techniques.
On-Page Techniques
On-page techniques are the 
methods you can use on your 
web pages to improve their 
rating in search engines.
The main component of this is 
looking at keywords that people 
are likely to enter into a search 
engine if they wanted to find 
your site, and then including 
these in the text and HTML code 
for your site in order to help the 
search engines know that your 
site covers these topics.
Search engines rely very heavily 
on the text that is in your pages 
so it is important that the terms 
people are going to search for 
are in text. There are seven 
essential places where you want 
your keywords to appear.
Ensuring that any images have 
appropriate text in the value of 
their alt attribute also helps 
search engines understand the 
content of images.
Off-Page Techniques
Getting other sites to link to you 
is just as important as on-page 
techniques. Search engines help 
determine how to rank your 
site by looking at the number of 
other sites that link to yours.
They are particularly interested 
in sites whose content is related 
to yours. For example, if you 
were running a website that 
sold fish bait, then a link from 
a hairdresser is not likely to be 
considered as relevant as one 
from an angling community.
Search engines also look at the 
words between the opening 
`<a>` tag and closing `</a>` tag 
in the link. If the text in the link 
contains keywords (rather than 
just click here or your website 
address) it may be considered 
more relevant.
The words that appear in links to 
your site should also appear in 
the text of the page that the site inks to.

**On-Page (SEO)**

>In every page of your website there are seven key places where keywords 
(the words people might search on to find your site) can appear in order 
to improve its findability

1. Page Title

The page title appears at the top 
of the browser window or on the 
tab of a browser. It is specified in 
the `<title>` element which lives 
inside the `<head>` element.

2. URL / Web Address

The name of the file is part of 
the URL. Where possible, use 
keywords in the file name.

3. Headings

If the keywords are in a heading 
`<hn>` element then a search 
engine will know that this page is 
all about that subject and give it 
greater weight than other text.

4. Text

Where possible, it helps to 
repeat the keywords in the main 
body of the text at least 2-3 
times. Do not, however, over-use 
these terms, because the text 
must be easy for a human to 
read.

5.  Link Text

Use keywords in the text that 
create links between pages 
(rather than using generic 
expressions such as "click here").

6. Image Alt Text

Search engines rely on you 
providing accurate descriptions 
of images in the alt text. This 
will also help your images show 
up in the results of image-based 
searches.

7.  Page Descriptions


The description also lives inside 
the `<head>` element and is 
specified using a `<meta>` tag. 
It should be a sentence that 
describes the content of the 
page. (These are not shown in 
the browser window but they 
may be displayed in the results 
pages of search engines.)

>Never try to fool search engines! 
They will penalize you for it. For 
example, never add text in the 
same color as the background of 
the page as they can detect this.

**Analytics: Learning about your Visitors**

* As soon as people start coming to your site, you can start analyzing 
how they found it, what they were looking at and at what point they are 
leaving. One of the best tools for doing this is a free service offered by 
Google called Google Analytics.

>Signing Up
The Google Analytics service 
relies on you signing up for an 
account at:
www.google.com/analytics
The site will give you a piece of 
tracking code which you need to 
put on every page of your site.

>How it Works
Every time someone loads a 
page of your site, the tracking 
code sends data to the Google 
servers where it is stored. 
Google then provides a webbased interface that allows you 
to see how visitors use your site

>The Tracking Code
A tracking code is provided 
by Google Analytics for each 
website you are tracking. It 
should appear just before the 
closing `</head>` tag. The code 
does not alter the appearance of 
your web pages

**How Many People Are Coming to Your Site?**

* The overview page gives you a snapshot of the key information you are 
likely to want to know. In particular, it tells you how many people are 
coming to your site.

>The content link on the left-hand side allows 
you to learn more about what the visitors are 
looking at when they come to your site

**Where Are Your Visitors Coming From?**

* The traffic sources link on the left hand side 
allows you to learn where your visitors are 
coming from.

>Referrers
This shows the sites that have 
linked to you and the number 
of people who have come via 
those sites. If a site sends a lot 
of traffic to you, get in touch and 
try to work together to ensure 
that traffic keeps flowing. You 
could also try to find similar 
sites and ask them to link to you

>Direct
This shows which page a user 
arrived on if they did not come 
via a link on another site. They 
might have typed the URL into 
their browser, used a browser 
bookmark, or clicked a link in an 
email, PDF, or Word document.

>Search Terms
This shows the terms users 
entered into a search engine 
to find your site. This can help 
you learn how visitors describe 
what they're looking for (which is 
often different to how someone 
might describe their own site). 
This can help you fine-tune your 
content and your SEO keywords.

>Advanced Features
We have only scratched the 
surface of what you can find 
out about your visitors from 
Google Analytics. Their help 
files tell you many more of the 
advanced features. If you run 
an online shop, it is well worth 
looking at their e-commerce 
tracking, which adds information 
about products sold, average 
basket size and much more. 
You can also set up goals where 
you specify the paths you want 
people to take, and then see how 
far they get through those paths, 
which is especially useful when 
gathering data from users

## Domain Names & Hosting

* DOMAIN NAMES 
Your domain name is your web 
address (e.g. google.com or bbc.
co.uk). There are many websites 
that allow you to register domain 
names. Usually you will have to 
pay an annual fee to keep that 
domain name.
These sites usually have a form 
that allows you to check whether 
your preferred domain name is 
available, and because millions 
of domain names have already 
been registered, it might take 
you a while to find the one that is 
right for your site.
A lot of sites that offer domain 
name registration also offer web 
hosting

* web hosting

>so that other people can see 
your site, you will need to upload 
it to a web server. Web servers 
are special computers that are 
constantly connected to the 
Internet. They are specially set 
up to serve web pages when 
they are requested.
With the exception of some very 
large sites, most websites live on 
web servers run by web hosting 
companies. This is usually far 
cheaper and more reliable than 
trying to run your own web 
servers.
There are lots of different types 
of hosting on offer. We will now 
take a look at some of the key 
things that will help you choose 
which hosting company to use

## FTP & Third Party Tools

* To transfer your code and images from your 
computer to your hosting company, you use 
something known as File Transfer Protocol.

>As the name suggests, File 
Transfer Protocol (or FTP) allows 
you to transfer files across the 
Internet from your computer to 
the web server hosting your site. 
There are many FTP programs 
that offer a simple interface 
that shows you the files on your 
computer alongside the files that 
are on your web server. These 
allow you to drag and drop 
files from your computer to the 
server or vice versa.






































