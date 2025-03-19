--= TinyBasic =--

System Requirements: Sinclair ZX Spectrum 16k/48k/+/128k/+2/+3/Next 

Written by Matthew Begg for the 2025 BASIC 10-Liner Competition (SCHAU category)
Licence: CC BY-SA 4.0

--= INTRODUCTION =--

Ever tried writing a BASIC interpreter inside a BASIC interpreter? No? Well, I've done it for you. And not just any BASIC interpreter, but one crammed into a mere ten lines that is a love letter to the early hobbyist pioneers from the 1970s. Prepare for TinyBasic, a testament to the absurd, the impractical, and the strangely compelling. Brace yourselves.

--= LOADING INSTRUCTIONS =--

- Spectrum 16k/48k/+ - type LOAD "" then ENTER. That's 'J' then Symbol Shift+P twice, then ENTER.
- Spectrum 128k/+2/+3/Next - choose "Tape Loader" or "Loader" then ENTER.
- Emulator (e.g. Fuse): load the "TinyBasic.tap" file into your emulator then use the instructions above.

The BASIC interpreter will load and automatically start.

--= HISTORY OF TINY BASIC =--

"Tiny BASIC", a minimalist version of BASIC, emerged in the mid-1970s, playing a crucial role in early personal computing. Designed by Dennis Allison and published in Dr. Dobb's Journal, its small size made it ideal for the first microcomputers with limited resources, empowering hobbyists to program their own homebrew machines. It paved the way for more advanced BASIC interpreters.

My version of TinyBasic is meant to hark back to the look and feel of the early black and green terminal screens with block capitals and a flashing block cursor.

--= USING TINYBASIC =--

TinyBasic is a line-oriented BASIC interpreter. You type commands in full then press ENTER. Commands without a line number are executed immediately. Use line numbers to store your lines of BASIC code. Use LIST to see your program listing. Type line numbers on their own to delete that line. You can overwrite a line by typing the line again with the same line number. Use RUN to start your program from the beginning. You can SAVE your programs to tape/disk (or emulated tape/disk). There is a full explanation of supported commands in the 'TINYBASIC COMMANDS' section of the manual below.

TinyBasic has a few understandable restrictions - some borne out of being written in 10 lines of Sinclair BASIC, and some for historical accuracy (because the original Tiny BASIC had the same restrictions). Things to note:

- It is slow. This is to be expected, as it is an interpreter running on top of an interpreter. PRINT commands are particularly slow to parse. Please be patient. 
- Line numbers can be between 1 and 256. You can stick to the traditional 10, 20, 30... convention if you like, but you'll run out of lines quite quickly like that!
- Variables can only store numbers and are labelled A to Z. There are no arrays and no strings.
- You can only have one BASIC command per line (apart from IF statements). This makes it similar to ZX81 BASIC.
- Lowercase letters are not supported. Uppercase only please.
- If you're unsure of which BASIC commands are supported, type 'HELP' then ENTER to see the full list. There's also a full explanation of each command in the 'TINYBASIC COMMANDS' section of the manual below.
- FOR...NEXT loops can only work incrementally e.g. 1, 2, 3, 4 etc. There is no STEP command.
- Error handling is practically non-existent. Some errors get caught by Sinclair BASIC. If that happens, just type GOTO 2 then ENTER to resume using TinyBasic.
- If typing in lots of lines in a row, sometimes the Sinclair BASIC scrolling routine gets confused and the word 'scroll?' will appear at the bottom. Just press ENTER to continue.
- If your program hangs in an infinite loop, use 'STOP' (symbol shift+A) to 'break' cleanly within TinyBasic. Don't use CAPS SHIFT+SPACE, as that's the break for Sinclair BASIC! If you do, don't panic, just type GOTO 2 then ENTER to get back to TinyBasic.

--= TINYBASIC COMMANDS =--

BEEP <pitch>
  Makes a beep sound for 1/5th of a second. The pitch value is the same as the Sinclair BASIC 'BEEP' command. 
  Example:
    BEEP 0
  plays middle C for 1/5th of a second.

CLEAR
  Initialises all variables back to 0.
  Example: 
    10 LET A=15
    20 CLEAR
    30 PRINT A
  Sets variable A to 15, clears all variables then prints variable A (which is now '0').


