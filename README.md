The program begins with a welcome message

print("Welcome to our store system")


Call the main() function.

Next, the main() function is called. It controls the entire program flow.it initializes an empty list called "inventory" and displays a menu using the show_menu() function. This function is repeated to add more than 5 products.

 inventory = [
        {'name': 'Laptop', 'price': 5000000.00, 'quantity': 5},
        {'name': 'Mouse', 'price': 30000.00, 'quantity': 10},
        {'name': 'Keyboard', 'price': 45000.00, 'quantity': 7},
        {'name': 'Monitor', 'price': 300000.00, 'quantity': 4},
        {'name': 'USB Cable', 'price': 10000.00, 'quantity': 20},
    ]


-----------------------------------------------------------
show_menu() Displays 6 options:

print("1. Add product")
print("2. Consult product")
print("3. Update price")
print("4. Delete product")
print("5. Calculate total value")
print("6. Exit")


Each option shows me an if/elif structure and calls the function based on the option selected by the user.
------------------------------------------------

Option 1: add_product():

Use strip() to remove spaces.
Checks if the product already exists 
If it already exists, return a message. (The product already exists. Please verify.)
If not exists, REQUEST the unit price and quantity using try.
Checks that the price is greater than 0 and that the price is not a negative value.
If everything is correct, add it to the empty list.

-------------------------------------------------------

Option 2 Consult product:

If found, a message and product details are printed.
If not found, it displays a message indicating that there is no product.

-----------------------------------------------------------
Option 3 update_price()

Use find_product() to search.
If it's not found, it displays an error message.
If it's found, request the new price using the try command.
Check that the price is greater than 0.
If all else fails, update the price.
-----------------------------------------------------------
Option 4: delete_product() Requests the name of the product to delete

Uses find_product() to see if it exists.
If it doesn't, display a message.
Delete the product and return to the menu.
--------------------------------------------------------
Option 5: calculatetotal() Calculates all products with a lambda Displays the total with two decimal places.

---------------------------------------------------------
Option 6: If you choose this option you exit the program, ending with a message







