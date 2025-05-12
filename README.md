
"""" Criterios de aceptación:
• El programa debe permitir agregar al menos 5 productos iniciales. FALTA
• Al consultar un producto, debe indicar si no existe en el inventario con un mensaje claro. YA
• La actualización de precios debe validar que el nuevo precio sea un número positivo. FALTA
• La eliminación de un producto debe confirmar su existencia antes de borrarlo. YA
• El cálculo del valor total del inventario debe ser preciso y mostrar el resultado con dos decimales. YA
• El código debe estar estructurado en funciones para cada operación y debe incluir comentarios explicativos. YA
• El código y los comentarios deben estar 100% sin excepción alguna en inglés. YA """ 


#Welcome message 
print("Welcome to our store system")


#Function to add products to inventory
def add_product(inventory):
    #Add a new product if no exist
    name = input("Product name: ").strip() #This function it is used for spaces
    # Check if the product already exists 

    if any(p['name'].lower() == name.lower() for p in inventory): #Verify if product exists
        print(f" '{name}' The product already exists. Please verify")
        return
    try: 
        # Request and convert price and quantity
        price = float(input("UNIT PRICE: "))
        quantity = int(input("AVAILABLE QUANTITY: "))
    except ValueError:
        # If there is an error in the conversion, it indicates it
        print("Incorrect. Price and quantity must be numbers.")
        return
    #add the product to inventory 
    inventory.append({'name':name, 'price':price, 'quantity':quantity})
    print(f"Product '{name}' add successfully.\n") #  Confirmation message



    #Product search function
def find_product(inventory, name):
   #Find product by name and return it
    for product in inventory: #Find product in inventory 
        if product['name'].lower() == name.lower():  #  comparison // capital letters
            return product
    return print(f"{name} the product does not exist") # If no find, return print()

    #this function find product specifically
def consult_product(inventory):
    #Query and display product information
    name = input("Product name: ").strip()
    product = find_product(inventory, name)  # Find product

    if product:
      # If found, display its information
        print("The product exists, these are its details: ")
        print(f"Product: {product['name']}")
        print(f"Price: {product ['price']:.2f}")
        print(f"Quantity: {product['quantity']}\n")
    else:
        print(f"This {name} undefind in inventory.\n")

# Function to update the price of a product
def update_price(inventory):
   #Update the price 
    name = input("name of the product to be updated: ").strip()
    product = find_product(inventory, name)

    if not product:
        print(f"This product undefind '{name}'.\n")
        return

    try:
        new_price = float(input("Enter new price: "))  # Enter new price 
    except ValueError:
        print("Incorrect price. Please, must be a number.\n")
        return
    if new_price <= 0:
            print("Values ​​cannot be less than $0.00")
    else:
        product['price'] = new_price  # Updated price
        print(f"Price'{name}' Updated to {new_price}.\n")

# Function to delete product 
def delete_product(inventory):
    #DELETE PRODUCT
    name = input("Name of the product to be removed: ").strip()
    product = find_product(inventory, name)

    if not product:
        print(f" The product does not exist'{name}'.\n")
        return

    inventory.remove(product)  # Remove the product from inventory
    print(f"Product '{name}' removed.\n")

# Function to calculate the total value of the inventory
def calculate_total(inventory):
    
    # Multiply price * quantity for each product and add everything together
    total_value = (lambda inv: sum(p['price'] * p['quantity'] for p in inv))(inventory)
    print(f"Total inventory value: ${total_value:.2f}\n")  # 2 decimal

# Function that displays the options menu
def show_menu():
    """Displays the options menu to the user."""
    print("===============INVENTORY MENU=================")
    print("1. Add product. ")
    print("2. Consult product")
    print("3. Update price")
    print("4. Delete product")
    print("5. Calculate total value")
    print("6. Go out")
    print("==============================================")

# Main function 
def main():
   #"Main function that controls the flow of the program."
    inventory = []  # Empty list where products are saved


    while True:
        show_menu()  # Menu
        choice = input("Select an option: ").strip()  # Ask the user for an option

        # Según la opción elegida, llama a la función correspondiente
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
            print("__See you later__")  # Closing message
            break  # Exit the loop
        else:
            print("Invalid option.\n")  # Handles invalid option

# Call main only if the file is executed directly
if __name__ == "__main__":
    main()


        

