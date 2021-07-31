Color Names
===========

These files are generated using a script which parses the list of colors
on Wikipedia, here:

  http://en.wikipedia.org/wiki/List_of_colors

The script used is (poorly) written in Python and depends heavily on the
input format as was copied and pasted from Wikipedia using Firefox into a
plain text file. The script is named `format-colors` and can be found in the
same directory as the data files. Run it at your own discretion.

There's a GNU Make file called `makefile` that just re-generates the data
files when the input file is updated or the script is changed. You probably
don't need this file at all.

There are various output formats, explained below.

Note: some of the information in the output files is redundant, ex. the
identifier name can be found from the regular name and the RGB integer
triplet is provided also by the hex HTML RGB triplet. The reason is I needed
this in a specific format for a project. It should be trivial to remove this
information if it is redundant for you.

Note: If you're using these files for something automated/scripted, please
put them on your own server so you don't pound mine.

C Code
------

For use in programs in the C programming language. It contains an enum like:

```c
typedef enum Color {
  ...
  COLOR_RED,
  ...
};
```

And then an array of `ColorInfo` structures where the `COLOR_` enumerators
index into the array. It looks like:

```c
ColorInfo color_data[COLOR_NAMES_MAX] = {
  ...
  { "Red", "#f00", { 255, 0, 0 } },
  ...
};
```

So if you wanted to look up the colour red, you'd do something like this:

```c
const ColorInfo *clrinf = &color_data[COLOR_RED];
printf("Color Name: %s\n", clrinf->name);
printf("Color Hex: %s\n", clrinf->hex);
printf("Color RGB: (%d, %d, %d)\n",
  clrinf->rgb.r, clrinf->rgb.g, clrinf->rgb.b);
```

Look at the code for more details.

Conf
----

Similar to Windows `.ini` files or GKeyFiles (GLIB). For example:

```ini
...
[red]
name=Red
hex=#f00
rgb=255;0;0
...
```

CSV
---

Comma separated values for example to import into a spreadsheet utility.
Looks like:

```csv
...
red,"Red",#f00,255,0,0
...
```

HTML
----

The HTML format is meant to be viewed in your browser as a "catalog" of the
colors. It closely resembes the Wikipedia colour list page.

Use the "View Source" feature in your browser to examine the format.

JSON
----

JavaScript Object Notation, looks like a JS or Python data structure, for
example:

```js
{
  ...
  "red": {
    "name": "Red",
    "hex": "#f00",
    "rgb": [255, 0, 0]
  }
  ...
}
```

S-Expressions
-------------

S-Expression, which might be useful for Lisp or other languages, for example:

```lisp
(
  ...
  (red 'Red' '#f00' (255 0 0))
  ...
)
```

XML
---

Good ol' XML format, for example:

```xml
<colors>
  ...
  <color id="red" hex="#f00" red="255" green="0" blue="0">Red</color>
  ...
</colors>
```

# [html2text](http://www.aaronsw.com/2002/html2text/)

html2text is a Python script that converts a page of HTML into clean, easy-to-read plain ASCII text. Better yet, that ASCII also happens to be valid Markdown (a text-to-HTML format).

Usage: `html2text.py [(filename|url) [encoding]]`

    Options:
      --version             show program's version number and exit
      -h, --help            show this help message and exit
      --ignore-links        don't include any formatting for links
      --ignore-images       don't include any formatting for images
      -g, --google-doc      convert an html-exported Google Document
      -d, --dash-unordered-list
                            use a dash rather than a star for unordered list items
      -b BODY_WIDTH, --body-width=BODY_WIDTH
                            number of characters per output line, 0 for no wrap
      -i LIST_INDENT, --google-list-indent=LIST_INDENT
                            number of pixels Google indents nested lists
      -s, --hide-strikethrough
                            hide strike-through text. only relevent when -g is
                            specified as well

Or you can use it from within Python:

    import html2text
    print html2text.html2text("<p>Hello, world.</p>")

Or with some configuration options:

    import html2text
    h = html2text.HTML2Text()
    h.ignore_links = True
    print h.handle("<p>Hello, <a href='http://earth.google.com/'>world</a>!")

_Originally written by Aaron Swartz. This code is distributed under the GPLv3._


## How to do a release

1. Update the version in `html2text.py`
2. Update the version in `setup.py`
3. Run `python setup.py sdist upload`

## How to run unit tests

    cd test/
    python run_tests.py

[![Build Status](https://secure.travis-ci.org/aaronsw/html2text.png)](http://travis-ci.org/aaronsw/html2text)