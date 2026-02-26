BimMobiles
==========
Written by Matthew Begg for the 2023 BASIC 10-liner competition. From an original concept by Matthew Begg and Richard Begg.

Description
===========
The red car and the blue car had a race. Except these 'cars' are BimMobiles from the planet Bim. It is the year 3456, and the Bimmers are at war again. Their planet is exactly one half red, one half blue. The two factions battle it out in the BimMobiles arena in a bid to turn the planet entirely to their colour. 

This is a two-player only game inspired by the light cycles in the film 'Tron'. Try to stay alive as long as possible without crashing into a wall, your opponent's trail or your own trail. First to five points wins.

Usage
=====
To start the game, load the program via LOAD "" or 'Tape Loader'. If running in an emulator, I recommend setting the emulation speed to 200% or 300%. Those of you lucky enough to be running this on a ZX Spectrum Next may want to switch into 7 or 14 MHz mode.

The welcome screen explains the controls and simple rules. Then there's a countdown: 3...2...1...

Player 1 uses the arrow keys (ZX Spectrum+, ZX Spectrum+ 128k, +2/+3) to control their vehicle. If using the original rubber keyed Spectrum 16k/48k, the arrow keys are accessed via CAPS SHIFT + 5 to 8.

Player 2 uses a Kempston joystick.

Score a point whenever your opponent crashes. Try and score 5 points before your opponent does.

Improvements
============
Speed performance is an issue (hence recommendations to increase CPU speed in emulators or on the Next). I may investigate trying a BASIC compiler to see if that helps increase speed on original hardware (not for this competition of course!)

Line descriptions
==== ============
- Line 1 (137 characters) - clear the screen. Set up the text array (for instructions), and the position arrays. Read in the text.
- Line 2 (101 characters) - set up the direction arrays and choose a random-ish start location for each player.
- Line 3 (218 characters) - clear the screen, draw the white play area borders and the 'BimMobiles' text at the top. If it is the first time through, load the subroutine on line 9 that shows the instructions to the players.
- Line 4 (157 characters) - draw each player's BimMobile, then start a '3...2...1...' countdown. 
- Line 5 (86 characters) - draw the BimMobiles again. Get the key input (k) and the joystick input (j)
- Line 6 (237 characters) - adjust the blue vehicle's direction if arrow keys are pressed. Adjust red vehicle's direction if the joystick is used. Update positions of both cars.
- Line 7 (245 characters) - check that the new position is a black square (i.e. isn't occupied by a vehicle's trail, or boundary). If it is, update the opponent's score, change the colour of 'BimMobiles' logo, and flash the score. Go to line 2 if the score isn't 5, or go to line 10 if it is. End of main loop - go back to line 5.
- Line 8 (70 characters - contains data statement for the welcome screen text.
- Line 9 (247 characters) - displays the welcome text. Waits for ENTER to be pressed to start the game (i.e. return from subroutine). If ENTER isn't pressed, repeat line 9.
- Line 10 (77 characters) - displays the 'Winner' message then resets the game by going to line 1.

Variables (as they first appear in the program listing)
=========
- a$ : string array that contains the four lines of welcome text
- s : array that holds the two players' scores
- x : array that holds the two players' x position
- y : array that holds the two players' y position
- s : flag to show welcome text the first time only
- n, m and o : used throughout as temporary FOR loop variables
- r : array that holds the horizontal direction of each player (-1 left, 0, or 1 right)
- d : array that holds the vertical direction of each player (-1 up, 0 stay still, or 1 down)
- k : the character code of the pressed key
- j : the value of the joystick input
- w : the winning player (1 or 2)