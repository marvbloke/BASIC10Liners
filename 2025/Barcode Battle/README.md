--= BARCODE BATTLE =--

System Requirements: Sinclair ZX Spectrum 48k/+/128k/+2/+3/Next 

Written by Matthew Begg for the 2025 BASIC 10-Liner Competition (EXTREME-256 category)
Licence: CC BY-SA 4.0

Players: 0, 1 or 2

--= INTRODUCTION =--

The BARCODIANS have arrived!  These enigmatic beings, disguised as barcodes on everyday products, possess incredible abilities. Now, it's your turn to harness their power. Enter the code, unleash the warrior, and prepare for battle!

--= LOADING INSTRUCTIONS =--

- Spectrum 48k/+ - type LOAD "" then ENTER. That's 'J' then Symbol Shift+P twice, then ENTER.
- Spectrum 128k/+2/+3/Next - choose "Tape Loader" or "Loader" then ENTER.
- Emulator (e.g. Fuse): load the "Barcode Battle.tap" file into your emulator then use the instructions above.

The game will load and automatically start.

--= FEATURES =--

'Barcode Battle' is inspired by the 'Barcode Battler' - a fascinating and somewhat quirky handheld game console released by Epoch in 1991. It leveraged the popularity of barcodes at the time, turning everyday products into playable characters in a simple yet addictive battling game.

- Custom 'PCH' font to give futuristic feel - the default Spectrum font is never seen!
- 1 or 2 players, or even let the computer play itself!
- Deterministic algorithm means that one barcode always produces the same warrior name, colour and stats
- Computer controlled players use AI (!) to play the game
- Winner stays on
- Futuristic bleep-bloop sound effects throughout
- Colourful graphics
- Strategic gameplay using the barcodes on everyday supermarket items

--= CONTROLS =--

On warrior selection screen:
- 0-9 and ENTER - typing in barcode number
- 'C' - create a computer-controlled warrior

In the game itself:
- 'A' - increase your ATTACK score 
- 'D' - increase your DEFEND score 
- 'E' - try and increase your ENERGY level 
- 'B' - battle your opponent 

--= WARRIOR SELECTION =--

Once loaded, you are asked to enter two barcode numbers. For a human player, enter an 8 to 13 digit barcode number as found on many household items. For a computer-controlled (CPU) player, press 'C' to create a warrior. Both barcodes can be human (2 players), both can be CPU (0 players), or one of each (1 player).

The barcodes are then converted into Barcodian Warriors with their own name, colour and set of stats. The stats are displayed as numbers and bars:

- A: ATTACK score (red)
- D: DEFEND score (magenta)
- E: ENERGY level (green)

--= ON YOUR TURN =--

The aim of the game is to destroy your opponent by reducing their energy level to 0. You do this by engaging in battles. You and your opponent take it in turns to carry out 3 actions. Choose from these possible actions:

- press 'A' to increase your ATTACK score by 1. This uses 2 of your energy.
- press 'D' to increase your DEFEND score by 1. This uses 1 of your energy.
- press 'E' to try and increase your ENERGY level by 0, 1 or 2 (random).
- press 'B' to battle your opponent. 

--= BATTLING =--

Battling is only possible if your ATTACK score is the same or higher than your opponent's DEFEND score. The amount of damage you do to their ENERGY level depends on this difference between your ATTACK and their DEFEND scores:

- The same: you have a 50/50 chance of reducing their ENERGY by 1
- Your ATTACK is bigger than their DEFEND: you will reduce their ENERGY by between 1 and the total difference (random)
- Your ATTACK is lower than their DEFEND: battling is not possible

Once a warrior's ENERGY level is 0 or less, they are dead. The winning warrior stays on for the next game (reverting to their original stats). You then either enter the same barcode (rematch!), another barcode, or press 'C' for a computer-controlled player.

--= APPENDIX A - PROGRAMMER'S NOTES =--

The challenge I set myself for this game was to use a custom font throughout, with the Sinclair font never shown. This is difficult due to the amount of characters and lines it would use up to store an entire character set. Then I had the brainwave that I didn't need an entire character set - I only needed the digits 0 to 9 and the letters contained in the title of the game (BARCODE BATTLE). It meant I had to clever with what other words I could display that only used those letters (hence the stats are A, D and E, and the word "DEAD"). That's when I realised I could write the data into the user-defined graphics area, making it much easier to code. It still used up about 3 lines' worth of code just for the font, so I just had to be clever about fitting the game into the other 7 lines or so. 

