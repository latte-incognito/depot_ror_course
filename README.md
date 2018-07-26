# README
=============================
* [DONE] Chapter 7 Playtime

• [DONE] The :length validation option checks the length of a model attribute. Add validation to the Product model to check that the title is at least ten characters.

• [DONE] Change the error message associated with one of your validations.

* [DONE] Chapter 8 Playtime

•[DONE] Add a date and time to the sidebar. It doesn’t have to update; just show the value at the time the page was displayed.

•[DONE]Write some functional tests for the product management application using assert_select. The tests will need to be placed into the test/controllers/products_con- troller_test.rb file.
https://www.rubydoc.info/github/rails/rails-dom-testing/Rails/Dom/Testing/Assertions/SelectorAssertions

* TODO Chapter 9 Playtime

* Add a new variable to the session to record how many times the user has accessed the store controller’s index action. Note that the first time this page is accessed, your count won’t be in the session. You can test for this with code like this:
if session[:counter].nil? ...
If the session variable isn’t there, you need to initialize it. Then you’ll be able to increment it.

* Pass this counter to your template, and display it at the top of the catalog
page. Hint: the pluralize helper (definition on page 398) might be useful for forming the message you display.

* Reset the counter to zero whenever the user adds something to the cart.

* Change the template to display the counter only if the count is greater than five.

* TODO Chapter 10 Playtime

* Create a migration that copies the product price into the line item, and change the add_product() method in the Cart model to capture the price whenever a new line item is created.
* Write unit tests that add both unique products and duplicate products to a cart. Assert how many products should be in the cart in each instance. Note that you’ll need to modify the fixture to refer to products and carts by name—for example, product: ruby.
* Check products and line items for other places where a user-friendly error message would be in order.
* Add the ability to delete individual line items from the cart. This will require buttons on each line, and such buttons will need to be linked to the destroy() action in the LineItemsController.
* We prevented accessing other user’s carts in the LineItemsController, but you can still see other carts by navigating directly to a URL like http://local- host/carts/3. See if you can prevent accessing any cart other than than one currently stored in the session.