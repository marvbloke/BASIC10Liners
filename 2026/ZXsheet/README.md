--= ZXsheet =--
System Requirements: Sinclair ZX Spectrum 48k/+/128k/+2/+3/Next/'The Spectrum'
Written by Matthew Begg for the 2026 BASIC 10-Liner Competition (SCHAU category)
Licence: CC BY-SA 4.0

--= INTRODUCTION =--
ZXsheet is a full-featured spreadsheet application for the Sinclair ZX Spectrum written in just 10 lines of BASIC. It features a large 20 rows by 10 column workspace, full colour formatting, formula support, copy/paste functions (including relative addressing), the ability to save and print spreadsheets, and a groundbreaking graphical chart function.  

--= LOADING INSTRUCTIONS =--
- Spectrum 48k/+ - type LOAD "" then ENTER. That's 'J' then Symbol Shift+P twice, then ENTER.
- Spectrum 128k/+2/+3/Next - choose "Tape Loader" or "Loader" then ENTER.
- Emulator (e.g. Fuse): load the "ZXsheet.tap" file into your emulator then use the instructions above.
A blank spreadsheet will load and automatically start. Outside of the contest, if you want to see worked examples, try LOAD "Finance", LOAD "Sales" or LOAD "World".

--= HOW TO USE =--
Once loaded, the screen border flashes for 8 seconds while a blank spreadsheet is initialised. You then get to see the help screen with all the keyboard commands available. Press any key to view your blank spreadsheet. You can see all 20 rows (1 to 20) and the first 4 columns (A to D). Use the cursor keys on your Spectrum* to navigate around the spreadsheet. The selected cell is highlighted in yellow, with its contents shown at the bottom of the screen. Moving to the right will scroll the sheet sideways up to column J. 
*Note: All Spectrum models have dedicated cursor keys apart from the rubber-keyed original model (or 'The Spectrum'). These models use CAPS SHIFT+5,6,7,8 to move around. An emulator will use the arrow keys on your computer.
To enter something in a cell, press 'ENTER' for edit mode. You can enter numbers, text or formulas, then press ENTER to finish. Formulas must start with '='. You can change the colour of a cell using the 0 to 7 keys. Because 7 is white (and the background is white), this is useful for hiding formulas in more complex sheets. If you make a mistake, use the 'DELETE' key (or CAPS SHIFT+0) to clear a cell. You can copy the contents of a cell with 'C' (assuming it is text or a formula), and paste with 'V'. Text is copied as is, but formulas are copied using relative addressing. This is great for using the same formula across multiple columns without having to re-enter them each time. Press 'S' to save your spreadsheet to tape (or disk on +3). You can load a previously-saved spreadsheet using the normal LOAD command in Sinclair BASIC. Press 'P' to print the currently visible data to your ZX Printer (or emulated printer). You can get a bar chart of your data using the GRAPHICS/GRAPH key (or CAPS SHIFT 9) - see the section on 'CHARTS' below. Press 'SPACE' to toggle Calc mode (where all formulas are recalculated on data entry, not just the current formula). Press 'N' to start a new blank spreadsheet. To see a reminder of all these commands, press 'H' at any time.

