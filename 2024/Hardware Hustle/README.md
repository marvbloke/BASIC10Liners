HARDWARE HUSTLE
======== ======

Written for the ZX Spectrum by Matthew Begg (licence: CC BY-SA 4.0)
From the original roll-and-write game by Oskitone (licence: CC BY-SA 4.0)

Compatible with Sinclair ZX Spectrum 48k/+/128k/+2/+3/Next

Players: 1 or more
Controls: number keys and ENTER
How to start the game: LOAD "" or LOAD "HH". The game will auto-start.

INTRODUCTION

Buy, make, sell, and research your way to profit without burning out!

Hardware Hustle is a really fun turn-based resource management game that simulates the running of a small hardware business over 6 days. You'll be buying parts, making and selling widgets, researching and improving each part of the business, trying to make as much money as possible. The game board for each day resembles a spreadsheet from the 1980s (including the green-on-black text aesthetic).

The original paper-based game and full rules can be found here:
https://github.com/oskitone/hardware_hustle

PLAYING THE GAME

"PLAYERS?" - enter the number of players from 1 to about 8-ish

You start day 1 with 10 money.

Each player takes it in turn to carry out their actions on each day. This is made up of 3 phases: BUY parts, MAKE widgets and SELL widgets. Each of those phases use 'opportunity' which depletes as the game progresses and is limited per-phase by a random number generator (between 1 and 6). The six days are miniature spreadsheets, and the game ends when you reach the end of day six. The player at the end with the most money wins.

PHASES OF PLAY

- BUY: enter how many enclosures, speakers, controls and processors you'd like to buy
- MAKE: enter how many amplifiers, noiseboxes and synths you'd like to make
- SELL: enter how many amplifiers, noiseboxes and synths you'd like to sell

Enter numbers then press ENTER to indicate how many of each part you want to buy, how many of each widget you want to make and how many of each widget you wish to sell. You won't be able to carry out an action if it would exceed the amount of opportunity you have for that phase or if you would run out of money - you'll be asked to enter again. Enter '0' if you don't want to buy/make/sell that item. The 'PM' column shows the total number of parts and widgets you have at the end of the day, along with how much money you have. If you have less than zero opportunity left, you'll burn out and miss the next day. If you have over 6 opportunity left (or if the random number generated is lower than the remaining opportunity) you'll get the opportunity to do research on one of the phases. This will reduce the costs associated with that phase. Press a key to move onto the next player/day.

LINES OF CODE
Line 1  (230 characters): initialise the green-and-black screen, read in the data statements (user defined graphics, text strings, phases and research levels, starting opportunity values and prices of things to sell)
Line 2  (256 characters): draw the screen (phases of play on the left)
Line 3  (249 characters): draw the screen (spreadsheet for the day)
Line 4  (233 characters): run the BUY phase
Line 5  (252 characters): run the MAKE phase (also includes some of the DATA for UDGs)
Line 6  (255 characters): run the SELL phase
Line 7  (255 characters): continue the SELL phase and total up the day
Line 8  (253 characters): see if research or burnout happens, and the end of the game total scores 
Line 9  (218 characters): restart the game and DATA for the UDGs and phases/research
Line 10 (252 characters): subroutine for updating the spreadsheet and DATA for phases/research, text strings and opportunity values and prices

VARIABLES
Numbers
d - current day (FOR loop)
mp - maximum number of players
p - current player (FOR loop)
z - temporary variable holding the current cell value
t - running total of money within a phase
o - running total of opportunity within a phase
c - running check for validity within a phase
r - roll of the dice
n, m, q - temporary loops
y - temporary running total of parts available during the MAKE phase
x - temporary loop used for burnout skip

Arrays
n$(mp, 8) - player names
o(6) - opportunity start values per day (taken from DATA)
p(3,4,4) - phase research data (phase, upgrade, item)
g(mp+2,6,9,5) - the spreadsheet grid (player, day, row, phase)
l(mp,3) - what level of BUY/MAKE/SELL is each player
m(mp) - total money for each player
s(6+mp) - how much things cost when selling, plus flags for skipping

Strings
t$ - game title
u$ - column headings
v$ - 4 spaces
w$ - "PLAYERS?"
x$ - research line
