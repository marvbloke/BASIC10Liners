--= FAST FOOD FRED =--

System Requirements: Sinclair ZX Spectrum 48k/+/128k/+2/+3/Next 

Written by Matthew Begg for the 2026 BASIC 10-Liner Competition (EXTREME-256 category)
Licence: CC BY-SA 4.0

Players: 1

--= INTRODUCTION =--

Welcome to the high-stakes world of budget catering! You are Fred, the proud owner of a bustling Middlesbrough fast-food joint. Your mission is simple but challenging: earn as much money as possible between Tuesday and Saturday.

--= LOADING INSTRUCTIONS =--

- Spectrum 48k/+ - type LOAD "" then ENTER. That's 'J' then Symbol Shift+P twice, then ENTER.
- Spectrum 128k/+2/+3/Next - choose "Tape Loader" or "Loader" then ENTER.
- Emulator (e.g. Fuse): load the "Fast Food Fred.tap" file into your emulator then use the instructions above.

The game will load and automatically start.

--= HOW TO PLAY =--

The shop is open Tuesday to Saturday from 4pm to 11pm daily. During these hours, customers place orders (labelled 'a', 'b', or 'c') which appear on the left side of your screen. Each order lists specific menu items and quantities — ranging from standard burgers to local favourites.

To succeed, you must become a master of the menu:

Prepare Ingredients: Use the number keys to cook specific items (e.g., press '4' for cheese). 

Consult the Recipes: Not sure what goes into a Parmo? Use the 'o' and 'p' keys to flip through your recipe book at the bottom right. For example, an order comes in for 2x Hamburger, 2x Onion Rings, 1x Chips - you would need to cook 2x beef, 4x bread, 2x onion and 1x potatoes.

Time Your Prep: Every ingredient takes time to prepare, so plan ahead — especially since you can only hold three orders at once.

Fulfil Orders: Once you have all the right ingredients prepared, press the letter corresponding to the order ('a', 'b', or 'c') to serve it. The border will turn white while your order is checked by the customer. If the border turns green, you’ve successfully completed the order and you earn your money. If it turns red, you made a mistake (it still uses up the ingredients but the order remains unfulfilled).

At the end of each shift, you will see a summary of your performance. Watch out for waste — any ingredients left over at 11pm will cost you 50p each. If your total bank balance ever drops below £0, your business is finished.

Keep your cool, hold down the 'F' key for "Fast Mode" during the quiet lulls, and see if you can crack the £150+ "Fantastic" rating by the end of Saturday night:

- £0-£49: rubbish
- £50-£99: not bad
- £100-£149: that’s good
- £150+: fantastic!

Tip 1: best not to start preparing a big order after 10pm

Tip 2: there’s no penalty for ignoring an order. That’s tactical because some orders are more complicated than others. But they all equally clog up one of only 3 slots for orders, so you stop other orders coming in

Tip 3: you can hold down the ‘F’ key for fast mode. This is where time runs faster – useful if you have no orders yet, or no intention of fulfilling any more orders (near the end of the night)

--= CONTROLS =--

Press a number key to prepare/cook an ingredient:
1: bacon
2: beef
3: bread
4: cheese
5: chicken
6: onion
7: potatoes
8: sausage
9: tomato

Flick through the recipe book to learn which ingredients go into each menu item:
O: page left
P: page right

Fulfil orders by pressing 'a', 'b' or 'c'

Activate fast mode by holding down 'f' (makes time go faster)

--= FAST FOOD FRED MENU =--
- Cheese Burger £3 (Cheese, Beef, Bread)
- Chicken Nuggets £3 (Bread, Chicken)
- Chicken Parmo £3 (Bread, Cheese, Chicken)
- Chips £2 (Potatoes)
- Hamburger £2 (Beef, Bread)
- Hot dog £2 (Onion, Sausage, Bread)
- Margherita Pizza £4 (Cheese, Tomato, Bread)
- Onion rings £2 (Bread, Onion)
- Pollo Pizza £6 (Onion, Chicken, Cheese, Tomato, Bread)
- Royal Burger £5 (Bacon, Cheese, Beef, Beef, Bread)
- Ultimate Burger £8 (Onion, Tomato, Bacon, Cheese, Cheese, Beef, Beef, Bread)

--= APPENDIX A - LINE DESCRIPTIONS =--
Line 1 (255 characters): Set the screen to full brightness, a black border, back screen and red text. Clear the screen. Play the opening tune and display the 'Fast Food Fred' logo in red and yellow using BEEP, INK and PRINT commands. Create and store a blank link of 16 characters (b$). Set the text colour to show up best on the background, and set the colour to whatever was there before. Read in the day names (d$), recipe book text (r$), recipe book page number (r=3), and the cash total (c=0). Define the function for random numbers (r(x)). Define arrays for the ingredients (i), ingredient names (i$), menu items (m$) and menu item costs (c). For each of the 9 ingredients, read in their name and time to cook. For each menu item, read in the name, list of ingredients needed and the cost. Display the heading for the recipe book.

Line 2 (250 characters): Go to the subroutine for updating the recipe book page (line 10). Define a function for rounding the cash to the nearest pound (c(x)). Start the game loop for each of the 5 days (Tuesday to Saturday). Clear the daily amounts for the new day. Clear the 3 orders. Go to the subroutine for updating the order display on line 8. Set the time until the next order (t). Start the main game loop (h). Update the day, time and cash total on screen. For each of the 9 ingredients, print the names of them along with a flashing number if currently being prepared, and also invert some of the name as a progress bar. 

