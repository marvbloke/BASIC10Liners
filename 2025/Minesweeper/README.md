--= Minesweeper =--

System Requirements: Sinclair ZX Spectrum 48k/+/128k/+2/+3/Next 

Written by Matthew Begg for the 2025 BASIC 10-Liner Competition (EXTREME-256 category)
Licence: CC BY-SA 4.0

Players: 1

--= INTRODUCTION =--

This is a faithful recreation of Minesweeper for the ZX Spectrum, with the look and feel of the Windows 3.1 original. This classic game of logic and deduction challenges you to navigate a minefield by uncovering hidden squares. Press ‘U’ to uncover a square. If it's a mine, you lose! If it's a number, it indicates how many mines are adjacent to that square. Press ‘M’ to mark a suspected mine. Uncover all the safe squares to win!

--= LOADING INSTRUCTIONS =--

- Spectrum 48k/+ - type LOAD "" then ENTER. That's 'J' then Symbol Shift+P twice, then ENTER.
- Spectrum 128k/+2/+3/Next - choose "Tape Loader" or "Loader" then ENTER.
- Emulator (e.g. Fuse): load the "Minesweeper.tap" file into your emulator then use the instructions above.

The game will load and automatically start.

--= CONTROLS =--

- Use the arrow keys to move around the grid
- Press 'U' to uncover a square
- Press 'M' to mark a mine with a flag
- Press 'G' to start a new game
- Press 'H' to show the help screen - press any key to return to the game

--= GAMEPLAY =--

Once loaded, you are asked to enter the number of mines you'd like in the grid. There are some suggestions (10 for beginners, 35 for intermediate players and 50 for experts) but you can enter any number between 1 and 169. The game will then generate your grid. The progress of this is shown as a percentage. Once done, the classic Minesweeper window will appear. The two red numbers near the top show how many flags are still remaining and how many seconds you've taken so far (updated when any key is pressed). The smiley face in the top middle shows the current state of the game. One of the squares will be flashing - this is your current position. Use the arrow keys (for the rubber-keyed Spectrum 48k, that's CAPS SHIFT+5,6,7 and 8) to move around the grid. Clues as to the location of the mines are given as coloured numbers on the grid. The number relates to the amount of mines that are in the surrounding 8 squares of that number. 'U' uncovers a square and 'M' marks the square with a flag. Once you've uncovered all non-mine squares, the game will end and you'll be given your final timed score (the lower the better). Why not play another game and try and beat your time?

--= HISTORY OF MINESWEEPER =--

Microsoft’s Minesweeper was created by Curt Johnson and ported to Windows by Robert Donner. It was inspired by earlier games, but became a phenomenon thanks to its inclusion in Windows 3.1 in 1992. Its polished graphical interface made it accessible to a broader audience, and its presence in such a widely used operating system cemented its place in gaming history. The game's simple rules belied a surprising depth of logic and strategy, making it both easy to learn and challenging to master. Over the years, Minesweeper has been updated visually alongside Windows, but the fundamental gameplay has remained largely unchanged, contributing to its enduring appeal as a classic puzzle game.

--= APPENDIX A - LINE DESCRIPTIONS =--

Line 1 (247 characters): Reset the random number seed. Set the screen to have a black border, cyan background and black text, then clear the screen. Display some suggested number of mines and ask the user for the number of mines to include in the grid (stored in b). Defines functions (see 'FUNCTIONS' below)Initialises arrays m, f, g, i and b$ (see 'VARIABLES' below for more details). Read from the later DATA statements into t$, b$(1) and b$(3). Sets initial y and x cursor position to a random square. Reads in the data for the 8 user defined graphics. 

Line 2 (251 characters): For each mine (up to the total number of mines - b), store a random 'y' and 'x' position in variables c and d respectively. Test to see if that particular position on the grid is already filled. If so, decrease the FOR loop by 1 so it gets chosen again. Store a '1' in the grid g(c,d). Update the percentage on screen to show how far through the dissemination of mines we are (up to maximum of 50%). Initialise arrays m, r and s. Set the number of flags remaining (f) to the number of mines (b). Read in the 9 ink and sound values from the later DATA statements (into I() and S() respectively). Define the function C which counts mines around this square.

Line 3 (249 characters): Two FOR loops let us cycle through every square on the grid, setting F(C,D) to equal the number of mines around that square (using function C) then updating the percentage on screen accordingly (from 50 to 100%). Clears the screen. Draws the outline of the window, then draws the window icons at the top left and top right. Displays the title bar text, menu bar text, overlays the underscores for the menu shortcuts and the backgrounds for the score displays. Draw the window background (using B$). Use 3 POKEs to reset the timer. 

Line 4 (228 characters): Set P to the x position for writing the number of flags remaining. Set T to the current time (using function T). If it's over 999, just set it to 999. Set O to the x position for writing the time used. Write '000' into both boxes, then write F and T over the top in the right-justified position. Draw the appropriate smiley face (based on if all the mines have been found). Test if all mines have been found - if so, play the tune, clear the remaining squares on the grid and wait for a key press before starting the game again (with RUN).

Line 5 (134 characters): Set A to the attribute value of the current square. POKE the attribute to make it flash (adding 128 to it). Wait for a key press then store the ASCII code of that key in K. POKE the attribute to stop the current square from flashing. Set X and Y according to whether the left/right/up/down keys have been pressed and we're still inside the grid. If 'G' has been pressed, start a new game (with RUN). If 'U' is pressed, do some further checks: if there's a mine there...

Line 6 (232 characters): highlight the mine in red, change the smiley face, play a sad tune, show the remaining mines on the grid and wait for a key press before starting the game again (with RUN). Look at the squares surrounding the current one individually and print the number stored in array F to show how many mines surround it. If the number is 0, just use a space. Record that you've revealed that square in R(C,D). 

Line 7 (152 characters): If the 'M' key is pressed and the current square hasn't been revealed yet, play a short beep, check that there isn't a flag there already and that you've got at least 1 flag left to use. Display a red flag and jump back to line 4 to update the screen. If the current square already has a flag, remove it (updating the screen and M(Y,X)). 

Line 8 (245 characters): If the 'H' key is pressed, display the help text. Pressing a key then draws the help text again but in cyan so it effectively deletes it.

Line 9 (137 characters): Two secret cheats: If the 'T' key is pressed, it shows the location of all mines. If the 'R' key is pressed, it shows all the number clues. Although you can continue playing, it's totally cheating! End of main game loop, so jumps back to line 4. DATA statement containing the window title " Minesweeper " and a line of blocks.

Line 10 (245 characters): DATA statement containing the menu bar text (" Game Help     ") and the values for the 8 user defined graphics characters.

NOTE: All line lengths above were calculated programmatically using 'Ten Liner Counter'.

--= APPENDIX B - VARIABLES =--

- Array B$(3,15) - blank line and other text
- Array F(18,18) - the grid of numbers y,x
- Array G(18,18) - the grid of mines y,x
- Array I(8) - ink colours of numbers
- Array M(18,18) - the grid of marks y,x
- Array R(18,18) - the grid of revealed squares y,x
- Array S(9) - sound values

- String T$ - title

- A - attribute value at y,x
- B - number of mines remaining
- F - number of flags remaining
- K - ASCII code of key pressed
- H - height
- W - width
- X - x position of cursor
- Y - x position of cursor
- C, D, M, N, O, P - temporary variables

--= APPENDIX C - FUNCTIONS =--

- C(Y,X) - count mines around this square
- P() - return the memory address of the attributes at screen position Y,X
- R() - returns a random number between 0 and 12
- T() - returns the time in seconds 
 