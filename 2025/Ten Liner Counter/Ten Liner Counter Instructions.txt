--= Ten Liner Counter =--

System Requirements: Sinclair ZX Spectrum 16k/48k/+/128k/+2/+3/Next 

Written by Matthew Begg for the 2025 BASIC 10-Liner Competition (SCHAU category)
Licence: CC BY-SA 4.0

--= LOADING INSTRUCTIONS =--

You can use real hardware or an emulator such as Fuse. Load the tape image into the emulator, but use the MERGE command rather than LOAD if you want to count the lines of an existing program.

Ten Liner Counter can be merged onto the end of an existing BASIC program using the command:

   MERGE "LC"

The code starts at line 100, but use the following command to run it:

   RUN 101

--= INTRODUCTION =--

I've been enjoying taking part in the BASIC 10 Liner contests for the last few years. But one thing that has been quite time consuming is checking whether each line of your BASIC program meets the limits of the competition (80, 120 or 256 characters depending on the category). Other computers store their commands as one byte one character (e.g. Commodore 64) so counting is really easy - just look at the number of lines on the screen. But Sinclair BASIC is tokenised, meaning that commands like 'RANDOMIZE' or 'IF' both only take up one character. I ended up counting them by hand. Until I decided to do something to automate the process...

--= USING TEN LINER COUNTER =--

With your BASIC program already loaded (making sure it is numbered below 101, e.g. lines 1 to 10), merge in the Ten Liner Counter from tape (or a tape image file for emulators) using MERGE "LC". Now run the counter with the command "RUN 101". You'll be prompted to enter how many lines need counting (e.g. 10) and press ENTER. It will begin to count the characters used in each line of the program using the BASIC 10 Liner competition rules. The rules include counting each digit of the line number, plus the following space, then counting each tokenised command as one character.

--= HOW IT WORKS =--

Sinclair BASIC stores the current BASIC program listing from memory location 23755 onwards. The pattern is 0 then the line number, then a checksum then 0 then the line of code then a 13 to indicate the end of the line. Ten Liner Counter programmatically goes through the listing, totting up the number of characters used. In line with the rules of the Ten Liner competition, it adds 1 to the length for the 'space' between the line number and the code. It also looks out for references to numbers as these are stored differently.

--= APPENDIX A - Lines of code =--

100 (5 characters) - STOP command used so that the user's program doesn't accidentally run into the line counter code
101 (25 characters) - Asks the user for how many lines of code to count (e.g. 10)
102 (19 characters) - Start at memory location (m) of 23755 where the program listing begins. Start a loop from 1 to the number of lines of code entered by the user (l)
103 (43 characters) - increment (m) to get past the initial '0'. Initialise (c) to include a space and the length of the line number. Display the line number and a space. Add 3 to (m) to get past the checksum and the next 0
104 (27 characters) - Set (v) to contain the current character code. If (v) is 14, this indicates a number is being stored. This takes an extra 6 bytes so this is skipped. The line is repeated.
105 (37 characters) - Checks if the current character code (v) is 13 which means the end of a line. In which case, print the current count of characters and increment the line loop (n). If the loop finishes, use the STOP statement to end the program.
106 (50 characters) - Set (v) to contain the current character code. If it isn't 0 (or it is 0 and it isn't 0 in 3 characters' time) then increment the counter by one and go back to line 104.
107 (67 characters) - Checks if the current character code is 0 and codes in 3 and 4 characters' time are all 0, in which case 2 is added to the character count and it jumps back to line 104.
108 (15 characters) - failsafe line that again moves to the next character and jumps back to line 104.

NOTE: All line lengths above were calculated programmatically using 'Ten Liner Counter'.

--= APPENDIX B - Variables =--

C : character count for the current line being checked
L : number of lines of code to check
M : memory location (starts at 23755)
N : main loop of lines being checked
V : current character code