Line 3 (256 characters): Read the keyboard (k$). Checks if a key is pressed. If the key is between 1 and 9 (ingredient), then check that it isn't already in progress. Set the progress to 1. Add 50p to the daily spend. Beep (the pitch refers to the ingredient number). Flash the ingredient number. If 'o' or 'p' are pressed, update the recipe book number accordingly and go to the subroutine on line 10 to refresh the recipe book display. If 'a', 'b' or 'c' are pressed, and there's at least one ingredient in the order, then set the border to white and start the order checking process. Set the stock checking (i) and running costs (j) variables to 0. For each item in the order, and then for each individual item...

Line 4 (236 characters): ...set 'b' to the menu item being checked. For each ingredient in that menu item (y - up to 12 of them), if the ingredient isn't blank, set 'f' to the ingredient number, set 'g' to a flag to see if there's at least one ingredient in stock. Update the stock check (i) using flag 'g'. Update the stock of that item using 'g'. Repeat this process for each ingredient in that menu item. Add the cost of the completed menu item to the running costs (j). Repeat this for each individual menu item and each item in the order. Set the border to green and beep high if the order was successful, or a red border and low beep if it wasn't. Set the border to black again. If the order was successful, then update the daily income (d(2)) with the running cost of that order (j), add 1 to the total daily orders (d(4)), clear the completed order from the display, for each of the 3 order lines, clear the menu item and quantities.

Line 5 (251 characters): Now we focus on the preparing/cooking of ingredients. Set 'a' to the progress of the currently updating ingredient. Increase the stock of that ingredient if the progress reaches the time to cook. Update the progress of the item so it either increases by 1, or resets to zero if completed. Repeat for all 9 ingredients. If the time for a new order is reached: set the time for the next order, choose a random order slot (a), if that slot is empty, then set the border to yellow to signify a new order has come in. Decide if there are 1, 2 or 3 menu items in that order, choose each menu item, and a random quantity (1 to 3), and store the time of the order, and remove the chance of that menu item being chosen again within that order.

Line 6 (181 characters): Two beeps to signify the new order. Go to the subroutine on line 8 to update the order display. Set the border back to black. If the 'f' key is pressed for fast mode, add 25 to the time (h). Repeat the time loop (h). Beep to signify that the end of the day has been reached. For each of the 9 ingredients, check if any stock remains and add to the waste count (d(3)). Reset the progress and stock for each ingredient. Draw a blank red box over the ingredient list for the daily summary. Set the daily total (d(5)) to equal the income (d(2)) minus the spend (d(1)) and waste (d(3)). Add the daily total to the cash total (c). DATA for the day names (d$). 

Line 7 (243 characters): Display the number of orders, the costs, the waste, the income (sales), the day name and the daily total, and the current cash total. Wait for a key to be pressed. If the cash total is less than £0, exit the day loop otherwise repeat for the next day. Set the border to green and high beep if you've ended the full week in profit, or set the border to red and low beep if you've finished the week early with less than £0. Display the 'GAME OVER' message and wait for a key before starting the game again (RUN).

Line 8 (242 characters): Display all three orders. For each of the three orders (e), blank off the 4 lines of the display. If the first item of the order is not blank, then get the current time, split into hours (a) and minutes (b). Get the string of the time (t$). Display the order title bar including 'Order @' and the time. For each of the three item lines, display the quantity and the menu item name. Return from subroutine.

Line 9 (227 characters): DATA statement containing the recipe book title bar, initial page number and initial cash total. Then has all 9 ingredient names and times to cook. Then lists the menu item names, ingredient lists and costs. 

Line 10 (253 characters): Display the name of the current menu item and the cost. For the 8 possible ingredients, clear the line, read in the ingredient number into a$. If it's a valid ingredient, display the ingredient name. Return from subroutine. DATA statements continue with more menu items. 

NOTE: All line lengths above were calculated programmatically using 'Ten Liner Counter' from the 2025 BASIC 10 Liner contest.

--= APPENDIX B - VARIABLES =--
B$(16) - blank line
D$ - day names '
R$ - recipe book text
R - current recipe book page number
C - current cash total
I(9,3) - ingredients (1=time to cook, 2=progress, 3=stock)
I$(10,10) - ingredient names
M$(11,2,12) - menu items (1=name, 2=ingredients)
C(11) - costs for menu items
N, M, L, P - loop
D - current day (loop) (1=Tues, 2=Wed, 3=Thu, 4=Fri, 5=Sat)
D(5) - daily amounts (1=£spend, 2=£income, 3=£waste, 4=orders done, 5=£day total)
O(3,3,3) - orders 1-3, items 1-3, 1=menu item number, 2=quantity, 3=time of order
A - hour of time
B - minutes of time
T$ - time as a string
T - time until the next order
K$ - key pressed by user
Y - loop of each ingredient in an order item
I - checks stock of current ingredient when checking
J - running total cost of current order when checking
F - current ingredient number when checking order
G - flag to see if stock remains in current ingredient when checking
P, M, X, O, W, Z - IF statement

--= APPENDIX C - FUNCTIONS =--
r(x) - returns a random number between 1 and x
c(x) - rounds the cash amount to the nearest pound
