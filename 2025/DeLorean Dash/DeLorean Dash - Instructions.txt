--= DeLorean Dash =--

System Requirements: Sinclair ZX Spectrum 16k/48k/+/128k/+2/+3/Next 

Written by Matthew Begg for the 2025 BASIC 10-Liner Competition (EXTREME-256 category)
Licence: CC BY-SA 4.0

Players: 1

--= INTRODUCTION =--

Great Scott! Biff's gone rogue and messed with the space-time continuum. Again! Doc is frantic, his hair even more wild than usual. Apparently, Biff hopped in the DeLorean and hid crucial items from different time periods, rewriting history for his own nefarious ends. 

The good news? You, Marty McFly, are on the case. Doc's rigged the DeLorean for short time jumps, but there's a catch: in each era, Biff's left a trail of chaos – a sleek stallion in 1885, a souped-up hot rod in 1955, Marty’s dream pickup in 1985 and a tricked-out hoverboard in 2015 – and you gotta race them all to get the stolen items back. Buckle up McFly - it's time to hit the gas and set history straight, one time warp at a time!

--= LOADING INSTRUCTIONS =--

- Spectrum 16k/48k/+ - type LOAD "" then ENTER. That's 'J' then Symbol Shift+P twice, then ENTER.
- Spectrum 128k/+2/+3/Next - choose "Tape Loader" or "Loader" then ENTER.
- Emulator (e.g. Fuse): load the "DeLorean Dash.tap" file into your emulator then use the instructions above.

The game will load and automatically start the title sequence.

--= CONTROLS =--

- Press any key on the title screen to start
- 1 to 4: choose a time period to travel to
- N and M: press these keys alternately to drive your DeLorean. It is not necessary to press them super fast - just to find a steady rhythm
- Press any key after each race to return to the year select screen.

--= GAMEPLAY =--

Once loaded, you are shown the game logo and a short tune will play. You start the game in 1985. The four time periods are displayed - press a number from 1 to 4 to travel through time. Consult the time circuits at the bottom left of the screen - each journey must be to a different year than the one you're in now. Once your DeLorean hits 88 mph, the time circuits will engage, sending you hurtling through the space-time continuum.

Once you arrive, a vehicle from that year will race you across the screen. After a 3, 2, 1 countdown, the race begins. Press the keys 'N' and 'M' in a steady rhythm (not necessarily the fastest) to drive the car. If you make it to the end before your opponent, you'll win an item which will appear in your inventory on the bottom right of the screen. Watch out though - Biff has been known to follow you and randomly steal items when you least expect it. So you may need to win back those items again. Press a key to choose another year.

Once all 4 items appear in your inventory, they will flash and the game will end. Press ENTER to start the game again.

GAMEPLAY TIP: Strugging to win races? You might be pressing 'N' and 'M' too quickly. There's an optimum steady speed that you'll need to find.

--= VEHICLES AND ITEMS =--

1. September 2nd 1885 - Buford "Mad Dog" Tannen's Horse - Clara Clayton's Telescope
2. November 5th 1955 - Biff Tannen's Ford Super De Luxe - Lorraine Baines' Dress
3. October 26th 1985 - Marty McFly's Toyota SR5 Xtra Cab - Doc Brown's Video Camera
4. October 21st 2015 - Griff Tannen's Hoverboard - Grays Sports Almanac

--= APPENDIX A - LINE DESCRIPTIONS =--

Line 1 (254 characters): Set the speed of the music (m) to .15. Set border flash (b) to 0. Initialise arrays to hold the text (t$), a blank line (b$), the music notes (m()) and music note durations (d()). Set screen brightness on, set border to black, paper to black and ink to white. Clear the screen. Read 32 lines of text. Read the 10 music notes and durations. Animate the logo to fly in from the right of the screen to the centre. Animate the bottom of the logo appearing top to bottom. Print the 'DeLorean Dash' title then play the theme tune. Start to read the user defined graphics (UDGs) data.

Line 2 (256 characters): Read the UDGs. Set the current level (l) to 3 (which is 1985). Wait for key press. Animate the DeLorean driving from left to right of the screen flashing the border as it goes. Clear the screen. Draw the screen layout, including the logo on the bottom right and the time circuits on the bottom left.

Line 3 (245 characters): Draw the rest of the time circuits and the inventory. Then draw the year selections 1 to 4. Wait for key press then store it in k$. If 1 to 4 is pressed (and it isn't the same level you're already on) then continue. Update the time circuits dates and call the subroutine on line 6. Set z$ to the colours needed to draw the level (5=cyan for the sky, 4=green for the ground). Set y$ to the ink colours of the other vehicles. Set c$ to contain the DeLorean itself.

Line 4 (250 characters): Set e$ to contain the enemy vehicle. Print the names of the vehicles racing and the instructions. Draw the playing field (using b$ coloured as per z$). Draw the two vehicles (DeLorean and enemy). Do the 3, 2, 1 countdown with sounds. Initialise x() to contain the horizontal positions of the vehicles. Set k to 1 (used to work out if 'n' or 'm' need to be pressed next so you can't just press one of them repeatedly). Begin main game loop (n). Increment the enemy x position by a random amount between 0 and 2). Check if the correct 'n' or 'm' key has been pressed.

Line 5 (256 characters): If the correct key was pressed, increment the DeLorean x position by 1, then toggle k to expect the opposite key next time. Redraw both vehicles. Exit the game loop if either car reaches the end of the screen. End of the main game loop. Play a note. Decide if Biff steals an item - a random number between 1 and 6 has to match the level number (1 to 4) you're on. If so, display "Biff stole the " and the item's name. Update the inventory to remove the item. If you won the race, display "You found the " and the item name, then add it to the inventory. Run the subroutine on line 9. Wait for a key to be pressed.

Line 6 (256 characters): Subroutine for the transition from the year select screen to the game itself. Clear the screen, draw the DeLorean going across the screen with the speed up to 88 miles an hour. Incrementing beep sound as it drives. Update the level number. Update the time circuit text.

Line 7 (253 characters): Data statement containing the logo graphics and some of the text used in the game.

Line 8 (252 characters): Data statement containing more text used in the game.

Line 9 (256 characters): Subroutine for checking if the game has ended. Data statement containing text for the game and some UDGs

Line 10 (256 characters): Data statement containing the rest of the UDGs

NOTE: All line lengths above were calculated programmatically using 'Ten Liner Counter'.

--= APPENDIX B - VARIABLES =--

- A: temporary read
- B: border flash flag
- B$(32): blank line
- C$: car
- D(99): music duration
- D$: destination level date text
- E: ink of enemy
- E$: enemy car
- K: toggle key between N and M
- K$: key pressed
- L: current level
- L$: current level date text
- M(99): music notes
- M: speed of music
- N: temporary loop
- O: temporary loop
- P: temporary loop
- P$: previous level date text
- R: random number to determine if item is stolen
- T$(9,40): title graphics (first 6) then strings 
- X(2): positions of vehicles during the race
- Y$: order of colour ink for enemies 0610
- Z$: order of colour paper to draw 5540554

 