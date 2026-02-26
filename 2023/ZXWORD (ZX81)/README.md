ZXWORD
======
Written by Matthew Begg for the 2023 BASIC 10-liner competition. Please note that writing programs for the ZX81 in only 10 lines is really difficult as you can only have one statement per line.

Description
===========
ZXWORD is a simple word processor application for the Sinclair ZX81 (16KB RAM pack required). Documents can be saved, loaded and printed as required.

Usage
=====
To start the program, load via LOAD "". 

Just start typing to create your document. You can add text a letter, word, sentence or paragraph at a time. Press NEW LINE to add text to your document.

Press NEW LINE on its own to move to the next line in your document.

There are a few commands that you type starting with a '*' character:

*Dnnn - deletes a number of characters from the document. So, for example, to delete the last 8 characters, type '*D8'. To delete an entire line, use the command '*D32' (no spaces). 

*P - prints the document to the ZX Printer.

*Sfilename - saves the current document to tape with the filename provided. So, for example, to save a document called 'NOTES', use the command '*SNOTES' (no spaces).

To load a previously saved document, load it from tape as you would a normal program (either with LOAD "" or LOAD "FILENAME")

Known issues
===== ======
- There is a hard limit to the length of each document of 639 characters. 
- You can't edit earlier pieces of text, you can only delete from your current position with the '*D' command.
- You can't start entering text with a '?' character as it will crash the program. 
- If the program crashes, type 'GOTO 2' to return to your document without losing your work.

Line descriptions
==== ============
- Line 1 (9 characters): initialise the document (variable D$).
- Line 2 (98 characters): draw the screen including the toolbar at the bottom, the title at the top, the document itself and the cursor.
- Line 3 (8 characters): take input from the user.
- Line 4 (61 characters): add the text entered to the current document (assuming a command hasn't been entered, and you haven't filled the screen).
- Line 5 (65 characters): if the save command is entered (*S), save the document to tape using the filename entered.
- Line 6 (25 characters): if the print command is entered, print the document to the ZX Printer.
- Line 7 (91 characters): if the delete command is entered, delete the provided number of characters from the document.
- Line 8 (116 characters): if NEW LINE is pressed (i.e. no text is entered), go to the next line. This is done by adding a certain number of spaces to the document to get the cursor to the start of the next line.
- Line 9 (54 characters): if the delete command was used earlier, clear the screen to make sure the old characters don't reappear.
- Line 10 (6 characters): end of the main loop. Goes back to line 2 to redraw the screen.

Variables (as they first appear in the program listing)
=========
The entire program only uses two variables:
- D$: string containing the entire document
- I$: string containing the text entered by the user