CLS
  Clears the screen. 
  Example:
    10 CLS
    20 PRINT "FLASH"
    30 GOTO 10
  Clears the screen, prints "FLASH" then repeats. A simple flashing text routine. Use 'STOP' (symbol shift+A) to break out of the program.


END
  Ends the current program and returns to the TinyBasic prompt.
  Example: 
    10 PRINT "YOU CAN'T LEAVE"
    20 INPUT X
    30 IF X=99 THEN END
    40 GOTO 10
  Prints "YOU CAN'T LEAVE" then waits for a number to be entered. If the user enters 99, then the program ends. Otherwise it continues forever.


EXIT
  Leave the TinyBasic interpreter and return to Sinclair BASIC


FOR <variable>=<start> TO <end>
  Begins a loop. <variable> is a number that will start at <start> and increase by 1 each time the loop runs, until it reaches <end>.  The lines of code between FOR and the matching NEXT statement will be executed repeatedly. See 'NEXT'.
  Example: 
    10 FOR N=1 TO 12
    20 PRINT N*4
    30 NEXT N
  Prints the 4 times table.


GOTO <line>
  Jumps to another line in the program.
  Example:
    10 PRINT "HELLO WORLD"
    20 GOTO 10
  Prints 'HELLO WORLD' then jumps back to line 10 to print it again and again and again... ('STOP' to get out of it)


GOSUB <line>
  Jumps to the subroutine at the specified line number.  Execution continues at that line until a RETURN statement is encountered, at which point the program returns to the line immediately after the GOSUB. See 'RETURN'.
  Example:
    10 PRINT 1
    20 GOSUB 50
    30 PRINT 3
    40 END
    50 PRINT 2
    60 RETURN
  Prints the numbers 1, 2, 3 in the correct order.


HELP
  Lists all the commands that TinyBasic understands. 


IF <condition> THEN <statement>
  Tests the condition provided and, if true, executes the statement. IF statements can be nested.
  Example 1:
    10 PRINT "HOW OLD ARE YOU?"
    20 INPUT A
    30 IF A>40 THEN PRINT "WOW - THAT'S OLD"
    40 GOTO 10
  Asks the user how old they are. If they are over 40, it pokes fun at them.

  Example 2:
    10 INPUT A
    20 INPUT B
    30 IF A=4 THEN IF B=5 THEN PRINT "4 AND 5"
    40 GOTO 10
  If the user enters 4 and 5 then it prints "4 AND 5". You can actually achieve the same outcome by replacing line 30 as follows:
    30 IF A=4 AND B=5 THEN PRINT "4 AND 5"

INPUT <variable>
  Lets the user enter a numerical value which is then stored in the required variable
  Example:
    10 INPUT T
    20 FOR N=1 TO 12
    30 PRINT N*T
    40 NEXT N
  Asks the user to enter a number, then prints the times table for that number.


LET <variable>=<value>
  Assigns a value to a variable.
  Example:
    10 LET A=6
    20 LET B=A+3
    30 LET C=A*B
    40 PRINT A+B+C
  Assigns 6 to A, 9 to B and 54 to C. Then prints the value of all 3 variables added together (69).


LIST
LIST <line>
  Lists the current program. If used on its own, it lists the whole program. If a line number is provided, it starts from that line.
  Example:
    10 PRINT "NOT THIS"
    20 PRINT "THIS"
    LIST 20
  Just lists the last line of the program (20 PRINT "THIS")  


LOAD
  Loads a TinyBasic program from tape (or disk if using the Spectrum +3). Note that you cannot specify a filename, so you'll need to take care with the tapes/disks (or emulated tape/disk images) if loading/saving multiple programs. See 'SAVE'.


MODE <number>
  Customises the TinyBasic display by changing the colour of the text and clearing the screen. Uses the colour numbers on the Spectrum keyboard (1 to 7 accepted - no error checking though so be careful). Defaults to green (4)
  Examples: 
    MODE 7   (white text)
    MODE 6   (yellow text)
    MODE 4   (back to green text)


