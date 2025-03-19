ZX Alarm Clock
== ===== =====
Written by Matthew Begg for the 2023 BASIC 10-liner competition

Description
===========
'ZX Alarm Clock' recreates the classic bedside alarm clock with 7 segment displays. It uses the 24 hour clock system. Designed for the Sinclair ZX Spectrum 16k/48k/128k.

Usage
=====
To start using the clock, load the program via LOAD "" or 'Tape Loader'. The clock shows '8888' flashing. Now enter the current time in 24 hour format (e.g. '1524' if it is 3:24pm). Press 'a' to set the alarm time. When the alarm is sounding, the border will light up and the beeper will sound. Press 'a' to turn the alarm off. Use the number keys to change the colour of the clock.

Keys
====
'1' to '7' changes the colour of the clock
'a' sets/unsets the alarm (enter alarm time when digits are flashing)
's' sets the current time

Known issues
===== ======
- You have to type the time in quite slowly otherwise you'll get an error
- Currently there is no 'snooze' option - feel free to amend the code to add this

Listing
=======
   1 BRIGHT 1: LET i=2: INK i: L
ET a=0: LET a$="8888": LET t$="8
888": BORDER 0: PAPER 0: CLS : D
IM s$(10,7): FOR n=1 TO 10: READ
 s$(n): NEXT n
   2 FLASH 1: GO SUB 8: FLASH 0:
 FOR n=1 TO 4: PAUSE 0: LET t$(n
)=INKEY$: LET x=n: GO SUB 9: NEX
T n: LET it=VAL t$(3 TO 4)+(VAL
t$(1 TO 2)*60): POKE 23672,0: PO
KE 23673,0: POKE 23674,0: GO SUB
 8
   3 LET t=it+INT ((65536*PEEK 2
3674+256*PEEK 23673+PEEK 23672)/
3000): LET h=INT (t/60): LET m=t
-h*60: LET n$=STR$ INT (h/10)+(S
TR$ h)(LEN STR$ h)+STR$ INT (m/1
0)+(STR$ m)(LEN STR$ m): IF n$<>
t$ THEN LET t$=n$: IF h<24 THEN
GO SUB 8
   4 PRINT INK a*i;AT 18,7;"((A)
)": LET p=PEEK 23672: PRINT INK
(p<64 OR (p>127 AND p<192))*i;AT
 9,15;"  ";AT 13,15;"  ";: IF h>
23 THEN LET it=0: POKE 23672,0:
POKE 23673,0: POKE 23674,0
   5 LET k$=INKEY$: IF k$>"0" AN
D k$<"9" THEN LET i=VAL k$: GO S
UB 8
   6 IF k$="a" THEN LET a=NOT a:
 IF a THEN LET t$="8888": FLASH
1: GO SUB 8: FLASH 0: PAUSE 5: F
OR n=1 TO 4: PAUSE 0: LET t$(n)=
INKEY$: LET x=n: GO SUB 9: NEXT
n: LET a$=t$: GO TO 3
   7 PAUSE 5: BEEP (a$=t$)*a*.2,
0: BORDER (a$=t$)*a*i: GO TO 3-(
k$="s")
   8 FOR m=1 TO 4: LET x=m: GO S
UB 9: NEXT m: RETURN : DATA "101
1111","0000101","1110110","11101
01","0101101","1111001","1111011
","1000101","1111111","1111101"
   9 FOR y=1 TO 3: PRINT AT 3+y*
4,-3+x*7; INK (i*(VAL s$(VAL t$(
x)+1,y)));"   ";AT 7+y,-4+x*7; I
   1 BRIGHT 1: LET i=2: INK i: L
