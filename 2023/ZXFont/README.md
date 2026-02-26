ZXFont
======
Written by Matthew Begg for the 2023 BASIC 10-liner competition

Description
===========
The Sinclair Spectrum has a fixed font stored in ROM, but there is a trick that allows the computer to use custom fonts. This is a font editor written in just ten lines of BASIC code that lets the user create their own fonts and save them to tape for use in their own BASIC programs.

Usage
=====
To start the editor, load the program via LOAD "" or 'Tape Loader'. The editor takes about 10 seconds to copy the SYSTEM font into the CUSTOM memory space. You can select a character using the left/down/up/right arrow keys, then ENTER to move to the character editor. The character is then displayed enlarged in the centre of the screen. Use the arrow keys to move around and press the '0' (zero) key to toggle the pixel on and off. When you've finished, press ENTER to return to the main screen. You can save the whole character set to tape (press 's'), or load a previously saved character set (press 'l'). If you're unsure which character is which, the current character code is shown at the bottom left, and you can press 't' to toggle between the SYSTEM and CUSTOM fonts.

Keys - Main Screen
==== = ==== ======
'L' - load a character set from tape
'S' - save a character set to tape
'T' - toggle using the CUSTOM or SYSTEM font
Arrow keys to move around the character set
ENTER to edit the character

Keys - Editing Screen
==== = ======= ======
Arrow keys to move around the character
'0' (zero) - turn current pixel on or off
ENTER to exit editing mode

Using fonts in your own programs
===== ===== == ==== === ========
Character sets are saved as 768 bytes that you store at address location 64000. If you want to use the fonts you save with ZXFont, use these BASIC commands in your own programs:

CLEAR 63999: LOAD "" CODE 64000,768

To switch from the system font to your loaded custom font, use this command:

POKE 23607,249      (points the Spectrum to location 64000 in RAM for the font)

And to switch back to the system font:

POKE 23607,60.      (points the Spectrum to location 15616 in ROM for the font)

Line descriptions
==== ============
- Line 1 (144 characters) - empty the memory at location 64000 ready for the font. Copy the system font from ROM into RAM at 64000.
- Line 2 (186 characters) - read the data statements into the phrases array and set up the user-defined graphics for the arrows.
- Line 3 (214 characters) - set the font to either system or custom depending on the 't' flag. Clear and draw the main screen. Some data stored here.
- Line 4 (210 characters) - show the CHR$ number and check for input. Check if ENTER is pressed then go into Edit mode on line 7. Check if 's' is pressed for saving the font to tape.
- Line 5 (158 characters) - if arrow keys are pressed, move the cursor.
- Line 6 (215 characters) - if 'l' is pressed, load a font from tape. If 't' is pressed, toggle the system/custom font flag (actioned on line 3). Loop back to line 4. Some data stored here.
- Line 7 (251 characters) - Edit mode. Display the current character large in centre of screen. Set edit cursor at top left of edit area.
- Line 8 (235 characters) - check for input. Move cursor accordingly.
- Line 9 (198 characters) - if ENTER is pressed, goto line 10. If zero is pressed, toggle the bit onscreen between an underscore or block character. Loop back to line 8.
- Line 10 (193 characters) - write the edited character back to memory. Go back to the main mode on line 3.