NEXT <variable>
  Marks the end of a FOR loop. It increments the loop variable <variable> by 1 and checks if the loop should continue. See 'FOR'.
  Example: 
    10 FOR N=1 TO 3
    20 PRINT 4-N
    30 NEXT N
    40 END
  Prints a 3, 2, 1 countdown then ends.


NEW
  Erases the program and variables currently in memory, preparing the interpreter for a new program.


PRINT
PRINT <expression>
PRINT "<string>"
  The PRINT command can take 3 forms:
  - on its own: prints a blank line
  - with an expression: prints the value of the expression
  - with a string: prints the text provided
  NOTE: you can use a semicolon at the end of your PRINT statement so that subsequent PRINT statements continue on the same line. But you can't use semicolons to combine PRINT statements - they must be on separate lines.
  Example:
    10 LET A=4
    20 PRINT 5-A*9
    30 PRINT
    40 PRINT "THAT NUMBER ";
    50 PRINT "WAS -31"
  Sets the variable A to be 4. Prints the value of 5 minus 4 times 9 (-31). Prints a blank line. Prints the text "THAT NUMBER WAS -31".


REM <text>
  Used for adding comments to your program. The interpreter ignores anything following REM on the same line.
  Example:
    10 REM *** GREAT PROGRAM ***
    20 REM *** WRITTEN BY ME ***
    30 PRINT 3
  Just prints the number 3. REM statements are ignored.


RETURN
  Returns from a subroutine to the line after the GOSUB call. See 'GOSUB'.


RUN
  Starts running the current program. If you need to exit a program that's running, press symbol shift + A to get the 'STOP' command.


SAVE
  Saves a TinyBasic program to tape (or disk if using the Spectrum +3). Note that you cannot specify a filename, so you'll need to take care with the tapes/disks (or emulated tape/disk images) if loading/saving multiple programs. You may be prompted 3 times to 'Start tape then press any key'. See 'LOAD'.


--= TINYBASIC FUNCTIONS =--
In addition to the commands above, TinyBasic also understands the following operators and functions:
=,<,>,+,-,*,/,(,),ABS,AND,INT,NOT,OR,PI,RND

Although the "not equals to" operator <> is not supported, you can use NOT to similar effect. For example instead of 'IF A<>B THEN PRINT "DO THIS"', you can use 'IF NOT(A=B) THEN PRINT "DO THIS"'.


--= EXAMPLE TINYBASIC PROGRAMS =--
Try typing in these example programs. Remember to type them in carefully. Use 'LIST' to check the listing after typing. You can overwrite a line by typing the line again with the same line number. Remember to type 'RUN' to start the program.

EXAMPLE 1: GUESS A NUMBER

  5 REM *EX1 GUESS A NUMBER*
  10 CLS
  20 PRINT "I'M THINKING OF A NUMBER"
  30 PRINT "BETWEEN 1 AND 100."
  40 PRINT "CAN YOU GUESS IT?"
  50 LET N=1+INT(RND*100)
  60 LET T=1
  70 INPUT I
  80 IF I<N THEN PRINT "TOO LOW. GUESS AGAIN."
  90 IF I>N THEN PRINT "TOO HIGH. GUESS AGAIN."
  100 IF I=N THEN GOTO 130
  110 LET T=T+1
  120 GOTO 70
  130 PRINT "YOU GOT IT IN"
  140 PRINT T
  150 PRINT "TRIES. PRESS ENTER TO TRY AGAIN"
  160 INPUT I
  170 GOTO 10

EXAMPLE 2: COIN FLIP

  5 REM *EX2 COIN FLIP*
  10 CLS
  20 LET M=100
  30 PRINT "COIN FLIP"
  40 PRINT "==== ===="
  50 PRINT "MONEY LEFT: $";
  60 PRINT M
  70 PRINT "HOW MUCH WOULD YOU LIKE TO BET? $";
  80 INPUT B
  90 IF B>M THEN GOTO 80
  100 PRINT "HEADS (0) OR TAILS (1)?"
  110 INPUT G
  120 LET C=INT(RND*2)
  130 IF C=0 THEN PRINT "HEADS!"
  140 IF C=1 THEN PRINT "TAILS!"
  150 IF G=C THEN PRINT "YOU WIN!"
  160 IF G=NOT C THEN PRINT "YOU LOSE!"
  170 LET M=M-B*(G=NOT C)+B*(G=C)
  180 IF M>0 THEN GOTO 50
  190 PRINT "NO MONEY LEFT"