ET a=0: LET a$="8888": LET t$="8
888": BORDER 0: PAPER 0: CLS : D
IM s$(10,7): FOR n=1 TO 10: READ
 s$(n): NEXT n
   2 FLASH 1: GO SUB 8: FLASH 0:
 FOR n=1 TO 4: PAUSE 0: LET t$(n
)=INKEY$: LET x=n: GO SUB 9: NEX
T n: LET it=VAL t$(3 TO 4)+(VAL
t$(1 TO 2)*60): POKE 23672,0: PO
KE 23673,0: POKE 23674,0: GO SUB
 8
   3 LET t=it+INT ((65536*PEEK 2
3674+256*PEEK 23673+PEEK 23672)/
3000): LET h=INT (t/60): LET m=t
-h*60: LET n$=STR$ INT (h/10)+(S
TR$ h)(LEN STR$ h)+STR$ INT (m/1
0)+(STR$ m)(LEN STR$ m): IF n$<>
t$ THEN LET t$=n$: IF h<24 THEN
GO SUB 8
   4 PRINT INK a*i;AT 18,7;"((A)
)": LET p=PEEK 23672: PRINT INK
(p<64 OR (p>127 AND p<192))*i;AT
 9,15;"  ";AT 13,15;"  ";: IF h>
23 THEN LET it=0: POKE 23672,0:
POKE 23673,0: POKE 23674,0
   5 LET k$=INKEY$: IF k$>"0" AN
D k$<"9" THEN LET i=VAL k$: GO S
UB 8
   6 IF k$="a" THEN LET a=NOT a:
 IF a THEN LET t$="8888": FLASH
1: GO SUB 8: FLASH 0: PAUSE 5: F
OR n=1 TO 4: PAUSE 0: LET t$(n)=
INKEY$: LET x=n: GO SUB 9: NEXT
n: LET a$=t$: GO TO 3
   7 PAUSE 5: BEEP (a$=t$)*a*.2,
0: BORDER (a$=t$)*a*i: GO TO 3-(
k$="s")
   8 FOR m=1 TO 4: LET x=m: GO S
UB 9: NEXT m: RETURN : DATA "101
1111","0000101","1110110","11101
01","0101101","1111001","1111011
","1000101","1111111","1111101"
   9 FOR y=1 TO 3: PRINT AT 3+y*
4,-3+x*7; INK (i*(VAL s$(VAL t$(
x)+1,y)));"   ";AT 7+y,-4+x*7; I
NK (i*(VAL s$(VAL t$(x)+1,4)));"
 ";AT 7+y,x*7; INK (i*(VAL s$(VA
L t$(x)+1,5)));" "
  10 PRINT AT 11+y,-4+x*7; INK (
i*(VAL s$(VAL t$(x)+1,6)));" ";A
T 11+y,x*7; INK (i*(VAL s$(VAL t
$(x)+1,7)));" ": NEXT y: RETURN

Line descriptions
==== ============
- Line 1 (137 characters) - initialises the screen, reads in the segment patterns
- Line 2 (188 characters) - flashes the digits and lets the user enter the current time. Sets the initial time and resets the timer addresses in memory
- Line 3 (226 characters) - gets the current time from timer addresses, converts to hours and minutes and updates the time on the screen if it has changed
- Line 4 (179 characters) - displays the alarm indicator and updates the flashing colon. Tests if midnight has been reached
- Line 5 (63 characters) - gets keyboard input. Checks if the number keys have been pressed and changes the display colour if so
- Line 6 (174 characters) - checks if the alarm has been set/unset. Gets the alarm time from the user
- Line 7 (66 characters) - sounds the beeper and lights up the border if the alarm time is reached. Also checks if the user wants to set the time again with 's' key
- Line 8 (154 characters) - routine for updating all four digits on the screen. Also contains the DATA statement with the segment patterns
- Line 9 (173 characters) - routine for drawing one digit (part 1)
- Line 10 (122 characters) - routine for drawing one digit (part 2)

Variables (in order they appear in the listing)
=========
i - ink colour
a - alarm flag (0=not set, 1=set)
a$ - alarm time in "hhmm" format
t$ - current time in "hhmm" format
s$ - array containing the segment patterns for displaying each digit
n and m - temporary variables used for loops
x - current digit being updated (1 to 4)
it - initial time (total minutes)
t - current time (total minutes)
h - current hours
m - current minutes
n$ - new time (for checking against t$ to see if time has changed)
p - copy of timer variable used for the flashing of the centre ':'
k$ - current key being pressed by the user
y - vertical position of segment
DATA contains the segment patterns for each digit
 
