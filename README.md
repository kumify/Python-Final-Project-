# Python-Final-Project-
Admin will have the following functionalities: ⬅️

👉 1. Add new food items. Food Item will have the following details:
        🔴 FoodID //It should be generated automatically by the application.
        🔴 Name
        🔴 Quantity. For eg, 100ml, 250gm, 4pieces etc
        🔴 Price
        🔴 Discount
        🔴 Stock. Amount left in stock in the restaurant.

👉 2. Edit food items using FoodID.

👉 3. View the list of all food items.

👉 4. Remove a food item from the menu using FoodID
class FoodItem:
    def _init_(self, name, quantity, price, discount, stock):
        self.food_id = None  # Will be generated automatically
        self.name = name
        self.quantity = quantity
        self.price = price
        self.discount = discount
        self.stock = stock


class Admin:
    def _init_(self):
        self.food_items = []
        self.next_food_id = 1

    def add_food_item(self, name, quantity, price, discount, stock):
        food_item = FoodItem(name, quantity, price, discount, stock)
        food_item.food_id = self.next_food_id
        self.next_food_id += 1
        self.food_items.append(food_item)
        print("Food item added successfully.")

    def edit_food_item(self, food_id, name, quantity, price, discount, stock):
        for food_item in self.food_items:
            if food_item.food_id == food_id:
                food_item.name = name
                food_item.quantity = quantity
                food_item.price = price
                food_item.discount = discount
                food_item.stock = stock
                print("Food item edited successfully.")
                return
        print("Food item not found.")

    def view_food_items(self):
        if not self.food_items:
            print("No food items available.")
            return
        print("List of all food items:")
        for food_item in self.food_items:
            print(f"Food ID: {food_item.food_id}")
            print(f"Name: {food_item.name}")
            print(f"Quantity: {food_item.quantity}")
            print(f"Price: {food_item.price}")
            print(f"Discount: {food_item.discount}")
            print(f"Stock: {food_item.stock}")
            print()

    def remove_food_item(self, food_id):
        for food_item in self.food_items:
            if food_item.food_id == food_id:
                self.food_items.remove(food_item)
                print("Food item removed successfully.")
                return
        print("Food item not found.")


# Example usage
admin = Admin()

admin.add_food_item("Pizza", "Large", 12.99, 0.2, 5)
admin.add_food_item("Burger", "Regular", 6.99, 0.1, 10)
admin.view_food_items()

admin.edit_food_item(1, "Pizza", "Medium", 10.99, 0.15, 3)
admin.view_food_items()

admin.remove_food_item(2)
admin.view_food_items()
0 comments on commit 512b817
