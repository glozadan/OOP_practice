# OOP_practice
Project from Codecademy "Learn Python 3" course

import datetime

#Basta Fazoolin’ with My Heart
class Menu:
  def __init__(self, name, items, start_time, end_time):
    self.name = name
    self.items = items
    self.start_time = start_time
    self.end_time = end_time
  
  def __repr__(self):
    return f"{self.name} menu is available from {self.start_time} to {self.end_time}"
  
  def calculate_bill(self, purchased_items):
    total_bill = 0
    for item in purchased_items:
      if item in self.items:
        total_bill += self.items[item]
    return f"The total bill is ${total_bill}."

#Creating the Franchises
class Franchise:
  def __init__(self, address, menus):
    self.address = address
    self.menus = menus
  
  def __repr__(self):
    return f"This franchise is located at {self.address}"
  
  def available_menus(self, time):
    time = datetime.time(time)
    available_menus_lst = []
    for menu in self.menus:
      if (time >= menu.start_time) and (time <= menu.end_time):
        available_menus_lst.append(menu)
        #print("The available menu(s) at {time} are {available_menus_lst}")
    return f"At {time} the menus are: {available_menus_lst}"

#Creating Businesses
class Business:
  def __init__(self, name, franchises):
    self.name = name
    self.franchises = franchises



#Brunch Menu
brunch_items = {'pancakes': 7.50, 'waffles': 9.00, 'burger': 11.00, 'home fries': 4.50, 'coffee': 1.50, 'espresso': 3.00, 'tea': 1.00, 'mimosa': 10.50, 'orange juice': 3.50}
brunch_start_time = datetime.time(11, 00)
brunch_end_time = datetime.time(16, 00)

brunch_menu = Menu("Brunch", brunch_items, brunch_start_time, brunch_end_time)
#print(brunch.end_time)
#print(brunch_menu) --> Brunch menu is available from 11:00:00 to 16:00:00


#Early bird Menu
early_bird_items = {'salumeria plate': 8.00, 'salad and breadsticks (serves 2, no refills)': 14.00, 'pizza with quattro formaggi': 9.00, 'duck ragu': 17.50, 'mushroom ravioli (vegan)': 13.50, 'coffee': 1.50, 'espresso': 3.00}
early_bird_start_time = datetime.time(15, 00)
early_bird_end_time = datetime.time(18, 00)

early_bird_menu = Menu("Early Bird", early_bird_items, early_bird_start_time, early_bird_end_time)


#Diner Menu
diner_items = {'crostini with eggplant caponata': 13.00, 'ceaser salad': 16.00, 'pizza with quattro formaggi': 11.00, 'duck ragu': 19.50, 'mushroom ravioli (vegan)': 13.50, 'coffee': 2.00, 'espresso': 3.00}
diner_start_time = datetime.time(17, 00)
diner_end_time = datetime.time(23, 00)

diner_menu = Menu("Diner", diner_items, diner_start_time, diner_end_time)


#Kids Menu
kids_items = {'chicken nuggets': 6.50, 'fusilli with wild mushrooms': 12.00, 'apple juice': 3.00}
kids_start_time = datetime.time(11, 00)
kids_end_time = datetime.time(21, 00)

kids_menu = Menu("Kids", kids_items, kids_start_time, kids_end_time)

#Testing the __repr__ method
#print(kids_menu)

#Testing the calculate_bill method
#test_bill = brunch_menu.calculate_bill(['pancakes', 'home fries', 'coffee'])
#print(test_bill) -> $13.5

#Testing with an Early Bird purchase
#test_early_bird_bill = early_bird_menu.calculate_bill(['salumeria plate', 'mushroom ravioli (vegan)'])
#print(test_early_bird_bill) -> $21.5

all_menus = [brunch_menu, early_bird_menu, diner_menu, kids_menu]

#First Franchise: Flagship Store
flagship_address = "1232 West End Road"
flagship_store = Franchise(flagship_address, all_menus)

#Second Franchise: New Installment
new_installment_address = "12 East Mulberry Street"
new_installment = Franchise(new_installment_address, all_menus)

#Testing the available_menus method in Franchise class
#print(new_installment.available_menus(17))


#Creating Business
first_business = Business("Basta Fazoolin' with my Heart", [flagship_store, new_installment])

#Crearing the menu of the franchise
arepas_items = {'arepa pabellon': 7.00, 'pernil arepa': 8.50, 'guayanes arepa': 8.00, 'jamon arepa': 7.50}
arepas_start_time = datetime.time(10, 00)
arepas_end_time = datetime.time(20, 00)
arepas_menu = Menu("Arepas", arepas_items, arepas_start_time, arepas_end_time)

#print(arepas_menu)

#Take a'Arepa Franchise
arepas_place = Franchise("189 Fitzgerald Avenue", [arepas_menu])

arepas_business = Business("Take a' Arepa", [arepas_place])
