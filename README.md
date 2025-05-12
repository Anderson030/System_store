# Welcome message
print("Welcome to our store system")

# Function to add products to inventory
def add_product(inventory):
    """Add a new product if it does not already exist"""
    name = input("Product name: ").strip()  # Remove spaces

    # Check if the product already exists
    if any(p['name'].lower() == name.lower() for p in inventory):
        print(f"'{name}' The product already exists. Please verify.")
        return

    try:
        # Request and convert price and quantity
        price = float(input("UNIT PRICE: "))
        quantity = int(input("AVAILABLE QUANTITY: "))
    except ValueError:
        print("Incorrect. Price and quantity must be numbers.")
        return

    if price <= 0 or quantity < 0:
        print("Price must be positive and quantity cannot be negative.")
        return

    # Add the product to inventory
    inventory.append({'name': name, 'price': price, 'quantity': quantity})
    print(f"Product '{name}' added successfully.\n")

# Function to find a product by name
def find_product(inventory, name):
    """Find product by name"""
    for product in inventory:
        if product['name'].lower() == name.lower():
            return product
    return None

# Function to consult product
def consult_product(inventory):
    """Query and display product information"""
    name = input("Product name: ").strip()
    product = find_product(inventory, name)

    if product:
        print("The product exists, these are its details:")
        print(f"Product: {product['name']}")
        print(f"Price: ${product['price']:.2f}")
        print(f"Quantity: {product['quantity']}\n")
    else:
        print(f"This '{name}' is undefined in inventory.\n")

# Function to update the price of a product
def update_price(inventory):
    """Update the product price"""
    name = input("Name of the product to be updated: ").strip()
    product = find_product(inventory, name)

    if not product:
        print(f"This product is undefined: '{name}'.\n")
        return

    try:
        new_price = float(input("Enter new price: "))
    except ValueError:
        print("Incorrect price. Must be a number.\n")
        return

    if new_price <= 0:
        print("Price must be greater than $0.00")
    else:
        product['price'] = new_price
        print(f"Price of '{name}' updated to ${new_price:.2f}.\n")

# Function to delete a product
def delete_product(inventory):
    """Remove product from inventory"""
    name = input("Name of the product to be removed: ").strip()
    product = find_product(inventory, name)

    if not product:
        print(f"The product '{name}' does not exist.\n")
        return

    inventory.remove(product)
    print(f"Product '{name}' removed.\n")

# Function to calculate the total value of the inventory
def calculate_total(inventory):
    """Calculate the total value of inventory"""
    total_value = sum(p['price'] * p['quantity'] for p in inventory)
    print(f"Total inventory value: ${total_value:.2f}\n")

# Function that displays the options menu
def show_menu():
    """Displays the options menu to the user."""
    print("===============INVENTORY MENU=================")
    print("1. Add product")
    print("2. Consult product")
    print("3. Update price")
    print("4. Delete product")
    print("5. Calculate total value")
    print("6. Exit")
    print("==============================================")

# Main function
def main():
    """Main function that controls the flow of the program."""
    # Start with at least 5 initial products
    inventory = [
        {'name': 'Laptop', 'price': 1200.00, 'quantity': 5},
        {'name': 'Mouse', 'price': 25.50, 'quantity': 10},
        {'name': 'Keyboard', 'price': 45.00, 'quantity': 7},
        {'name': 'Monitor', 'price': 300.00, 'quantity': 4},
        {'name': 'USB Cable', 'price': 10.00, 'quantity': 20},
    ]

    while True:
        show_menu()
        choice = input("Select an option: ").strip()

        if choice == '1':
            add_product(inventory)
        elif choice == '2':
            consult_product(inventory)
        elif choice == '3':
            update_price(inventory)
        elif choice == '4':
            delete_product(inventory)
        elif choice == '5':
            calculate_total(inventory)
        elif choice == '6':
            print("__See you later__")
            break
        else:
            print("Invalid option.\n")

# Call main only if the file is executed directly
if __name__ == "__main__":
    main()