EXAMPLE 3: HORSE RACE

  5 REM **EX3 HORSE RACE**
  10 LET M=100
  15 CLS
  20 PRINT “HORSE RACE”
  25 PRINT “MONEY LEFT: $”;
  30 PRINT M
  35 PRINT “HORSES:”
  40 PRINT “1. TINY TITAN   4-1”
  45 PRINT “2. BASIC BULLET 8-1”
  50 PRINT “3. GOSUB GAL    3-1”
  55 PRINT "CHOOSE A HORSE (1 TO 3)"
  60 INPUT H
  63 IF H<1 OR H>3 THEN GOTO 55
  65 PRINT "HOW MUCH WOULD YOU LIKE TO BET? $";
  70 INPUT J
  73 IF J>M OR J<1 THEN GOTO 65
  75 LET A=.1
  80 LET B=.2
  85 LET C=.3
  90 LET F=.00004
  95 LET A=A/(1+9*(RND<.25))
  100 LET B=B/(1+9*(RND<.125))
  105 LET C=C/(1+9*(RND<.333))
  110 CLS
  115 PRINT "  S___F"
  120 PRINT 1+A
  125 PRINT 1+B
  130 PRINT 1+C
  135 IF A>F AND B>F AND C>F THEN GOTO 95
  140 IF A<F THEN PRINT "TINY TITAN WINS!"
  145 IF B<F THEN PRINT "BASIC BULLET WINS!"
  150 IF C<F THEN PRINT "GOSUB GAL WINS!"
  155 LET N=-J
  160 IF H=1 AND A<F THEN LET N=J*4
  165 IF H=2 AND B<F THEN LET N=J*8
  170 IF H=3 AND C<F THEN LET N=J*3
  175 LET M=M+N
  180 IF M>0 THEN GOTO 15
  185 PRINT "NO MONEY LEFT!"
  190 PRINT "PLAY AGAIN? (1=YES 0=NO)
  195 INPUT I
  200 IF I THEN GOTO 10

--= APPENDIX A - LINE DESCRIPTIONS =--
Brief line descriptions:
1 - initialise
2 - take input and either execute or add to listing (uses GOSUB 10 and GOSUB 8)
3 - run commands 1: HELP, EXIT, CLS, END, GOTO, INPUT, CLEAR
4 - run commands 2: LIST, NEW, MODE, GOSUB, RETURN
5 - run commands 3: PRINT, SAVE (DATA)
6 - run commands 4: LOAD, BEEP, IF, BREAK (DATA)
7 - run commands 5: LET, FOR, NEXT (DATA)
8 - SUB parse the line
9 - continue to parse the line (DATA)
10 - SUB process input from user (DATA)

Detailed descriptions:

Line 1 (251 characters) - INITIALISE
Turn the screen black with green writing. Define a function (n(w$)) for testing if a character is a number or not. Define a function (c(x)) for adding 214 to an ASCII value (to convert from a command number to an ASCII code). Define a function (h()) to set the highest line. POKE 23658,8 sets Caps Lock on so everything is uppercase. Initialise arrays k$, j, j$, l$, p$, b$, c, v, p, f (see 'Variables' below for details). Read in initial values for t$, u, h, i. Read in the 30 command names and command numbers, and store them in arrays along with their lengths and their ASCII equivalents. Display the 'TINYBASIC V1.0' title and the word 'READY'.

Line 2 (256 characters) - TAKE INPUT AND EXECUTE/ADD TO LISTING 
Set input mode (i) to 1 (meaning string input). Calls the input subroutine on line 10 to get input from the user. Sets current line (l) to 0 (meaning interactive). Checks that the line entered by the user (s$) is not blank. If the command is 'RUN', cycle through each line of the program (up to the highest line h), check each line isn't blank, set the current line (c$) to the line in the program, and call the main running subroutine on line 3. If the first character is a number, then go to the parser/tokeniser subroutine on line 8. If the line is 3 characters or fewer, clear the corresponding line in the program. Go through the line entered by the user a character at a time. If it's not a number, set the current line (l) to the value of the previous characters (allows for line numbers that are 1, 2 or 3 digits long). Calls the parser/tokeniser on line 8. Stores the parsed line used by the computer in l$(l) and stores the line to be printed on screen in p$(l). Stores the length of the printed line in p(l). Updates the highest line. Repeats line 2.

