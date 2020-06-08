

Program 1: Fun with Slack {.page-title}
=========================



Objectives
==========================================================================================

-   Develop a command-line Slack client in Node.js

Overview
======================================================================================

Slack is a collaboration platform that is a competitor to Microsoft
Teams. Slack has a web API that you will utilize in this assignment to
create a command-line interface for accessing a Slack workspace. The
interface will allow the user to post, browse and search messages from
the command line. This kind of utility would be useful in a shell script
that automates Slack operations.

**Note:** Although there are npm modules that provide a nice wrapper
around the Slack web API, you may not use them. The point of this
assignment is to practice interacting with a web service from Node.js
without relying on someone else having written a Node.js library for the
service. However, you may use the request module to streamline your HTTP
requests.

Specification
================================================================================================

Create a program named slack.js. When run without any command line
arguments, it should display a short help message that lists the
commands that it supports, and then exit. See below for the commands.

When it starts, slack.js should retrieve the value of the SLACK\_TOKEN
environment variable (from the process.env map) and use it as the
authorization token for web requests. If SLACK\_TOKEN is missing or
empty, display an error message and exit immediately.

If SLACK\_TOKEN is present, slack.js should perform the command
indicated by its command line arguments. The commands are given below.

Commands
--------------------------------------------------------------------------------------

show-channels

``` 
node slack.js  show-channels
```

The show-channels option should display a list of channel names and
topics. Format the output as follows:

``` 
Channel name  Topic
------------  -------------------------------------------------
general       Course announcements and work-based matters
random        Non-work banter and water cooler conversation
```

show-users

``` 
node slack.js  show-users
```

The show-users option should display a list of users:

``` 
User          Name
------------  -------------------------------------------------
fred          Fred Jones
slackbot      slackbot
```

post

``` 
node slack.js  post <channel-name> <message>
```

The post option should post a message to the specified channel. For
example:

``` 
node slack.js  post general "This is a nifty utility."
```

On successful post, display “Message successfully posted.”

get-posts

``` 
node slack.js  get-posts <channel-name> [<search-word>]
```

The get-posts option should display a list of messages in the specified
channel. Note that the channel name, not the channel id, is provided. If
the \<search-word\> is specified, display only messages containing the
word; otherwise, display all messages.

Example:

``` 
node slack.js  get-posts general
```

displays all messages in the general channel, while

``` 
node slack.js  get-posts random cool
```

displays messages in the random channel containing the word ‘cool’.

Format the output with the username and the message text as follows:

``` 
@fred: It's a grand day

@joliet: What's up?
```

Warmup
==================================================================================

1.  Read about the [Slack API](https://api.slack.com/web) and then set
    up your own Slack team for testing purposes by going to slack.com
    and choosing the “Create a new team” option. Login to your test team
    and make a few posts.

2.  To interact with your test team via the Slack API, I recommend using
    the legacy [Slack test token
    generator](https://api.slack.com/custom-integrations/legacy-tokens)
    to generate a test authentication token (don’t go down the OAuth
    path, which is for authentication of browser-based apps). You will
    need to include this token with your request (see
    [Authentication](https://api.slack.com/web#authentication) for
    details).

3.  Next, spend some time exploring the [Slack API
    Methods](https://api.slack.com/methods). Use the test interface to
    invoke the test methods from your browser. Use your browser’s
    developer tools to inspect the network traffic as you perform these
    tests. Explore using the *channels.list* method to list the
    channels, *chat.postMessage* to post a message in a channel,
    *channels.history* to retrieve posts made in a channel, and
    *users.list* to list the users.

    Note that the Slack API has evolved over the years and in some cases
    there are multiple methods that can perform some of these tasks. I
    recommend the ones listed here for simplicity.

4.  Next, write a test Node.js program that invokes the *channels.list*
    method and displays the id and name of each channel to work out the
    techniques you’ll need. Use the HTTP POST technique.

Level 2
==============================================================================================

Implement the *show-channels*, *show-users*, and *post* commands.

Detect and handle errors gracefully.

Level 3
==============================================================================================

In addition to the Max 75 Level, implement the *get-posts* command. When
calling *channels.history*, use a count of 5, and use the paging
mechanism described in the API documentation for *channels.history* to
retrieve all of the messages.

[](https://protect.bju.edu/cps/courses/cps404/programs/program1.html#max-95-level)Max 95 Level
==============================================================================================

Organize the code that communicates with the Slack service into an
object-oriented module that defines a JavaScript “class” named *Slack*.
Define the module in a file named slack-api.js in the same directory as
slack.js, and require() it in your main program. See
nodejs/module\_demo\_oo in the class files for a small example that
demonstrates this organization.

Design your API with a separate method for each command listed above.
Your API must be reusable; there should be no program-specific behavior
in your slack-api.js file (i.e., console.log() should not be used in
your API).

For example, to support the show-channels command, you might design a
method getChannels() that pulls a list of channels from the Slack
service, puts them into a list of objects, and returns them to the
caller, which might invoke the method like this:

``` {.highlight}
slack = require('./slack-api');
var s = new slack.Slack();

s.getChannels(function(err, channels) {
    if (err) { /* handle error */ }

    // display results
    var channel;
    for (channel in channels) {
        console.log(channel.name + "  " + channel.topic);
    }
});
```

Max Level
================================================================================================

Read about promises and async/await in these tutorials:

-   [JavaScript ES 2017: Learn Async/Await by
    Example](https://codeburst.io/javascript-es-2017-learn-async-await-by-example-48acc58bad65)
-   [Writing neat asynchronous Node JS code with Promises &
    Async/Await](https://medium.com/@tkssharma/writing-neat-asynchronous-node-js-code-with-promises-async-await-fa8d8b0bcd7c)

Then, write a separate version of your program that uses promises or
async/await to improve your code in the following ways:

-   Redesign the Slack class to allow its methods to be called with
    await
-   Use await or promise-based API’s to call asynchronous methods

Call these file versions slack-xc.js and slack-api-xc.js.

Style Requirements
==========================================================================================================

-   Put a comment at the top of the program with your name, the
    assignment, a brief description
-   Use good style (meaningful variable and function names, appropriate
    white space and indentation)
-   Define functions to avoid duplicate code.
-   Define all functions first, and put the main script at the end
-   Write a brief header comment for all (named) functions that you
    define

Grading Criteria
======================================================================================================

See the course syllabus for grading criteria.

Submission
==========================================================================================

-   Create a report indicating what you were able to complete and submit your code to upload your code to github


