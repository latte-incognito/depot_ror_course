# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
=============================
* TODO Chapter 7 Playtime

• The :length validation option checks the length of a model attribute. Add validation to the Product model to check that the title is at least ten characters.

• Change the error message associated with one of your validations.

* TODO Chapter 8 Playtime

•Add a date and time to the sidebar. It doesn’t have to update; just show the value at the time the page was displayed.

•Write some functional tests for the product management application using assert_select. The tests will need to be placed into the test/controllers/products_con- troller_test.rb file.

* TODO Chapter 9 Playtime

*Add a new variable to the session to record how many times the user has accessed the store controller’s index action. Note that the first time this page is accessed, your count won’t be in the session. You can test for this with code like this:
if session[:counter].nil? ...
If the session variable isn’t there, you need to initialize it. Then you’ll be able to increment it.

*Pass this counter to your template, and display it at the top of the catalog
page. Hint: the pluralize helper (definition on page 398) might be useful for forming the message you display.

*Reset the counter to zero whenever the user adds something to the cart.

*Change the template to display the counter only if the count is greater than five.