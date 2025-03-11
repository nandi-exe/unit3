## Criteria C: Development

For my development section, i will explain the three most important functions that I used when creating the main home page, HomeScreenU.

### Load_Discount

My first major issue with development was finding a way to display the contents of the menu database. So far, all database implementation done in my application mainly dealt with undercover work, as seen in both the login system and registration system. On top of that, most of the work being completed in these two screens dealt with saving user-inputted data into the database, rather than dealing with external forces requesting information from the database.

For my HomeScreenU Class, I decided to add the function "load_discounts". The purpose for this was to lsit out all discounts listed in the "orders" table within the app's database.
The function connects to the FoodFinder's local SQLite database (myapp.sql) and creates a cursor. By executing an SQL query, it retrieves all in menu items where the discount column is greater than zero. These items are then sorted in descending order by the discount percentage, ensuring that the highest discounts appear first.

```
conn = sqlite3.connect("myapp.sql")
cursor = conn.cursor()
cursor.execute("SELECT dish_name, price, discount, restaurant_name FROM menu WHERE discount > 0 ORDER BY discount DESC")
rows = cursor.fetchall()

```
Fig 1. The extraction from the database.

The program then iterates through the collected data, extracting values for the extracting values for the name (dish name), price (dish price), discount (percentage discount), and restaurant (name of the restaurant offering the discount).
Initially, I was going to have a standard table list all the available discounts, but I was finding it difficult to implement and was not pleased with the result. in the end, I instead found a way to use MDCards to showcase the menu data.

```
for name, price, discount, restaurant in items:
    card = MDCard(
        size_hint=(None, None),
        size=("180dp", "120dp"),
        elevation=10,
        padding="8dp",
        spacing="8dp",
        orientation="vertical"
    )

```
Fig 2: Each discounted item is represented as an MDCard, with a fixed size (180dp x 120dp) and elevation (10) for a shadow effect.

The remainder of the code comprised of adding the dish details to the cards, as well as making the cards clickable. The clickability feature was added so that when ```show_item_details``` ran,  whatever card that was clicked on could expand and show more information for each individual dish.

```
box = BoxLayout(orientation="vertical", spacing="8dp", padding="8dp")
box.add_widget(MDLabel(text=name, bold=True, halign="center"))
box.add_widget(MDLabel(text=f"Price: ${price}", halign="center"))
box.add_widget(MDLabel(text=f"Discount: {discount}%", halign="center"))
card.add_widget(box)
card.bind(on_release=lambda instance, n=name, p=price, d=discount, r=restaurant: self.show_item_details(n, p, d, r))

```
The ```box.add widget``` adds each widget onto the homescreen, while the card.bind allows the cards to become clickable and expand, allowing the user to read more infomation on the product, such as it's location, the price drop, and also allows them to select whether or not they would want to purchase the item.

## Show_Item_Details

As mentioned in the previodu section, the show_item_details function generates a pop-up that displays detailed information about a selected menu item. This feature enhances the user experience by allowing them to see the original price, discounted price, and restaurant details before making a purchase.
In order to incentivise users unto buying the products displayed on the homescreen, the pop up shows the initial price the 
Since the database stores only the discounted price, the function reverses the discount to calculate the original price using:

```
original_price = round(price / (1 - discount / 100), 2)
```
By adding this to the MDBox, it shows consumers how much they're saving.

I then set up the content of the pop up. The program creates a vertical MDBoxLayout with adaptive height, spacing, and padding to maintain a clean look:

```
content = MDBoxLayout(
    orientation="vertical",
    spacing="5dp",
    adaptive_height=True,
    padding="10dp"
)
```
Each detail (dish name, prices, and restaurant) is displayed using MDLabel components:
```
content.add_widget(MDLabel(text=f"Dish Name: {name}", halign="center", size_hint_y=None))
content.add_widget(MDLabel(text=f"Original Price: ${original_price:.2f}", halign="center", size_hint_y=None))
```


### Add_To_Cart

The final component I will focus on is the add_to_cart function.
Most of the difficulties that stemmed from this section dealt with the cart, as passing on their contents to other screens became a frequent problem throughout the development of this application. 

First, it checks if the cart attribute exists within the class. If it does not, a new empty list is created to store cart items. This ensures that the cart can be used dynamically without prior initialization.

```
if not hasattr(self, 'cart'):
    self.cart = []

```
This mainly exists to avoid the program crashing due to the clas potentially not containing a cart. 
I then had the function he function append a dictionary containing the dish_name, price, and restaurant to the cart list. This is done to maintain the structure and keeps track of the main details of each added item. To finish it off, an additional function, load_cart(), is called to update the cart’s display in the UI. This ensures that any new additions are immediately reflected in the application interface, likely rendering the updated list of selected items.

```
self.cart.append({
    "dish_name": name,
    "price": price,
    "restaurant": restaurant
})
self.load_cart()
```