Line 3 (254 characters) - RUNNING COMMANDS PART 1 (HELP, EXIT, CLS, END, GOTO, INPUT, CLEAR)
Command 35 (HELP): POKE 23692,255 enables scrolling. Displays the word 'COMMANDS' then goes through the first 21 commands and displays them on the screen in two columns.
Command 9 (EXIT): POKE 23658,0 turns off Caps Lock then stops TinyBasic to return to Sinclair BASIC.
Command 37 (CLS): clears the screen using CLS.
Command 12 (END): display the word 'END' and the current line number. Return to take input on line 2.
Command 22 (GOTO): sets the current line (l) to the value given with 1 subtracted (so that when it increments, it goes to the correct required line).
Command 24 (INPUT): set the input flag to 2 (meaning it only accepts numbers). Call the input subroutine on line 10. Check the inputted value isn't blank, then set the provided variable to that value.
Command 39 (CLEAR): reinitialises the variables array (v(36)).

Line 4 (249 characters) - RUNNING COMMANDS PART 2 (LIST, NEW, MODE, GOSUB, RETURN)
Command 26 (LIST): POKE 23692,255 enables scrolling. Cycle through each line of the program (up to the highest line h), check the line isn't blank and it's not earlier than the option line number provided, then print the line to the screen.
Command 16 (NEW): resets TinyBasic by running the whole thing from the beginning (RUN).
Command 3 (MODE): sets the ink colour to the number specified, then clears the screen (CLS)
Command 23 (GOSUB): Increment the GOSUB pointer (V(27)) by 1. Store the current line number in that pointed to variable. Set the current line number to the line number provided with 1 subtracted (so that when it increments, it goes to the correct required line). 
Command 40 (RETURN): Checks that the GOSUB pointer (V(27)) is greater than 0. Sets the current line to the pointed to variable. Subtracts 1 from the GOSUB pointer V(27)). Ends the 'l' FOR loop early.

Line 5 (255 characters) - RUNNING COMMANDS PART 3 (PRINT, SAVE)
Command 31 (PRINT): Adds a space to the end of the current line. POKE 23692,255 enables scrolling. Cycle through each character of the current line backwards from the end. Set a temporary flag (z) to record the position of the first non-space character from the end. End the m loop if a non-space character is found. Set temporary flag (y) if the last character is a semicolon. If the first character after the PRINT command is a quote mark or there's nothing after the PRINT command, then print the rest of the current line (minus the final quote mark and possible semicolon). If the first character after the PRINT command is not a quote mark and there is something after the PRINT command, then print the value of the expression. If there's no semicolon at the end, print a carriage return.
Command 34 (SAVE): Save 3 arrays: L$() contains the lines used by the computer, P$() contains the lines used when printing, P() contains the lengths of the lines to print.
DATA statement containing the title ("TINYBASIC V1.0")

Line 6 (232 characters) - RUNNING COMMANDS PART 4 (LOAD, BEEP, IF, BREAK)
Command 25 (LOAD): Load 3 arrays: L$() contains the lines used by the computer, P$() contains the lines used when printing, P() contains the lengths of the lines to print. Clear the screen, and set the highest line to 256.
Command 1 (BEEP): Sound the beeper for 0.2 seconds using the value provided as the pitch. Same values as Sinclair BASIC beep (e.g. 0 is middle C, 2 is D, 4 is E, 5 is F etc)
Command 36 (IF): Cycle through the rest of the IF statement one character at a time. Set the temporary flag z to the position of the 'THEN' statement. Test the expression given between the IF and THEN statements to see if it is true. If true, then let the current line (c$) equal everything after the THEN statement and go back to line 3 to run the relevant commands.
BREAK: tests to see if the STOP key (symbol shift and A) is currently pressed. If so, display "BRK AT " and the current line number. Jump back to take input on line 2.
DATA statement containing initial values for FOR loop level (U=0), highest line number (H=1), input mode flag (I=1 meaning string input)), and the start of the command names and command numbers.

