--= ZX STOCK EXCHANGE =--

System Requirements: Sinclair ZX Spectrum 16k/48k/+/128k/+2/+3/Next 

Written by Matthew Begg for the 2025 BASIC 10-Liner Competition (PUR-80 category)
Licence: CC BY-SA 4.0

Players: 1

--= INTRODUCTION =--

It is July 1982. Welcome to the frenetic trading floor of the ZX Stock Exchange. The air crackles with the buzz of hurried transactions and the staccato rhythm of the ticker tape. In this game you'll test your financial acumen in the heart of the City, where fortunes are won and lost in the blink of an eye. Can you navigate the volatile markets, buy low, sell high, and amass a fortune? Or will the unpredictable tides of the market leave you penniless? Only your wits and a touch of luck will determine your fate in this 8-bit financial adventure.

'ZX Stock Exchange' is my first attempt at a PUR-80 game (10 lines of BASIC - 80 characters or less per line). I wanted to have the feel of the 1980s stock trading floor but keep it fun with simple controls, a green-screen terminal in the middle, and a side-scrolling stock ticker at the bottom. 

--= LOADING INSTRUCTIONS =--

- Spectrum 16k/48k/+ - type LOAD "" then ENTER. That's 'J' then Symbol Shift+P twice, then ENTER.
- Spectrum 128k/+2/+3/Next - choose "Tape Loader" or "Loader" then ENTER.
- Emulator (e.g. Fuse): load the "ZX Stock Exchange.tap" file into your emulator then use the instructions above.

The game will load and automatically start.

--= CONTROLS =--

- 1-9 - select a stock
- 'B' - buy 1 of that stock
- 'S' - sell 1 of that stock

--= HOW TO PLAY =--

The game starts on 1st July 1982, and gives you a full month to accrue as much money as possible (or lose it all!) Time runs from 8am to 4pm in 2 minute increments. The screen is laid out as follows:

- The blue bar shows your current balance at the top right. You start with £200.
- The green-on-black computer terminal in the middle shows the nine stocks you can trade in, with their name, current price and how much you own. Their price is updated every 'hour'.
- The red bar shows the current date and time.
- The yellow-on-black strip at the bottom is the stock ticker showing how much each stock has decreased or increased in the last hour.

Your currently selected stock is shown with a flashing green bar. Use the 1 to 9 keys to select a stock. Then press 'B' to buy 1 of that stock at the current price (assuming you have enough money). Press 'S' to sell 1 of that stock at the current price (assuming you have some to sell). Hold the 'B' or 'S' key down to trade in bigger quantities. You can trade up to 30 stocks each hour. You are aiming to buy low, sell high. Keep an eye on your current balance though.

The game continues until 4pm on 31st July 1982 at which point your final balance is displayed at the top right. Press any key to start the game again. If you want a shorter game, decide on an earlier date to finish at, for example 7th July 1982 would give you a week to prove yourself.

--= APPENDIX A - LINE DESCRIPTIONS =--

Line 1 (79 characters): Set the screen to white border, white background and blue ink. Set the inverse flag so things are drawn with solid bars behind them. Read in initial variables x$,c,s,i and z$ (see 'Variables' below for more details). Clear the screen. Print the blue bar at the top featuring the game title "ZXSE", then the current cash balance ('c') rounded to the nearest pound. Initialise arrays for the stock names, stock prices/quantities and the stock ticker (s$, s and b$). 

Line 2 (78 characters): Read in y$. Define the random function r(x). For each of the 9 stocks, generate a random 3 letter name. Set their initial prices at between 50.0p and 600.0p. 

Line 3 (78 characters): Start the date loop (from the 1st to the 31st). Start the hour loop (from 8 to 15). Update the terminal (subroutine on line 10). Draw the red bar at the bottom to show the current date and hour.

Line 4 (74 characters): Start the minute loop (from 0 to 59 minutes in 2 minute increments). Update the minutes displayed on the red bar and update the two-line ticker at the bottom. Read for any key pressed (k$). Start updating the ticker.

Line 5 (80 characters): For each line of the ticker, remove the first character and add it to the end. Set 't' to equal 1000 (written as 1e3 to save 1 character!). Use 'z' to check if a key is pressed. Allows the computer to skip a large chunk of code if no key is pressed, keeping the game running fast. If a number key is pressed, change 's' to that number. DATA statement 1 of 4 (contains x$)

Line 6 (78 characters): Print the 'Buy Sell' instruction on the top blue bar. If the 'b' key is pressed AND you have enough money, then reduce your cash (c) by the price of the current stock (divided by 1000) and increase the quantity held of that stock (s(s,2)) by 1. DATA statement 2 of 4 contains c, s and i.

Line 7 (80 characters): If the 's' key is pressed AND you own at least one of that stock, then reduce the quantity of that stock by 1 and increase your cash balance by the current stock price divided by 1000. Update the cash balance on screen. Update the terminal (subroutine on line 10). End the key pressed loop (z) and the minute loop (m). 

Line 8 (79 characters): At the end of every hour, reinitialise the banner array. For each stock,  generate a random amount to decrease/increase it by (a). Update its price. Add its name to the 1st line of the ticker. DATA statement 3 of 4 contains z$.

Line 9 (74 characters): Add the change (a) to the 2nd line of the ticker, along with a 'p' to indicate pence. End the stock loop (n). End the hour loop (h). End the day loop (d). Wait for a key to be pressed. Restart the game (RUN). DATA statement 4 of 4 contains y$.

Line 10 (79 characters): Terminal update subroutine. For each stock, print the number, name, price in pence and the quantity owned by the player. Make sure the currently selected stock (s) is made to flash. Return from subroutine.

NOTE: All line lengths above were calculated programmatically using 'Ten Liner Counter'.

--= APPENDIX B - VARIABLES =--

ARRAYS
s$(9,3) - 3 letter names of the 9 stocks
s(9,2) - the current price (1) and current quantity (2) held of each stock
b$(2,32) - the 2 line banner at the bottom (used for the animated ticker)

STRINGS
k$ - current key pressed
x$ - "Buy Sell" instruction
y$ - the graphics control characters to get flashing green writing on a black background for the computer terminal in the middle
z$ - a single space

NUMBERS
c - cash balance (starts at 200)
d - date (runs from 1 to 31)
h - hour (runs from 8 to 15)
i - not used?
n,o - loops and conditional statements 
s - selected stock (between 1 and 9 - starts at 1)
t - a thousand 

--= APPENDIX C - FUNCTIONS =--

r(x) - returns a random number between 0 and x-1


 