For the algorithm that turns a barcode into a specific 4 letter name, colour and set of 3 stats, this used a few tricks: 
- The names are only 4 letters long and consist of a consonant, vowel, consonant and vowel. That means they're always readable
- The 3 stats are worked out by squaring the digits, adding them together, then getting the square root. It's the old polynomials trick (as used in many forms of error correction). 

--= APPENDIX B - LINE DESCRIPTIONS =--

Line 1 (255 characters): Sets and clears the screen to use bright blue, black border and white text. Reads in the 19 user-defined graphics from the later DATA statements - these are used to store the font for the letters and digits ABCDE012345L67O89RT (in that order). Initialises the arrays b$, e$, n$, h$ and s then reads in initial values for x$, d$, t$, c$ and v$ (see 'Variables' below). Start the overall game loop ('y'). Draw blank lines in the two warrior boxes. DATA statement contains the custom font user-defined graphics (part 1)

Line 2 (249 characters): Set 'F' used to contain the 'infinite' loop number 1e9 (used throughout the listing for endless loops). Clear the bottom status line. For each warrior box, plot and draw the outline around it. Define the function 'r' (see 'Functions' below). Draw the title ' BARCODE BATTLE ' on the screen. For each player ('o' checks that there isn't a winner staying on), start an infinite loop for the user to enter a barcode. Uses the input subroutine on line 8. Checks that the barcode is at least 8 digits long or is blank (for CPU warriors). Adds '12345' onto the end in case the barcode is shorter than 13 characters (but is concatenated by e$ only storing 13 chars). If the entered code is blank (for a CPU warrior), generate... 

Line 3 (251 characters): ...and display the random digits for the CPU warrior with a beep based on the digit. Wait 1 second. Erase the two barcodes from the screen from right to left (with sound effects). Set the turn flag (t) to 0. For each player, let's generate the 3 statistics (attack, defend and energy). A temporary variable (a) is set to 0. Then for a subset of 10 digits from the barcode, take each digit (b), square it, then add it to the running total (a). Then set 'a' to be the square root of the running total divided by the number of the statistic plus 1 (2, 3 or 4) added to the number of the statistic multiplied by 5. This algorithm gives deterministic values every time that barcode is used. The integer of that final value is stored as the statistic for that player (s(n,m)). The paper colour of each player is determined by adding 1 to the value of the 3rd digit, then using that as an index to choose which digit in the first 10 digits is divided by 2. 

Line 4 (256 characters): The name (n$) for each player is taken from a consonant, vowel, consonant, vowel (chosen by the paper colour and an offset). An infinite loop (q) is started. A loop for the three 'goes' (or 'actions') - (g) is started. Displays the actions counter (e.g. 1/3 or 2/3 or 3/3) in the appropriate warrior's box. For each player, displays the name (flashing if it's their turn, 'C' shown if it's a CPU warrior). For each of the three statistics, sets up a temporary string (a$) containing the stat (if negative, sets it to 0). Temporary variable (z) works out the length of the bar to be shown.

Line 5 (256 characters): Defines the digit display function (FN d$(x)) (only put it here because it won't fit anywhere else!). Display the UDG letter 'A', 'D' or 'E' in the correct colour, along with the number of the statistic then a bar of the correct length (with a maximum of 12 in length). Clears the status bar at the bottom. Sets 'u' to equal the turn flag plus 1. Pause 1 debounces the keys (if a key is already pressed), then either pause 0 (wait for a key) if the player is human, or pause 1 (move on) if the player is CPU. Reduce the goes/action (g) counter by 1 in case the turn isn't a valid one. Read in the key as k$. If the player is CPU, then set the key (k$) as one of the 4 possible actions ("adeb"). Goes to the subroutine on line 9 to see if a battle should take place. If 'a' has been pressed (and the player's energy is 3 or higher), then reduce energy by 2, add 1 to their attack score...

Line 6 (247 characters): ...display a red status bar saying "A1 E-2" using status bar subroutine on line 10, and increase 'g' as it is a valid go. If 'd' has been pressed (and the player's energy is 2 or higher), then increase 'g' as it is a valid go, reduce energy by 1, add 1 to their defend score, display a magenta status bar saying "D1 E-1" using status bar subroutine on line 10. If 'e' has been pressed, then increase 'g' as it is a valid go, set temporary variable (a) to between 0 and 2, add that to their energy, and display a green status bar saying "E+" and whatever was added. Use temporary variable (a) to determine if either player is dead. If so, increase 'g' beyond the limit of 'goes'. End of the 'goes' loop. Clear the 'goes' indicator from that warrior's box. Toggle the turn flag (t) ready for the other player's turn.

Line 7 (242 characters): Use the previous 'a' value to see if either player is dead, if so exit the loop. Otherwise loop back for the other player's turn. Prepare a white status bar saying the name of the dead player and the word "DEAD". Clear their barcode so it'll prompt for a fresh one in the next game. Black out the warrior's box. Make a low sound. Display the prepared 'DEAD' status bar. Wait 10 seconds (or for a key press) then return to the beginning of the 'y' loop for the next game. DATA statement contains the custom font user-defined graphics (part 2)

Line 8 (256 characters): BARCODE ENTRY subroutine - Set string to blank (s$). Display a flashing cursor. Start an infinite loop (z). Wait for key press. Set i$ to the key pressed. Checks that the key pressed is between 0 and 9 and the maximum length of the barcode hasn't been reached. Adds the key pressed to the string so far and beeps with a pitch according to the number pressed. Displays the typed character and a fresh flashing cursor. If DELETE was pressed and the length of the string is bigger than 0, then removes the last character from the string and rubs it out on screen. If 'C' or 'ENTER' is pressed, leaves the z loop. The flashing cursor is removed and the random number generator is reset. Returns to where the subroutine was called from. DATA statement contains the custom font user-defined graphics (part 3)

Line 9 (252 characters): BATTLE subroutine - If 'b' is pressed, the difference between the player's attack score and the opponent's defend score is calculated (d). If this is 0 or higher, the battle can continue (otherwise the key press is ignored). The amount of damage (a) is calculated. This is based on whether the difference is 0 (in which case the amount is randomly 0 or 1), or if the difference is bigger than 0 (in which case it is between 1 and the difference). Increase 'g' as it is a valid go. Display a yellow status bar saying "NAME BATTLE NAME E-.." with the names of the warriors and the amount of damage done. Reduce the opponent's energy by the amount of damage. Returns to where the subroutine was called from. DATA statement contains the custom font user-defined graphics (part 4) 

Line 10 (253 characters): STATUS BAR subroutine - get's the paper colour from the first character of the message string (m$) and stores in p. Sets 'v' to be the length of the message. Sets m$ to contain 32 spaces (from b$) plus the message and another space. Starts a loop (z) from 1 to 17 plus half the length of the message (this is to make sure the message only scrolls as far as the centre of the status bar). Update the status bar on screen with the correct paper colour (p) and make a sound as it scrolls (beep pitch based on paper colour). Updates the message (m$) to remove the first character and add to the end (scrolling effect). End of loop z. Returns to where the subroutine was called from. DATA statement contains the custom font user-defined graphics (part 5) and the initial values of strings x$, d$, t$, c$ and v$ (see 'Variables' below)

NOTE: All line lengths above were calculated programmatically using 'Ten Liner Counter'.

--= APPENDIX C - VARIABLES =--

ARRAYS
b$(32) - blank line up to 32 characters
e$(2,13) - two barcodes (up to 13 characters long)
h$(5,24) - high score table (future proofing - not currently used)
n$(2,5) - two warrior names (4 characters long but 5th character used to insert space)
s(2,5) - statistics for the 2 players: 1:attack, 2:defend, 3:energy, 4:paper colour, 5:CPU player flag

STRINGS
a$ - temporary string
c$ - consonants for name generation in custom font ("TRLDCBLRTB")
d$ - the digits 0-9 in custom font ("0123456789")
i$ - the key pressed during barcode entry
k$ - the key pressed during the game (or CPU's action)
m$ - message to be shown on the status bar
t$ - title of the game in custom font (" BARCODE BATTLE ")
v$ - vowels for name generation in custom font ("AEOAEOAEOE")
x$ - possible moves for CPU player ("adeb")

NUMBERS
a - temporary variable used when reading UDGs and throughout the code
b, z - temporary variables
d - difference between the player's attack score and the opponent's defend score 
f - 1e9 (the 'infinite' loop number)
n, o, p, q - FOP loops
p - paper colour used in status bar subroutine 
t - turn flag (0=player 1, 1=player 2)
u - turn flag +1 
v - length of the status bar message 
y - overall game loop

--= APPENDIX D - FUNCTIONS =--

d$(x) - returns the UDG characters for the 1 or 2 digit number x
r(x) - returns a random number between 1 and x


 