Line 7 (253 characters) - RUNNING COMMANDS PART 5 (LET, FOR, NEXT)
Command 27 (LET): set temporary flag (z) to whether or not the variable number is 2 digits or 1. Set variable to the expression given (using 'z' to work out the position in the line of these values).
Command 21 (FOR): increase the FOR loop level (U) by 1. Set temporary flag (z) to whether or not the variable number is 2 digits or 1. Set y to be the variable number. Set the variable v(y) to be the initial value of the loop. Set the FOR array value to the value needed to end the loop. Set the FOR array line to go back to to the current line. 
Command 29 (NEXT): Set temporary flag (y) to whether or not the variable number is 2 digits or 1. Set z to be the variable number. Increment the FOR variable by 1. Set temporary flag m to be whether or not the FOR variable has reached/exceeded the needed value to end the loop. Set the current line accordingly (either jumping back to the FOR statement, or continuing on). Decrease the FOR loop level (U) by 1. 
RETURN to the line that called the running commands routine.
DATA statement with more command names and command numbers.

Line 8 (252 characters) - PARSER/TOKENISER SUBROUTINE PART 1
Initialise D$ (which will contain the line as it is parsed). Set the 'is it a string' flag to 0 (S). Cycle through the current line (s$) one character at a time. Set temporary variable z$ to equal the current character. If the current character is a quote mark, toggle the 'is it a string' flag (S). If the current character isn't a space (or it is a space but we're in a string), then cycle through the 30 possible commands and see if the current character (plus the length of the possible command) matches a command. If it does, then add the ASCII character with that command's token to D$. Add the character to D$ if it's not a command. Repeat this for the whole line. Initialise C$ (which will contain the final line). Set the 'is it a string' flag to 0 (S). Cycle through the parsed line (d$) one character at a time. Set temporary variable z$ to equal the current character. If the current character is a quote mark, toggle the 'is it a string' flag (S). If we're not in a string and the current character is between 'A' and 'Z'...

Line 9 (255 characters) - PARSER/TOKENISER SUBROUTINE PART 2
...then replace it with a V(number) array reference. Add the current character to the final list (c$). RETURN to the line that called the parser/tokeniser.
DATA statement with more command names and command numbers.

Line 10 (252 characters) - INPUT SUBROUTINE
Initialise S$ (the line entered by the user). Display the flashing block cursor. Start an infinite loop. Use 'PAUSE 0' to await a key press. Set i$ to equal the character typed by the user. Check that the character entered is valid (depends on whether the input mode is set to expect just a number or a string). If valid, add the character to S$, rub out the block cursor, print the character, then print the block cursor again. If DELETE is pressed and there's at least 1 character in the line entered, then reduce the length of the line by one (deleting the last character), rub out the block cursor, go back 2 characters and display the block cursor again. Check if ENTER has been pressed. If not, repeat the loop. If it has, rub out the block cursor and RETURN to the line that called the input routine.
DATA statement with more command names and command numbers.

NOTE: All line lengths above were calculated programmatically using 'Ten Liner Counter'.

--= APPENDIX B - VARIABLES =--
- Array B$(20) = blank line
- Array F(26,2) = for loops for each variable 1=value to reach 2=line to go back to
- Array K$(32,6) = keywords
- Array J(32) = length of keywords (1-32)
- Array J$(32) = chr$ of replacement keyword
- Array L$(256,50) = lines used by computer
- Array P$(256,50) = lines used to print
- Array P(256) = length of the lines to print
- Array V(36) = variables and go sub levels (go sub counter 27, 28 onwards for line to return to)

- String C$ = current line (final)
- String D$ = current line (being parsed)
- String I$ = INKEY$
- String S$ = line entered by user
- String T$ = TINYBASIC V1.0
- String Z$ = temporary 

- Number H = highest line number
- Number I = FLAG input mode (1=string, 2=number)
- Number L = current line (0 for interactive)
- Number M = FOR loops/temporary
- Number N = FOR loops
- Number S = FLAG is a string
- Number U = current level of FOR
- Number Y = temporary
- Number Z = temporary


--= APPENDIX C - FUNCTIONS =--

N(W$) - is the string a numerical digit?
C(X) - convert command number to an ASCII code
H() - set highest line
