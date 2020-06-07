

Crash Course in HTML
====================

* * * * *

What is HTML? 
-------------

-   Hypertext Markup Language

-   Consists of plain text with markup tags

-   Browser flows text in an unbroken paragraph until a markup tag is
    encountered in the text

Basic Example
------------------

-   See
    [example](Sample%20Document.md)

-   Begins with a declaration specifying which HTML version

-   Every HTML document consists of a HEAD and a BODY

-   HEAD section is optional

    -   May contain a TITLE, which appears in the browser title bar and
        is the default name for bookmarks

    -   May contain metadata (data about the content) and scripts

-   BODY section is required, and contains the visible content of the
    page

 
 Basic Content Formatting
----------------------------

-   See a [comprehensive
    example](Sample.md)

-   \<h1\> ... \</h1\> defines a heading (\<h2\>, ..., \<h7\> define
    successively smaller headings)

-   \<p\> ... \</p\> defines a paragraph

-   \<br/\> creates a line break

-   \<hr/\> defines a horizontal line

-   \<b\>, \<i\>, and \<u\> create boldface, italic, and underline
    effects

-   Alignment is controlled by an optional *align*attribute:\
     \
     \<h1 align="center"\>This is a centered header\</h1\>

 

 Markup Tags 
----------------

-   Tags appear in \< brackets \> and are not case sensitive

-   Tags come in pairs:\
     \
     \<h1\>This is a heading\</h1\>\
     \
     The closing version of the tag begins with a / (as in \</h1\>)\
      

-   Some tags can be self-closing. For example, a line break can be
    written\
     \
     \<br\>\</br\> \
     \
     or just\
     \
     \<br/\>\
      

-   Some tags can contain attributes: \
     \
     \<p align="right"\>This is a right-aligned paragraph.\</p\>\
     \<a href="http://www.bju.edu" \>This is a link to the BJU home
    page\</a\>
     \
     An attribute consists of a name=value pair 

 
 Character Entities
----------------------

You may have wondered how \> and \< symbols get included on a web page,
if they are used to define tags. For example, how do we get the browser
to display the text \<b\> instead of turning on boldface?

We use &lt; and &gt; to get the \< and \> brackets, respectively,
displayed on a web page. These are called **HTML character entities**.

-   An HTML character entity begins with & and ends with ;\
      

-   That means that to get a & marker displayed, we must also use a
    special character entity: &amp;\
      

-   Aside from \< \> and &, other important character entities include

    -   the non-breaking space: **&nbsp;** \
         Normally the browser will break a line at white space. To avoid
        this, you can introduce a non-breaking space. For example, if
        Mrs. Humphrey comes at the end of a line, the browser might
        break the line between Mrs. and Humphrey. To avoid that break,
        you could write Mrs.&nbsp;Humphrey instead, forcing the browser
        to display the entire name Mrs. Humphrey on the same line.

    -   the quotation mark: **&quot;**