--= TUTORIAL/EXAMPLE =--
Let's try creating a way to track sales of various fruits over time. Starting with a blank sheet and the cursor in cell A1, press 'ENTER' followed by 'FRUIT' then ENTER. The cursor automatically moves to the cell below. Continue using 'ENTER'<text>'ENTER' to create the first column:
FRUIT
Apple
Banana
Cherry
Let's make these row headings colourful by moving back to them in turn and pressing a colour key (for example, turn 'Apple' green with 4, 'Banana' yellow with 6 and 'Cherry' red with 2.)
Move to cell B1 using the arrow keys, then enter the column headings as Jan, Feb (in cell C1), Mar (in cell D1) going across. Enter random numbers between 20 and 80 in the nine data entry cells (B2,B3,B4,C2,C3,C4,D2,D3,D4). 
Now let's see a chart of sales in January. To do this, navigate to the cell with the HIGHEST number in the Jan column (to correctly set the scale of the bar chart). Then press the 'GRAPHICS' or 'GRAPH' key (if using the original Spectrum, The Spectrum or an emulator, press CAPS SHIFT+9). You will then see a horizontal bar chart of the data, with coloured bars representing the sales of apples, bananas and cherries in that month. You can go to the highest number in the Feb or Mar columns and press 'GRAPHICS' to see charts for those months too.
Let's add some totals. Move to cell A5 and enter 'TOTAL', then in B5 enter the formula '=b2+b3+b4'. You'll notice this automatically calculates the total fruit sold in January. Go back to B5 and press 'c' to copy the formula. Go to C5 and press 'v' to paste the formula. You'll notice this uses relative addressing to actually insert the formula '=C2+C3+C4' to give the total for February. Go to cell D5 and press 'v' for the March total. 
Go to cell A6 and enter 'GRAND T' then go to B6 and enter 'OTAL' (so you get the words 'GRAND TOTAL' spanning cells A6 and B6). Go to cell C6 and enter the formula '=b5+c5+d5' which then totals up all the fruit sold across all three months. You can go over these totals and use the number keys 0-7 to make them a different colour if you wish.
So far, all of these calculations have happened automatically. This happens when formulas are first entered. But if you change any of the numbers in the data entry cells, you'll notice the totals don't update. To solve this, you need to use 'Calc' mode by pressing SPACE. This is indicated with a '(c)' symbol in the bottom right. Now when you change any of the numbers, all the totals will update automatically. The downside is that the spreadsheet is much slower to use when you enter data (the yellow bar disappears when ZXsheet is 'thinking'). You can switch back to manual mode by pressing SPACE again. Remember to press 'h' if you want a reminder of which keys do what.
This simple example sticks to only three types of fruit and only three months of sales data, but there's nothing stopping you adding more months (scrolling to the right) or more fruits.

--= FORMULAS =--
Formulas must begin with the equals sign. A really simple formula would be '=3+4'. This would always display 7 on the sheet, but you would see the '=3+4' formula at the bottom of the screen when the cell was selected. All cells are referenced in the traditional letter-for-column then number-for-row format (e.g. the fourth row down in the second column is cell B4). So if cell A3 contained the number '84', and cell A4 contained the formula '=A3+5', cell A4 would display as 89. If you were in Calc mode (by pressing 'SPACE'), you could change the number in cell A3 and see the displayed number in A4 change as a result. As well as numbers, cell references and simple operators (like +,-,*,/ and brackets) you can also enter the following symbols/functions as part of your formulas:
- Conditional operators like '=', '>', '<='
- Mathematical functions like 'to the power of' (Sym Shift+H), trigonometric functions like SIN/ASN, COS/ACS, TAN/ATN, rounding to nearest integer with INT, random numbers with RND, exponentials with EXP, logarithms with LN, and PI. These must be entered using the relevant 'Symbol Shift' or 'Extend Mode' keys rather than typing them in (for example, you get INT by pressing CAPS SHIFT and SYMBOL SHIFT together to enter Extend Mode (with the flashing 'E' cursor) then press R). See the ZX Spectrum manual or your emulator's help page for the full keyboard layout.

--= TROUBLESHOOTING =--
When entering formulas, it is possible to make a mistake which Sinclair BASIC gets confused by. This can result in a 'Nonsense in BASIC' error. If this happens - don't panic! You haven't lost your work. You just have to enter the following short line of commands to return to your spreadsheet:
LET w$=“”:LET s=1:GOTO 2   (then ENTER)
(If you are entering this on a 48k Spectrum, the 'LET' command is just a single 'l' key, and the 'GOTO' command is a single 'g' key.) You can then use 'DELETE' to clear the offending incorrect formula.

--= CHARTS =--
ZXsheet contains a simple bar chart function for visualising your data graphically. For this to work, the first column A must contain your data labels. You can use the 0-7 keys to colour these labels. Then another column should have the data in it. Make sure you have navigated to the HIGHEST value in that column (to correctly set the scale of the bar chart) before pressing the key below:
- ZX Spectrum 48k and 'The Spectrum': CAPS SHIFT+9 (labelled 'GRAPHICS')
- ZX Spectrum+/128k/+2/+3/Next: GRAPH
- Emulator (such as Fuse): SHIFT+9
Your data is displayed as horizontal bars with the values at the ends of each bar. The colour of each bar is taken from the data labels in column A. Press any key to return to your spreadsheet. Troubleshooting: if your bars don't appear how you expect, make sure you had highlighted the HIGHEST value in that column before pressing GRAPHICS/GRAPH.

