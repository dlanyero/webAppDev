

# Lab 2: Asynchronous Programming with Node.js 
============================================

Objectives
==========

-   Learn to use the Node.js debugger
-   Learn to use asynchronous functions in the Node.js API

Prerequisites
=============

-   Review the course slides on the Node.js execution model
-   Skim chapter 7 of *Pro Node.js for Developers* (see
    [Resources](https://protect.bju.edu/cps/courses/cps404/Resources)),
    and chapter 11 pp. 178 - 183.

Instructions
============

1.  Read about [debugging Node.js programs in Visual Studio
    Code](https://code.visualstudio.com/Docs/editor/debugging) and watch
    [this short video](https://youtu.be/rIZMFEE9uqI) for a demo. Then,
    use the Visual Studio Code debugger to step through your lab1.js
    program, inspect variable values, etc. 2 points.

2.  Save your lab1.js program as **lab2http.js**. Then, redesign the
    program so that it downloads the [Dallas Police data
    set](https://www.dallasopendata.com/resource/are8-xahz.csv), uses
    the CSV module to parse it, and displays the same output as lab1.

    Use the http.get() method to download the data (see the
    http\_request.js example we went over in class). No error handling
    is needed. 3 points.

3.  Locate the request module on npmjs.org and read about how to use it.
    Install it using npm, and create a second version of your program
    named **lab2request.js** that uses the request module instead of the
    http module to download the data. Handle errors gracefully. Perform
    the following error handling tests and document the results in the
    lab report:

    -   Change the URL so that the server name is not found (connect
        failure)
    -   Change the URL so that you get a response 404 (not found)

    5 points.

4.  Create a third version of your program named **lab2mydownload.js**.
    In this version, you are to define a function

    ``` {.highlight}
     function download(url, callback)
    ```

    This asynchronous function should use the http.get() method to
    download data from the indicated url and pass the downloaded data to
    the callback function. The function should check the
    response.statusCode, and if it is not 200, report an error to the
    callback using code like this:

    ``` {.highlight}
    callback(new Error("Received response code: " + response.statusCode))
    ```

    The function should also detect and report failures to connect,
    etc., to the callback. Perform the error scenario tests from step 3
    above to verify that all of this error handling works correctly, and
    document these tests carefully in the report.

    Rewrite the main program to use your download() function. 10 points.

Submission
==========

Upload your code to github
