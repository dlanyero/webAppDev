

# The HTTP Protocol 
-----------------


Browsers (and other User Agents) talk to web servers using the HTTP
protocol.

-   HTTP - HyperText Transfer Protocol
-   Simple protocol consisting of
    -   HTTP request from browser to web server
    -   HTTP response from web server to browser
-   Our focus: Version 1.1, defined in RFC 2616
-   Current version is HTTP/2, defined in RFC 7540
    -   Adds encryption requirement and improves protocol efficiency

Protocol Overview
-----------------

-   Client/server protocol
    -   Client is a **user agent** such as a web browser or mobile app
    -   Server may be a web server, application server, or other custom
        server
-   Request-response protocol
    -   Client submits **HTTP request message**
    -   Server responds with **HTTP response message**

HTTP Request Message
--------------------

An HTTP request consists of a header and an optional body.

-   The request header begins with single line containing an [HTTP
    request
    method](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods),
    followed by a URL, followed by an HTTP protocol number.

    Example:

    ``` {.highlight}
    GET /stories/top/topstory.html HTTP/1.0
    ```

-   The GET method is used for most requests. Other commonly used
    methods include POST and HEAD.

-   After the first line of the request, several request header lines
    may follow, of the form

    *attribute-name*: *attribute-value*

    These header lines are used to transmit information about what
    browser version is issuing the request, as well as any cookies that
    have been previously sent to the browser from this web server.

-   After all of the header lines have been transmitted, a blank line is
    sent.

-   For some verbs, such as POST, the request may include a body with
    additional information (such as data submitted in a form). That
    information is sent after the blank line.

Here is a sample HTTP request, sent from a Mozilla browser when
requesting the URL http://www.cs.bju.edu/portal/index.asp:

``` {.highlight}
GET /portal/index.asp HTTP/1.1
Host: www.cs.bju.edu
User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.4) Gecko/20030624
Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,
        video/x-mng,image/png,image/jpeg,image/gif;q=0.2,*/*;q=0.1
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Cookie: ASPSESSIONIDQARQQDQA=GGELAOOBANPOLIJMBKCGONCI; ASPSESSIONIDAASSTCTD=PBJBCOOBAPLFMNFJCKEMFFLF
```

HTTP Response Message
---------------------

After the browser sends its request, it waits for the web server to
respond.

The web server sends an HTTP response.

-   The first line contains an HTTP response code consisting of an HTTP
    version number, a status code, and a textual description.

-   Following the response code, the server sends a series of response
    headers, in a format similar to request headers. Some important
    headers include content-type and content-length.

-   After the headers comes a blank line. Then, the server transmits the
    body of the response.

Here is a sample HTTP response, sent from an IIS server in response to
the previous request for URL http://www.cs.bju.edu/portal/index.asp:

``` {.highlight}
HTTP/1.x 200 OK
Server: Microsoft-IIS/5.0
Date: Sat, 17 Jan 2004 15:07:20 GMT
X-Powered-By: ASP.NET
Content-Length: 7262
Content-Type: text/html
Cache-Control: private
```

More on Response Codes
----------------------

Common response codes include:

-   200 (Ok): the server was able to successfully retrieve the requested
    resource.

-   404 (Not found): the server cannot find the requested resource. This
    is the response a browser receives when a user clicks a “broken
    link”. The server usually includes an HTML message in the response
    describing the problem and explaining how the user might be able to
    find what he is looking for.

-   302 (Resource moved): tells the browser that the resource has been
    moved to a different location. The server also returns the new URL
    in the response headers, and the browser then automatically attempts
    to load the new URL. The user never sees anything to indicate that
    the resource has been moved.

More on MIME Types
------------------

A URL often refers to a document containing HTML, but it might also be
an image, a sound clip, a movie, or other resource.

When the web server transmits the requested resource, it tells the
browser what kind of content the response body contains using the
content-type response header. This header specifies the MIME type of the
content.

RFC 2046 specifies the format of MIME types, and the IANA website
maintains a registry of all registered MIME types, including text/plain,
text/html, image/gif, image/jpeg, etc. The web server usually uses the
file name extension (.html, .txt, .gif, etc.) to determine the MIME
type. Files of type .exe, as well as files whose extension is
unrecognized, are assigned a MIME type of
application/binary-octet-stream. When browsers receive these files, they
usually present a “save file?” dialog.

Form Submission
---------------

When a user submits a form,

1.  The browser encodes the form field values using URL encoding.
2.  The browser computes a destination URL for the form submission,
    using the form’s *action* attribute (which may contain a relative or
    absolute URL).
3.  The browser transmits the form name/value pairs in the HTTP request
    message as follows:
    -   If the form’s method=”GET”, the browser appends a query string
        containing the form data to the path of the destination URL.
    -   If the form’s method=”POST”, the form data is placed in the body
        of the HTTP request message and transmitted to the destination
        URL.


