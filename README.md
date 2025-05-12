Criterios de aceptación:
• El programa debe permitir agregar al menos 5 productos iniciales.
• Al consultar un producto, debe indicar si no existe en el inventario con un mensaje claro.
• La actualización de precios debe validar que el nuevo precio sea un número positivo.
• La eliminación de un producto debe confirmar su existencia antes de borrarlo.
• El cálculo del valor total del inventario debe ser preciso y mostrar el resultado con dos
decimales.
• El código debe estar estructurado en funciones para cada operación y debe incluir
comentarios explicativos.
• El código y los comentarios deben estar 100% sin excepción alguna en inglés


# System_store
system

#Gestionar el inventario de una tienda:
#productos disponibles, su cantidad y precios actualizados, además de calcular el valor
#total del inventario.  [] [][] []


#Welcome message 
print("Welcome to our store system")


#Function to add products to inventory
def add_product(inventory):
    #Add a new product if no exist
    name = input("Product name: ").strip() #This function it is used for spaces
    # Check if the product already exists (ignores case)

    if any(p['name'].lower() == name.lower() for p in inventory): #Verify if product exists
        print(f"{name}The product already exists. Please verify")
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
    print(f"Product{name} add successfully.\n") #  Confirmation message



    #Product search function
    def fine_product(inventory,name):
        #Fine product whit name
        for product in inventory:
            if product ['name'].lower()











inventory = []  # Empty list where products are stored





