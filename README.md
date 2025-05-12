
Welcome to our store system.

Then, the main() function is called, which controls the program flow. It initializes an empty list called inventory and repeatedly shows a menu using the show_menu() function.

Function show_menu()
This function displays a menu with 6 options:

Add product

Consult product

Update price

Delete product

Calculate total value

Exit

Each option is validated using an if/elif structure and calls the corresponding function.

Option 1: add_product()
Prompts the user for a new product name.

Uses strip() to remove surrounding spaces.

Checks if the product already exists (case-insensitive).

If it exists, shows a warning message.

If not, requests unit price (float) and quantity (int) using try.

Validates that price > 0 and quantity is non-negative.

If all is valid, appends the product to the inventory and confirms success.

Option 2: consult_product()
Requests the product name.

Uses find_product() to search.

If found, prints its details (name, price, quantity).

If not found, shows a message indicating absence in inventory.

Option 3: update_price()
Requests the name of the product to update.

Uses find_product() to locate it.

If not found, shows an error.

If found, asks for new price using a try block.

Validates that the price is greater than 0.

If valid, updates the price and confirms the change.

Option 4: delete_product()
Asks for the name of the product to delete.

Uses find_product() to confirm existence.

If it doesn’t exist, shows a message.

If it exists, removes it from inventory and confirms.

Option 5: calculate_total()
Calculates the total value by summing price * quantity for each product.

Displays the total with two decimal places.

Option 6: Exit
Shows a farewell message and exits the loop.

Initial products
The inventory list starts with 5 predefined products when main() begins:

Laptop

Mouse

Keyboard

Monitor

USB Cable















ChatGPT puede cometer errores. Comprueba la información 
