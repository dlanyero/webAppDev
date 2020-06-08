
# Exercise 1: HTML Prototyping 
-------------------------------

**Estimated time to complete: 4-6 hours**

Overview
--------

In this assignment, you construct an HTML prototype for a multi-page web
application. Your prototype consists of a collection of HTML pages that
the user can view and navigate by opening them with a web browser
directly from the local filesystem (no deployment to a web server). The
pages contain navigation buttons that move the user from page to page.

You will want a good HTML/JavaScript editor for this assignment. I
recommend [Visual Studio Code](https://code.visualstudio.com/), but you
can use any programmer’s editor you wish.

Basic Prototype 
---------------------------

Construct the following pages in HTML:

### index.html

![](https://github.com/dlanyero/webAppDev/blob/master/Wiki/exercises/exercise1/index.jpg)

Notes:

-   Use [this
    graphic](https://protect.bju.edu/cps/courses/cps404/exercises/ex1/wallyswallofwisdom.jpg).
-   Make the *Write on the Wall* button navigate to editpost.html. You
    can use a little JavaScript event handler:

    ``` {.highlight}
    <input type="button" onclick="location='editpost.html'">
    ```

-   Use CSS or a table to center the image and the content in the
    browser, as shown.

### editpost.html 

![](https://github.com/dlanyero/webAppDev/blob/master/Wiki/exercises/exercise1/editpost.jpg)

Notes:

-   The entries in the Category dropdown should be Love, Computer
    Support, Dorm Life, Family, Food. The associated values should be
    LOVE, CS, DL, FAM, FOOD.

-   Give names to all input controls. Make the default state for all
    input controls as shown in the illustration. Make sure the radio
    buttons work properly (only one of the values can be selected).

-   Clicking the Continue button should cause the previewpost.html page
    to appear, with all of the submitted form values in the query
    string. Note that the submitted form values need not appear in the
    body of previewpost.html (that would require more JavaScript coding
    than I expect from you at this stage).

-   Clicking Cancel should display index.html. Use a little JavaScript
    for this purpose (see how the About button was done in the sample
    prototype in the Class Files for the necessary technique).

-   Use a two-column borderless table to lay out the form.

### previewpost.html

![](https://github.com/dlanyero/webAppDev/blob/master/Wiki/exercises/exercise1/previewpost.jpg)

Notes:

-   Clicking *Finish* or *Cancel* should display index.html
-   Clicking *Edit* should display editpost.html

### Guidelines

-   Use only relative URL’s in your IMG tags.
-   Write clean, well-formed HTML. To ensure well-formed HTML, I suggest
    using a site like https://www.10bestdesign.com/dirtymarkup/ to clean
    up your markup (indent with spaces, not tabs).

Paypal Integration 
------------------------------

Creating sites that allow users to make payments is an important
practical skill. For full credit, add e-commerce capabilities to the
prototype.

The prototype will allow users to purchase framed prints of selected
quotes. The shopping cart and payments will be handled via Paypal, which
has a very easy-to-use e-commerce integration for websites that requires
no server-side scripting. You will use the Paypal Sandbox, which
requires no credit card to sign up, and which allows you to test sending
payments with fake credit card numbers.

![](./Exercise%201_%20HTML%20Prototyping%20·%20CpS%20404_files/paypal.jpg)

1.  Begin by logging in to Paypal at https://developer.paypal.com (or
    creating a new Paypal account, if you don’t have one). No credit
    card is needed for this.

2.  Paypal offers a number of ways for a website to integrate with their
    payment system. For this assignment, use the HTML Buttons option
    ([read about
    it](https://developer.paypal.com/docs/integration/web/)). Note that
    you do not need a business account to create buttons for the sandbox
    accounts.

3.  Follow the instructions in the [Paypal
    documentation](https://developer.paypal.com/docs/integration/web/)
    in the “PAYMENT BUTTONS \> Integration Guide \> Test Your Payment
    Buttons” section to create accounts for both a Buyer and a Seller.

4.  Modify the index.html page so that an Add to Cart button is
    displayed next to each item, as shown below. Clicking on the button
    should trigger a form submission to **www.sandbox.paypal.com** and
    add a product to the Paypal shopping cart. Test the form. Clicking
    on a button should cause a Paypal shopping cart to appear showing
    the product with the selected quote, like “Quote-The quick brown
    fox.”

5.  Refer to the “PAYMENT BUTTONS \> HTML Reference \> Variable
    Reference” to determine how to charge a \$5 shipping fee for each
    item purchased. For example, if the user orders 2 of one quote and 1
    of another, the total shipping charge should be \$15. Add these
    variables, and verify that the shipping is correctly calculated.

6.  Using your website, purchase 3 copies of one quote, and 2 of the
    other. Check out and complete the purchase using your test Buyer
    account. After completing the purchase, logout of the test buyer
    account, and login to the test Seller account. You should see the
    purchase there. Click on the Details link to see the transaction
    details, and make a screen shot for your report as proof that you
    successfully completed a transaction.

Submission
----------

-  Upload your code to github and create a brief report indicating what you were able to accoomplish, what works and what does not. 