--= APPENDIX A - QUICK REFERENCE =--
arrow/cursor keys/CAPS SHIFT+5/6/7/8 - move around the spreadsheet
ENTER - edit the current cell
SPACE - toggle calculation mode
0 to 7 - set the colour of the current cell
GRAPHICS/GRAPH/CAPS SHIFT+9 - create a bar chart for the current column of data (ensure you have the highest value selected first)
DELETE/CAPS SHIFT+0 - clear the current cell
C - copy the current cell (if it is text or a formula)
V - paste the contents of the clipboard into the current cell (text as is, or relatively addressed formula)
N - start a new empty spreadsheet (Y to confirm)
S - save the current spreadsheet to tape (or disk if +3) (Y to confirm, then enter filename)
P - print the currently displayed data to a ZX Printer
H - display the help screen (press any key to return to your spreadsheet)

--= APPENDIX B - PROGRAMMER'S NOTES =--
I had been very impressed with a previous BASIC 10 liner contest entry in 2021 called "ZXcel/256" by Nick Shcherbyna. He had managed to cram a fully-featured spreadsheet application into a ZX Spectrum BASIC 10 liner. It included formulas and relative addressing via copy/paste. However it wasn't very practical to use day-to-day due to the slow speed of navigating around the sheet and the long recalculation times. At the end of his description, Nick said "It was a one day hobby project, so there is a lot to improve. Left it as an exercise to the reader." So I thought I'd take him up on the exercise. Mine definitely took more than one day!
My main goals were:
- Match ZXcel/256 in terms of functionality as a minimum
- Make it much faster to navigate, by having manual and automatic calculation modes
- Make the user interface attractive by continuing the look of the Spectrum+ 128k operating system (as in a parallel universe where Sir Clive doesn't get distracted by the QL, and instead makes the Spectrum a productivity powerhouse!)
- Add the ability to save spreadsheets
- Add the ability to create graphs/charts (this was difficult to fit in, and ended up requiring the user to choose the highest value before entering the graphics mode)
I really enjoyed putting this together, and who knows - there might be a full office suite of BASIC 10 liners coming in the future!
Programming tip: This is the first 10 liner I've written that uses a much better method for IF statements within multi-statement lines. In the past, I used FOR n=(opposite condition) TO 0. This worked, but was not easy to follow as it used the opposite of the condition you wanted. I now use FOR n=1 TO (condition). Much easier!

--= APPENDIX C - LINE DESCRIPTIONS =--
Line 1 (253 characters): Initialise the spreadsheet in three arrays: E$ stores what is entered by the user in each cell, S$ has all the cell references evaluated, and V$ is what is shown on screen (truncated to 7 characters). Initialise a blank cell (B$) and two blank lines (X$). Initialise the array of ink colours for each cell (I). Define functions to check if a character is a digit, and to truncate a cell to 7 characters. Set the data read position to line 7. Read in initial values for the write buffer (W$), app name (Z$), text descriptions used in part of the help box (D$), calculation mode (S), on screen position of the current cell (Y,X), x offset when using higher columns (Z), position of source cell for copy/paste (CY,CX) and the Sinclair logo before it is built (L$). Loop through the 6 pairs of colours needed to build the Sinclair logo, reading in the paper and ink codes and adding to L$. For each of the 10 columns, and each of the 20 rows, initialise S$ with "0" in each cell. Flash the border during this process so the user is aware something is happening. This loop takes approx. 8 seconds. DATA for the Sinclair logo user-defined graphic (UDG) piece.
Line 2 (255 characters): Set the data read position to line 1. Read in the 8 lines of UDG data for the logo piece (UDG A). While doing that, also create UDGs for vertical bars on the left (UDG B) and the right (UDG C). Start the main application loop that includes redrawing the whole screen (Q). Set the brightness off, border to white, background to white and ink to black. Clear the screen. If the calculation mode (S) is zero (i.e. the app has just started for the first time), then go to the subroutine on line 9 to display the help box. Set the calculation mode to manual (S=1) then start the loop again (which will clear the screen a redraw without the help box). Set the brightness on and print the black bar at the bottom of the screen containing the app name 'ZXsheet' (Z$) and the Sinclair logo (L$). For each of the 20 rows, display the row number (right justified). Start the application loop which refreshes column headings and cell contents (R). Set the brightness on. Display the (c) symbol at the bottom right if calculation mode is automatic (S=2). For each of the currently displayed columns, print a left bar, two spaces, the column letter name, two spaces and a right bar. Set brightness off. If calculation mode is automatic (S=2) then loop through each row and each currently displayed column...
Line 3 (253 characters): ...If the current cell is a formula (i.e. starts with '=') and calculation mode is automatic (S=2), then set A$ to contain the evaluated cell as a string. Add 7 blank spaces to the front of it and use the T$ function to truncate it. Set V$ for the cell to show the last 7 characters of A$. Regardless of calculation mode, continue to display the sheet as follows: For each of the 20 rows, print the 4 cells going across the screen, including the correct ink colours and allowing for the offset (Z) if you've scrolled further right. Start the main application loop that awaits keyboard input (L). Display the yellow selection bar over the current cell. Display the cell name and colour of the current cell at the bottom of the screen in #1...
Line 4 (251 characters): ...display the contents of the current cell at the bottom of the screen in #1. Start a small loop that checks if a key has been pressed (K) - stores key in K$. Remove the yellow selection bar while ZXsheet 'thinks'. If the 'h' key is pressed, go to the subroutine on line 9 to display the help box then redraw the screen (jump to Q). Update the Y position if the up or down cursor keys are pressed (and you're not at the top or bottom of the screen). If you've already scrolled right, are in the first column on screen and have pressed the 'left' key, then reduce the offset (Z) by 1 and refresh the screen (jump to R). If you haven't scrolled to the furthest right screen and you're in the fourth column on screen and have pressed the 'right' key, then increase the offset (Z) by 1 and refresh the screen (jump to R). Update the X position if the left or right cursor keys are pressed and you're not too far left or right already. If the 'n' key is pressed, prompt the user to confirm they'd like to start a new spreadsheet...
Line 5 (245 characters): Wait for a key press. If 'y' is pressed, then use RUN to reinitialise and start a new spreadsheet. If 'ENTER' is pressed, then display the current cell reference and colour in #1 and use INPUT to get the user's input in the write buffer (W$). If a number key between 0 and 7 is pressed, then set the ink colour for the current cell accordingly (I), and update the colour on screen of the current cell. If 'SPACE' is pressed, then toggle the calculation mode and update the screen (jump to R). If the 'c' key is pressed, set the CY and CX variables to the current cell position. If 'DELETE' is pressed, then clear the current cell in E$, S$...
Line 6 (250 characters): ...and V$ then update the screen (jump to R). If the 'v' key is pressed and the current cell does not start with a digit, then copy the contents of the cell at CX,CY into the clipboard (C$), go to the subroutine on line 10, then set the write buffer (W$) to equal the temporary string from line 10 (F$). If the 's' key is pressed, prompt the user to confirm they'd like to save the spreadsheet. Wait for key press. If 'y' is pressed, then ask for a filename. Save the file using that file name, with it automatically running the saved program from line 2 onwards (to ensure sheet data is intact). Refresh the screen (jump to Q). If the 'p' key is pressed, clear the #1 (bottom of the screen), then COPY the screen to the printer, and refresh the screen (jump to Q). If the cursor is in columns B to J and the 'GRAPHICS' key is pressed, then clear the screen, get the value of the current cell (A) (i.e. the highest value). For each of the 20 rows, get the value of each cell in the current column (B), get the ink value of the cell in the first column (I)...
Line 7 (256 characters): ...print the data label for the bar, then the bar (as a fraction of 18 characters), then the value itself. Once all the bars have been displayed, wait for a key press, then refresh the screen (jump to Q). If the write buffer (W$) isn't empty, then parse the buffer as follows: set the current cell to contain the write buffer (W$) in E$, put "0" in S$ for now, put the first 7 characters in V$ for now. Set the digit flag (C) to true if the first character of the write buffer is a digit or a '+' or a '-'. If the write buffer has more than 1 character, then loop through them. For each character, check that it's a digit or a '.', (update C flag). If the digits flag is still true after the whole buffer has been checked, then set the evaluated cell (S$) to the write buffer (W$), set A$ to contain the evaluated cell as a string. Add 7 blank spaces to the front of it and use the T$ function to truncate it. Set V$ for the cell to show the last 7 characters of A$. DATA for the initial value of the write buffer (W$="").
Line 8 (254 characters): If the first character of the write buffer (W$) is '=' (i.e. formula), then parse the buffer as follows: copy the write buffer (W$) to the clipboard (C$). Go to the subroutine on line 10. Set the evaluated cell (S$) to equal the result of the subroutine (F$) plus the remainder of the write buffer. Set A$ to contain the evaluated cell as a string. Add 7 blank spaces to the front of it and use the T$ function to truncate it. Set V$ for the cell to show the last 7 characters of A$. Empty the write buffer (W$=""). Display the resulting cell on the screen. Move the cursor down to the next cell (unless you're already on the 20th row). Refresh the screen (jump to R). Repeat the main keyboard loop (L). Emergency 'STOP' command just in case. DATA for initial values of Z$, D$, S, X, Y, Z, CY, CX, L$ then the 6 pairs of ink and paper values for the Sinclair logo.
Line 9 (230 characters): This is the subroutine for displaying the help box. Set brightness on. Display the title bar of the help box (including Z$ and L$). Set the data read position to line 9. For the 12 lines of text, read it into A$, then display it (with left and right bars either side). Draw a line along the bottom of the help box. Wait for a key press, then return from the subroutine. DATA containing the lines of help text.
Line 10 (252 characters): This is the subroutine for parsing formulas and replacing cell references with array statements: Set the output to an empty string (F$=""). For each character in the copied write buffer (A), store the ASCII value of the character if it is in the range A to J (even if lowercase) (B). If the first character of the write buffer was '=' and the current character is between A and J (i.e. there's a cell reference), then add one to the loop (A). Copy the loop value into another temporary variable (T) but with 1 added if the next character is also a number (i.e. the cell reference's row number is double digits). Store the value of the cell reference row (J). Set the loop (A) to the temporary variable (T) (i.e. skip one more digit if double digits). If the row is between 1 and 20 and the write buffer isn't empty, then store CHR$176 (VAL) and the array statement that corresponds to the cell reference (e.g. 'C4' gets replaced with 'VAL s$(3,4)') (A$). If the write buffer is empty (i.e. this has been called by the 'paste' routine), then store the offsetted cell reference. Add the result (A$) to the output buffer (F$). Continue the loop (A). Return from the subroutine.

NOTE: All line lengths above were calculated programmatically using 'Ten Liner Counter' from the 2025 BASIC 10 Liner contest.

--= APPENDIX D - VARIABLES =--
- E$(20,10,31) - the spreadsheet stored as entered by the user
- S$(20,10,93) - the spreadsheet with cell references evaluated
- V$(20,10,7) - the spreadsheet as it appears on screen
- B$(7) - blank cell
- X$(64) - two blank lines
- I(20,10) - ink colours for each cell
- W$ - write buffer (starts as "")
- Z$ - app name ("ZXsheet")
- D$ - text descriptions for chart and move (used in the Help screen)
- S - calculation mode (starts as 0, then goes to 1 for manual, 2 for auto)
- Y - y position of current cell on screen (starts as 1, only ever between 1 and 20)
- X - x position of current cell on screen (starts as 1, only ever between 1 and 4)
- Z - x offset (starts as 0). So to get actual x location of a cell, it's z+x
- CX and CY - position of source cell for copy/paste (starts as 1,1)
- L$ - the Sinclair logo including colour codes (starts blank before being initialised)
- N - loop
- A,B - used to read colours for logos during initialisation
- A - used to read in the user-defined graphic of the logo piece
- Q - main loop including redraw of the screen
- R - main loop that refreshes column headings and cell contents
- L - main loop that checks the keyboard
- P,M,I,D - IF statement
- K - IF statement/flag for keyboard input
- A$ - temporary string used when evaluating cells
- C$ - clipboard
- A - used to store the highest value for a bar chart
- I - used to store the ink for each bar in the chart
- C - check flag for digits
- A$ - temporary string used to store lines of help text
- F$ - output buffer from parsing formulas
- B - used to store the ASCII capital value of a column heading
- J - used to store the value of the row number in a cell reference

--= APPENDIX E - FUNCTIONS =--
- D(X$) - is this character a digit or equals sign?
- T$(A$) - truncate A$ to 7 characters
