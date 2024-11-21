# Homework_12.2



class Item:
    def __init__(self, name, price, description, dimensions):
        self.name = name
        self.price = price
        self.description = description
        self.dimensions = dimensions

    def __str__(self):
        return f"{self.name}, price: {self.price}"


class User:
    def __init__(self, name, surname, numberphone):
        self.name = name
        self.surname = surname
        self.numberphone = numberphone

    def __str__(self):
        return f"{self.name} {self.surname}"


class Purchase:
    def __init__(self, user):
        self.user = user
        self.products = {}
        self.total = 0

    def add_item(self, item, cnt):
        if item in self.products:
            self.products[item] += cnt
        else:
            self.products[item] = cnt
        self.calculate_total()

    def calculate_total(self):
        self.total = sum(item.price * quantity for item, quantity in self.products.items())

    def get_total(self):
        return self.total

    def __str__(self):
        items_description = "\n".join([f"{item.name}: {quantity} pcs." for item, quantity in self.products.items()])
        return f"User: {self.user}\nItems:\n{items_description}\nTotal: {self.total}"


lemon = Item('lemon', 5, 'yellow', 'small')
apple = Item('apple', 2, 'red', 'middle')

print(lemon)  # lemon, price: 5

buyer = User("Ivan", "Ivanov", "02628162")
print(buyer)  # Ivan Ivanov

cart = Purchase(buyer)
cart.add_item(lemon, 4)
cart.add_item(apple, 20)
print(cart)

cart.add_item(apple, 10)
print(cart)
