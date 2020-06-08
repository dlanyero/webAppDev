[Home](https://protect.bju.edu/cps/courses/cps404/index.html)
[Schedule](https://protect.bju.edu/cps/courses/cps404/schedule.html)
[Resources](https://protect.bju.edu/cps/courses/cps404/Resources.html)
[Dr. Schaub](https://protect.bju.edu/cps/courses/cps404/Schaub.html)
[Syllabus](https://protect.bju.edu/cps/courses/cps404/docs/CpS404Syllabus.pdf)
[Grades](https://bju.instructure.com/courses/11957/grades)
[Submit](https://protect.bju.edu/cps/submit/upload/)

© 2020. All rights reserved.

### [CpS 404](https://protect.bju.edu/cps/courses/cps404/index.html "Home") Internet App Development {.masthead-title}

Lab 1: Node.js Orientation {.page-title}
==========================

Objectives
==========

-   Learn to create and debug Node.js applications
-   Learn to install and use third party Node.js modules

Prerequisites
=============

-   Install the software specified on the [Course
    Software](https://protect.bju.edu/cps/courses/cps404/docs/CourseSoftware.html)
    page.
-   Read Chapter 2 of *Pro Node.js for Developers* (see
    [Resources](https://protect.bju.edu/cps/courses/cps404/Resources.html))
    through p. 15.

Instructions
============

1.  Work through [this tutorial on VSCode and
    Node.js](https://code.visualstudio.com/Docs/runtimes/nodejs). You
    are welcome to use your preferred editor instead of VSCode.

2.  Create a folder named lab1 on your computer. Open the folder in VS
    Code. Copy the readfile\_sync.js sample program from the class
    examples into that folder and review the code. Use the node command
    to run it. Provide the filename of a text file as a command line
    argument; it should display the contents of the file.

3.  The Dallas police department provides a web service that allows you
    to retrieve a list of active police calls:

    https://www.dallasopendata.com/resource/are8-xahz

    Download the data set via this URL:

    https://www.dallasopendata.com/resource/are8-xahz.csv

    Review the data in a text editor. As is typical in a comma-delimited
    data file, the first row contains field names.

4.  Read about the Node.js module
    [csv-string](https://www.npmjs.com/package/csv-string). It parses
    comma-delimited files. It is not a part of the core Node.js library;
    you must use the npm command to install it into your lab1 folder
    (see the Installation section of the csv-string documentation). When
    you install it, a node\_modules folder should be created in your
    lab1 folder, and you should see the csv-string module inside. (You
    can ignore npm warnings about a missing package.json file.)

5.  Rename readfile\_sync.js to lab1.js. Add a require statement to the
    top to import the module (review the module documentation for an
    example if you need help). Alter the program so that it displays a
    list of all of the values in the date\_time and nature\_of\_call
    fields for those records where the division value is ‘Northeast’.
    Use the parse() function in the csv-string module to assist with
    parsing the data. The output should be formatted as follows:

    ``` {.highlight}
     2017-01-19T14:42:00.000 - DASV-Dist Active Shooter Veh
     2017-01-19T14:42:00.000 - DASV-Dist Active Shooter Veh
     2017-01-19T14:35:00.000 - DAEF-Dist Armed Encounter Foot
    ```

Submission
==========

There is nothing to submit. This is an ungraded assignment.
