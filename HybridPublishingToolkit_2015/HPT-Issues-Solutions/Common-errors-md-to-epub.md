# Common errors md to ePub

## name of error
**translation**
Translation: I’m expecting a piece of code here that you forgot, most likely some punctuation, like a semi-colon, parentheses, curly bracket, etc.

This error is pretty much always caused by a typo. Unfortunately, where the error points you to can be misleading. The “something” is sometimes just fine and the actual error is caused by the line before or after that piece of code. Anytime you forget or include an improper comma, semi-colon, quote, parentheses, bracket, etc., you’ll get this error. Here are some examples:

Incorrect:

int val = 5

Correct:

----
version: InDD CC

## font problem: italic styles render in iBooks as bold italic

**Translation:**
The styles.epub.css file needs to be customised if you want to apply specific typefaces to your ePub. This means you need to use @font-face as well as listing your fonts in the src:

You also need to add a line of code to your makefile to embedd the fonts into the ePub.
--epub-embed-font=../lib/* \

### solution

The solution consists of 3 parts: make 2 changes to the css + 1 to the makefile.

**css**
incorrect:
@font-face {
src: Open Sans-LightItalic; format('opentype');
}

correct:
@font-face {
  font-family: 'OpenSans-LightItalic';
  font-style: italic;
  font-weight: 300;
  src: local('Open Sans Light Italic'), local('OpenSansLight-Italic'), url(open-sans-v13-latin-300italic.woff) format('woff');
  src: local('Open Sans Light Italic'), local('OpenSansLight-Italic'), url(open-sans-v13-latin-300italic.ttf) format('truetype');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2212, U+2215, U+E0FF, U+EFFD, U+F000;
}

incorrect:
not specifying a style for italic

correct:
em {
    font-family: "OpenSans-LightItalic";
    font-style: italic;
}


**make file**
incorrect:


correct:
--epub-embed-font=../lib/* \


## command line - when using pandoc to create epubs

**Translation:**
Pandoc is a converter, 

### solution
a guide to set it up & use it to recreate files

## how to make a border

### solution


## footnotes repeated or not formatted

**Translation**

### solution
??

## Fonts
Optional fonts:

    lib/ - folder for storing custom fonts, that will be used in the EPUB

Note on the use of custom fonts: If you choose to use fonts, make sure to change the makefile to include the use of fonts in the makefile epub rule, such as in the rule bellow, where --epub-embed-font=lib/UbuntuMono-B.ttf \ was added to allow for the use of the Ubuntu Mono font. Also include the font on th EPUB style-sheet with @font-face rule

## Fonts not rendering
**Translation**
Instead of seeing the custom font I've chosen for the book, I see a default. You need to reference the fonts you use in the .css file and in the makefile - the line below tells the makefile to embed this font in the ePub file.

### solution
Check your makefile under **epub:** section you need to include
--epub-embed-font=../lib/* \

## My book is called 'Main Title'
**Translation**
You need to update the metadata.xml file so that your ePub has the right title, author, isbn and other important info related to it. This is a good indicator it hasn't been updated and is showing the default placeholder text.

### solution
Open the metadata.xml file inside the epub folder and update the details. You can find a more info about metadata here: <a href="http://www.publishinglab.nl/blog/2015/09/25/metadata-schmetadata-whats-it-good-for/">http://www.publishinglab.nl/blog/2015/09/25/metadata-schmetadata-whats-it-good-for/</a>