-   The full list:
    [http://www.w3.org/TR/html401/sgml/entities.html](http://www.w3.org/TR/html401/sgml/entities.html)

 

 HTML Versions and the \<!DOCTYPE\> element
----------------------------------------------

The current HTML standard version is HTML 5.

The \<!DOCTYPE\> element specifies the HTML version to which a
particular HTML document conforms. When used, it appears at the very
beginning of an HTML document.

There are a number of combinations of attributes you might see in a
\<!DOCTYPE\> tag. Here are some of the possibilities:

-   **HTML 5.0 :**\
     `<!DOCTYPE     html> `

-   **HTML 4.0 Standards Compliant:** \

    `<!DOCTYPE HTML PUBLIC "-//W3C//DTD     HTML 4.0//EN" "http://www.w3.org/TR/REC-html40/strict.dtd">     `{.western}

The \<!DOCTYPE\> element is checked by browsers, and controls a
browser's backwards compatibility mode.

The \<!DOCTYPE\> element is used by HTML validator tools to determine
which version of the standard should be used when validating the
document. Web publishers use these tools to check the correctness of
their documents before publishing them on the web.

 

Layout with Tables
------------------

For a long time, web designers relied on tables to obtain sophisticated
page layouts. Although Style Sheets are now available to help with
layout, tables are still the simplest way to go in many cases.

-   See [example
    \#1](table1.md).
    A simple table with borders. \
      

-   See [example
    \#2](table2.md).
    A simple table with no borders, some alignment, color, and width
    control.\
      

-   See [example
    \#3](table3.md).
    Tables can be used to control the formatting of an entire page.

 

Links 
-----

The \<a\> tag is used to create a link. Format: \<a
href="*url*"\>*Hyperlink text*\</a\>

-   The *href* specifies the destination of the link. When the user
    clicks the underlined *hyperlink text,* the browser navigates to the
    *url* and displays the new document.\
     \
     Example: \<a href="http://www.bju.edu" \> Click here to go to the BJU
    home page\</a\>\
      

-   The document will be opened in a new browser window if the target
    attribute is specified:\
     \
     \<a href="*url*" target="\_blank"\>*Hyperlink text*\</a\>\
     \
     The target="\_blank" attribute tells the browser to load the target
    document in a new browser window. The original window remains.

 

 Relative vs. Absolute URL's
--------------------------------

A URL (Uniform Resource Locator) is the address of a resource on the
web. It has the form

An absolute URL contains all of these elements (ex:
http://www.bju.edu). The browser must have an absolute URL to
be able to load a document.

Often, hyperlinks in an HTML page omit the protocol and web server name
in the URL; they specify a relative URL. Here's an example:

When the user clicks this hyperlink, the web browser creates an absolute
URL from this relative URL by filling in the missing pieces with
information from the current web page. For example, if the URL of the
current web page is

the browser would attempt to load

Relative URL's can also include .. and / marks. For example, if the link
were defined this way:

the browser would attempt to load

And if the link were defined this way:

the browser would attempt to load

The use of relative URL's makes it easier to move a set of web pages
from one server to another, or one subdirectory to another, and still
have the links work correctly.

 

 URL Encoding 
----------------

Certain characters may not appear in the URL. Spaces and certain other
punctuation characters \
 \
 `` < > % # { } | \ ^ [ ] ` " ``\
 \
 must be encoded using a special escape sequence: a percent symbol
followed by the character's UNICODE number in two hexadecimal digits.
For example, since the UNICODE value of a space is 32, %20 is used to
encode a space in a URL. \
 \
 Example: to link to a file with a space in the name, like
.../top story.html, the URL would be encoded using %20, like this:
.../top%20story.html.\
 \
 In addition, the following characters, when appearing in a query string
name/value pair, must be encoded:\
 \
 `; / ? : @ & = + , $'\
  

 

 Inline Links
----------------

A long document can contain several screenfuls of text. An inline link
is a link that takes the user to a specific spot in the target document
(a bookmark).

1.  Create the "bookmark" using the \<a\> tag in the target document:
    \<a name="*bookmarkname*" /\>\
     \
     Example: \<a name="faculty" /\>\
      

2.  Reference the bookmark in the hyperlink: \<a
    href="*targetdocumenturl*\#*bookmarkname*"*\>\
     \
    *Example: \<a href="departmentinfo.html\#faculty"\>Faculty
    info\</a\>

 

Using Images
------------

The \<img /\> tag is used to include an image on a web page. Format:
\<img src="*url*" alt="alt text" /\>

-   The *src* specifies the filename of the image \
      

-   The *alt* specifies the text to be displayed by the browser if the
    user has disabled image loading (in IE, the alt text is displayed as
    a tooltip when the user hovers the mouse over the image) \
      

-   Note this is usually written as a self-closing tag \
      

-   Example: \<img src="https://www.bju.edu/galleries/flickr-72157656321622504/large/21249929200_83a847cb7e_o.jpg?" /\>

The width and height attributes can be used to specify the size of the
image.

If the values are larger or smaller than the image's true size,  the
browser will shrink or stretch the image to fit.

-   Tip: A bar of any size can be created by taking a small 1x1 pixel
    gif and specifying the size you want. One useful application:
    producing dynamically generated bar graphs.\
      

-   Tip: Even if you want the image to appear at its true size,
    specifying the image's width and height attributes can speed the
    rendering of the page.

 

 Relative vs. Absolute URL's 
-------------------------------

Often the full image URL ("absolute" URL) is not used if the image
resides on the same server as the web page itself. Instead, a relative
URL is given. Here are some example possibilities of using relative
URL's:

-   \<img src="/images/bluebar.gif" /\>\
     The image is located in the /images folder located in the root
    folder of the same web server.\
      

-   \<img src="images/bluebar.gif" /\>\
     The image is located in an *images* subfolder located in the folder
    of this web page\
      

-   \<img src="bluebar.gif" /\>\
     The image is located in the same folder as this web page

-   Using a relative URL is always preferred. Watch out for tools that
    create images with absolute URL's that refer to a drive letter
    (file:///c:/my images/bluebar.gif). These can cause headaches when
    it comes time to publish.

 

 Laying out Text and Images
------------------------------

Tables are very helpful when you need to control the position of text
and graphics on a page.

### 

 

HTML Forms
----------

An HTML form is a region of a web page that contains data-entry
controls.

Here's a sample HTML page containing a form:

+--------------------------------------------------------------------------+
| ### Encrypt.html {.western}                                              |
+--------------------------------------------------------------------------+
| ``` {.western}                                                           |
| <html><body>                                                             |
|                                                                          |
|   <h2>Encryption System</h2>                                             |
|   <hr>                                                                   |
|   Welcome to the Crypt.<br>                                              |
|   <br>                                                                   |
|   <form action='http://somewhere.net/crypt.php'>                         |
|     Enter some text to encrypt:                                          |
|       <input type='text' name='PLAINTEXT' value='Enter text to encrypt'> |
| <br>                                                                     |
|     Enter secret key: <input type='password' name='SECRETKEY'><br>       |
|     <input type='submit' name='ENCRYPT' value='Encrypt me!'>             |
|   </form>                                                                |
| </body></html>                                                           |
| ```                                                                      |
+--------------------------------------------------------------------------+

 

Note features of this page:

-   The form is the area of the page in between the \<form ...\> and
    \</form\> tags\
      

-   The \<form\> tag has an *action*attribute which contains the URL of
    the server-side application that will process the form data when the
    user clicks the submit button. \
      

-   The *method* attribute tells the browser how to transmit the
    information. Possible values are "get" and "post"

    -   The "get" method causes the browser to encode the form data in a
        query string, which is visible in the browser location bar, and
        is recorded in web server logs\
          

-   Tip: Use "post" most of the time. Use "get" only when no passwords
    are involved and you want the user to be able to bookmark the
    results.\
      

-   The form contains \<input\> tags which define input areas on the
    page. The following input areas are used:

    -   \<input **type='text'** name='PLAINTEXT' value='Enter text to
        encrypt'\>\
         This defines a single-line text input area with a default value
        'Enter text to encrypt'. \
          

    -   \<input **type='password'** name='SECRETKEY'\>\
         This defines a password input area. When the user types the
        key, asterisks will appear. No default value is provided.\
          

    -   \<input **type='submit'** name='ENCRYPT' value='Encrypt me!'\>\
         This defines a submit button labeled 'Encrypt me!'.\
          

-   Note that each input area except the submit button has a name
    assigned to it ('PLAINTEXT', 'SECRETKEY'). These are names that we
    make up, and they will be used by the servlet to retrieve the
    information from the form.

-   For a review of other input areas, see
    [http://www.w3schools.com/html/html\_forms.asp](http://www.w3schools.com/html/html_forms.asp)

 Creating HTML Prototypes
----------------------------

When designing web applications, it is common for developers to
construct HTML prototypes.

To create a client-side HTML prototype that does not need to be deployed
to a web server to be viewed, use these tips to enable navigation:

-   When linking between pages, be sure to use relative links

-   See /home/cps401/examples/htmlproto for button techniques


