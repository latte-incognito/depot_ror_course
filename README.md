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


* TODO Chapter 11 Playtime
* The cart is currently hidden when the user empties it by redrawing the entire catalog. Can you change the application to remove it using an Ajax request, so the page doesn’t reload?
* Add a button next to each item in the cart. When clicked, it should invoke an action to decrement the quantity of the item, deleting it from the cart when the quantity reaches zero. Get it working without using Ajax first and then add the Ajax goodness.
* Make images clickable. In response to a click, add the associated product to the cart.
* When a product changes, highlight the product that changed in response to receiving a broadcast message.


* TODO Chapter 12 Playtime
Here’s some stuff to try on your own:
1.
https://github.com/rails/activemodel-serializers-xml#readme

* Get HTML- and JSON-formatted views working for who_bought requests. Experiment with including the order information in the JSON view by rendering @product.to_json(include: :orders). Do the same thing for XML using ActiveModel::Serializers::Xml.1
* What happens if you click the Checkout button in the sidebar while the checkout screen is already displayed? Can you find a way to disable the button in this circumstance?
* The list of possible payment types is currently stored as a constant in the Order class. Can you move this list into a database table? Can you still make validation work for the field?

* TODO Chapter 13 Playtime
* Check is not the only payment type, and routing number is not the only field that is dynamically inserted or deleted based on the payment type. Extend the system test to include other choices and other fields.
* Add a test to verify that the Add to Cart and Empty Cart buttons reveal and hide the cart, respectively.
* Add a test of the highlight feature you added in Iteration F3: Highlighting Changes, on page 164.

* TODO lol mb attach stripe or braintree

* TODO Chapter 14 Playtime

* Add a ship_date column to the orders table, and send a notification when this value is updated by the OrdersController.
* Update the application to send an email to the system administrator— namely, yourself—when an application failure occurs, such as the one we handled in Iteration E2: Handling Errors, on page 138.
* Modify Pago to sometimes return a failure (OpenStruct.new(succeeded?: false)), and handle that by sending a different email with the details of the failure.
* Add system tests for all of the above.

* TODO Chapter 15 Playtime
* Modify the user update function to require and validate the current password before allowing a user’s password to be changed.
* When the system is freshly installed on a new machine, no administrators are defined in the database, and hence no administrator can log on. But, if no administrator can log on, then no one can create an administrative user.
* Change the code so that if no administrator is defined in the database, any username works to log on (allowing you to quickly create a real administrator).
* Experiment with rails console. Try creating products, orders, and line items. Watch for the return value when you save a model object—when validation fails, you’ll see false returned. Find out why by examining the errors:
>> prd = Product.new
=> #<Product id: nil, title: nil, description: nil, image_url: nil, created_at: nil, updated_at: nil, price: #<BigDecimal:246aa1c,'0.0',4(8)>>
>> prd.save
=> false
>> prd.errors.full_messages
=> ["Image url must be a URL for a GIF, JPG, or PNG image",
      "Image url can't be blank", "Price should be at least 0.01",
      "Title can't be blank", "Description can't be blank"]
• Look up the authenticate_or_request_with_http_basic() method and utilize it in your :authorize callback if the request.format is not Mime[:HTML]. Test that it works by accessing an Atom feed:
  curl --silent --user dave:secret \
    http://localhost:3000/products/2/who_bought.atom
• We’ve gotten our tests working by performing a login, but we haven’t yet written tests that verify that access to sensitive data requires login. Write at least one test that verifies this by calling logout() and then attempting to fetch or update some data that requires authentication.