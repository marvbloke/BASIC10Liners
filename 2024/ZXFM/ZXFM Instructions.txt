ZXFM
====

Written for the ZX Spectrum by Matthew Begg (licence: CC BY-SA 4.0)

Compatible with Sinclair ZX Spectrum 16k/48k/+/128k/+2/+3/Next

Players: 1
Controls: Keyboard
How to start the game: LOAD "" or LOAD "ZXFM". The game will auto-start.

INTRODUCTION

ZXFM is a football management simulator for the Sinclair ZX Spectrum written in just 10 lines of BASIC! Play an entire season as manager of a team from your favourite league, or create your own leagues and teams. Manage injuries, buy and sell in the transfer market and save your progress to tape or disk as you go along. ZXFM was inspired by the original 1982 "Football Manager" game by Kevin Toms (which was also written in BASIC but used over 700 lines of code!)

PLAYING THE GAME

You have 20 teams to choose from. Team 1 has the highest rating, Team 20 has the lowest, so choose your team wisely depending on how much of a challenge you want. Type the number of the team you want and press ENTER. 

-= League Table screen =-
Use the 'R' key to rename a team and change its colours. Type the number of the team to rename and press ENTER. Enter the name you want (up to 14 characters) then press ENTER. Type the colour number for the ink (foreground) and paper (background) you want. Keep pressing 'R' to change more teams' names and colours. See Appendix A of this document for some example leagues you can type in. When you're happy with the league table, press any other key (e.g. ENTER). You can get back to the League Table screen any time using the 'T' key.

-= Team Selection screen =-
By default, the names of your players are randomly generated. Use the 'N' key to rename a player. Enter the name you want (up to 14 characters) and press ENTER. Keep pressing 'N' to change more players' names.

The team selection screen is laid out at follows:
- 'W' shows the current week number
- 'Rtg' shows the overall team rating
- 'Money' shows how much money you have available to spend. This increases each week due to ticket sales and TV money, and also increases when you sell players. It decreases when you buy players
- The main table shows the number, name, position (G=goalkeeper, D=defence, M=midfield, S=striker), rating and money value of each player. The players in positions 1 to 11 are the ones counted towards your overall team rating (shown at the top) and are your chosen team. The players in grey (positions 12 to 18) are available to you if you wish to swap (perhaps to increase your team rating or due to injury). Injured players are shown in red and do not count towards your team rating, so you'll need to use the 'Move' command to bring someone else in for them
- 'Next game' shows who your next opponent is. Twice during the season, it'll be the international break which means no fixture to play (although you can still buy/sell players)

-= Main Menu =-
Press the first letter (shown as a capital) of each option to select it:
- 'M' for Move: moves/swaps two players in your team. Type the player numbers (each followed by ENTER) to make the swap. The players must play in the same position (e.g. defender for a defender, striker for a striker etc).
- 'N' for Names: change the name of a player. Type the number of the player you want to rename and press ENTER. Type the name (up to 14 characters) then press ENTER
- 'S' for Save: saves your current game to to be played later. On the 16k/48k/128k/+2/+2A this is saved to tape, on the +3 it is saved to disk. Enter the filename (up to 8 characters) and press ENTER. Later on, simply load the saved file using LOAD "filename", LOAD "" or 'Loader'. You will resume where you left off.
- 'T' for Table: switches to the league table screen where you can see the current standings and use the 'R' key to rename a team (either your own or any of the others)
- 'B' for Buy: once each week you'll have the option to buy a player who is available on the transfer market. They are offered at varying values so sometimes you'll get a bargain and sometimes you'll end up paying over the odds if you're desperate! Make sure you have plenty of money available (top right) before pressing 'B'. The offered player is shown with their name, position, rating and cost (e.g. "I.Lane G (88) £10.3m" is a goalkeeper rated at 88 who would cost you £10.3 million. If you want to buy the player, press 'Y', otherwise press 'N'. The new player will appear in one of your empty slots, and you'll see how much the player is actually worth. If you press 'Y' but don't have enough money, nothing happens. Remember: you only get offered a player once a week, so if you don't buy one, you'll have to wait until the following week.
- 'E' for sEll: you can sell any of your players at the displayed value at any time. Careful though because leaving any of the first 11 slots empty will badly affect your overall team rating. Enter the number of the player you want to sell and press ENTER. You'll see your available money increase at the top.
- 'P' for Play: when you're happy with your team selection, choose this option to play this week's fixture (see below)

-= Playing a match =-
Games are played with each team's rating taken into account (which is why you should always get your overall team rating as high as you can before playing a match). During a match, your team and the opposition team are shown at the top, along with the current score. The 'vidiprinter' appears at the bottom and moves up the screen as the goals go in. The match clock is shown in the green box (it goes red when stoppage time is played after 90 minutes). Goals are reported as they go in, with the minute scored in brackets. Goals scored by your team also include the name of the scorer. After the game, the 'WAIT' message appears while the new league standings are calculated. This can take between 7 and 15 seconds before the new league table is displayed and the next week begins.

-= End of season =-
After 40 weeks (38 games plus 2 weeks' international break), the game comes to an end. Choosing 'Play' increases the week, but no games will be played. Feel free to restart the game (Shift+SPACE then 'RUN') to enjoy another full season!

-= Troubleshooting =-
If the game crashes at all (usually due to the wrong type of number/word being entered), just type GOTO 3 and press ENTER to return to your current game.

APPENDIX A - Suggested leagues

Here are the names and team colours of the most popular leagues in the world. Use the 'R' key when the league table is first displayed to change the name and colour of each team. Use leagues with 20 teams without modifying the game's code. 

Premier League 2023/24 (20 teams)
1  Man City i1 p5
2  Liverpool i7 p2
3  Arsenal i7 p2
4  Man Utd i7 p2
5  Tottenham i1 p7
6  Aston Villa i3 p5
7  Chelsea i7 p1
8  Newcastle i7 p0
9  West Ham i5 p3
10 Bournemouth i2 p0
11 Wolves i0 p6
12 Everton i7 p1
13 Nottm Forest i7 p2
14 Brighton i7 p1
15 Crystal Palace i2 p1
16 Fulham i0 p7
17 Luton Town i1 p7
18 Brentford i7 p2
19 Burnley i5 p3
20 Sheffield Utd i2 p7

Spanish La Liga 2023/24 (20 teams)
1  Real Madrid i0 p7
2  Girona i7 p2
3  Barcelona i1 p2
4  Atl. Madrid i7 p2
5  Atl. Bilbao i7 p2
6  Real Betis i4 p7
7  Real Sociedad i7 p5
8  Las Palmas i4 p6
9  Valencia i0 p7
10 Getafe i7 p1
11 Osasuna i7 p2
12 Alaves i1 p7
13 Villarreal i1 p6
14 Rayo Vallecano i2 p7
15 Sevilla i2 p7
16 Mallorca i7 p2
17 Celta Vigo i7 p5
18 Cadiz i1 p6
19 Granada i2 p7
20 Almeria i7 p2

Italian Serie A 2023/24 (20 teams)
1  Inter Milan i1 p0
2  Juventus i7 p1
3  AC Milan i0 p2
4  Atalanta i0 p1
5  Bologna i2 p0
6  Roma i6 p2
7  Fiorentina i7 p3
8  Lazio i7 p5
9  Napoli i7 p5
10 Torino i7 p2
11 Monza i7 p2
12 Genoa i1 p2
13 Lecce i2 p6
14 Frosinone i1 p7
15 Empoli i7 p1
16 Sassuolo i0 p4
17 Udinese i0 p7
18 Hellas Verona i1 p0
19 Cagliari i2 p1
20 Salernitana i7 p2

Other league sizes are supported but require you to modify two lines of code (even numbers of teams, no more than 20 teams. To modify the code press Shift+SPACE, then edit lines 1 and 7 as follows: in line one, change 'LET tt=20' to the number of teams, and change the end of line 7 from 'OR w>41' to double the number of teams plus 1)

German Bundesliga 2023/24 (18 teams - change line 1 'LET tt=18' and end of line 7 'OR w>37')
1  B. Leverkusen i2 p0
2  Bayern Munich i2 p7
3  VfB Stuttgart i2 p7
4  B. Dortmund i0 p6
5  RB Leipzig i2 p7
6  Eint Frankfurt i2 p0
7  SC Freiburg i7 p2
8  Hoffenheim i7 p1
9  FC Heidenheim i7 p2
10 Werder Bremen i7 p4
11 FC Augsburg i4 p7
12 VfL Wolfsburg i4 p7
13 B. MEngladbach i4 p7
14 VfL Bochum i7 p1
15 FC UnionBerlin i7 p2
16 FC Koln i7 p2
17 Mainz 05 i1 p0
18 Darmstadt 98 i7 p1

Women's Super League 2023/24 (12 teams - change line 1 'LET tt=12' and end of line 7 'OR w>25')
1  Chelsea i7 p1
2  Man City i1 p5
3  Arsenal i7 p2
4  Man United i7 p2
5  Liverpool i7 p2
6  Tottenham i1 p7
7  Leicester City i7 p1
8  Aston Villa i3 p5
9  West Ham i5 p3
10 Everton i7 p1
11 Brighton i7 p1
12 Bristol City i7 p2

APPENDIX B - Lines of code

Line 1 (256 characters): initialise the number of teams, starting week, arrays for teams, players, player positions, injury flag, league positions, team ratings, player ratings, total team points. Clear the screen, define function for random numbers, read in the DATA statement strings. Show the initial team selection screen with default team names, assign team ratings. DATA for player positions and 'next game' string.

Line 2 (236 characters): initialise the squad array, define function for determining the cost/value of a player from their rating. Ask player which team they want to be. Show the 'WAIT' message and call the fixture subroutine in line 10. Generate the default player names (e.g. K.Shaw) along with their player ratings (random but tied to the team's initial rating). Calculate new team rating. DATA for team selection string and league table heading string.

Line 3 (256 characters): randomise the seed. Clear the screen and display the current week's league table. Ask if they want to rename a team, if so ask for which team, what the new name is, as well as the ink and paper colours for that team. Otherwise (if any other key is pressed), clear the screen and start displaying the team selection screen. DATA for rename team string, ZXFM title and the four possible player positions

Line 4 (255 characters): continue displaying the team selection screen, ensuring that an injured player is shown in red and a blank or sold player is not displayed at all. The team rating is recalculated as the team is displayed. Show the menu bar at the bottom of the screen. If it isn't the end of the season, then read in the next opposing team's number and display 'Next game:' with the team name. If the fixture is against yourself, display that it's the international break.

Line 5 (256 characters): take input from the user. If they choose 'N' (names) ask which player to rename. If the player exists (i.e. their rating isn't 0) then ask what name they want them to be called and update the player array. If they choose 'S' (save) ask what to call the saved file, then save it to tape/disk. If they choose 'M' (move) ask which players to swap. It checks that the source player exists before doing the swap. If they choose 'B' (buy a player) and that week's buy flag is ok, then generate the name and position of the player for sale.

Line 6 (253 characters): continues the 'B' (buy) code. Generates the rating and cost of the player for sale, displays the player's details and asks if they want to buy. If they press 'y' for yes (and they've got enough available money), then it takes the money, and looks for a blank spot in the squad and puts them in. The line ends by finishing the main loop and sending them back to either the league table screen or the player selection screen (unless they've typed 'e' or 'p'...)

Line 7 (255 characters): If they choose 'E' (sEll a player) then ask which player to sell. If that player is not blank, then add their value to the available money and set their rating to 0 (which ensures the player no longer appears in the squad). The remaining code on this line, line 8 and line 9 relates to playing a match. Firstly, the number of the week is incremented. The available money is increased with that week's income (a random amount between £0 and £5m). The screen is cleared and the two teams are shown. The vidiprinter is initialised, an array is set up to contain the team's numbers and their score. A loop starts counting for the minutes from 1 to 91 plus a random number of added minutes (up to 99 mins). The score is updated on the screen (green background or red if over 90 mins). If it's the international break or the end of the season, it jumps back to the league table.

Line 8 (250 characters): continues the 'P' (play) code. Inserts a 2 second pause if it's half time. Determines whether a goal has been scored in each minute. The formula used takes into account that team's rating meaning it's more likely for a better team to score. If a team scores, display 'GOAL!' on the vidiprinter along with the minute it was scored in and the team's name. If it's our team that scores then display the player's name (a random player chosen from positions 7 to 11 - some of the midfielders and the two strikers). Update the vidiprinter's line position. Update the array of the team's score. After the match, update the points for both teams (1 point for a draw, 3 points for a win). Display the 'WAIT' message and add one to the counter of games played. DATA for the international break string.

Line 9 (247 characters): continues the 'P' (play) code for after the match. Decides if a player is injured this week (2 in 3 chance) and if so, which player is injured. Uses a bubble sort routine to update the league table with teams sorted by their points total. To speed up the process, a flag is checked on each pass through the table to see if no swaps have happened, in which case the bubble sort finishes early. DATA for the player selection heading.

Line 10 (232 characters): This line is called from line 2 as part of initialisation. The number of fixtures played is set to zero. DATA for the 'WAIT' string, the menu bar, and the random 4-letter surnames for players. The fixtures are held in a string. Firstly the string is filled with the lowercase letters from a to t interspersed with the letters from t to a. Letters are swapped randomly in a loop to ensure the fixtures are mixed up. It returns to line 2 to continue initialisation.

APPENDIX C - Variables

Numbers
a - average/total of player ratings
c, d - temporary variables used during bubble sort
f - number of fixtures played (similar to 'w' but doesn't include international breaks)
g - next game's opponent (team number)
i - injury flag. 0 means no injury this week, number is the player number who is injured
j - ink of renamed team
l - current line for the vidiprinter
m, n, o, q - used in FOR loops
m - used during match for minutes
p - paper of renamed team
r - rename team number
s - flag used during bubble sort to check it is finished sorting
t - the number of the team you are playing as 
tt - the total number of teams (20 by default)
u - temporary store of the buy flag from q(20)
w - current week
y, z - temporary variables 

Strings
a$ - name of game and the week indicator ('ZXFM W')
c$ - selection of 4-letter surnames used for players ('ShawCookDunnLaneReedWardHallHuntCarrBeck')
d$ - choosing a team string ('Team (1-')
e$ - league table heading ('Reg Pld Pts')
f$ - holds all the fixtures (see line 10)
g$ - the position names for goalkeeper, defender, midfielder and striker ('GDMS')
i$ - the flashing wait message ('WAIT')
l$ - the player table heading ('Rtg Pos Money No')
m$ - menu bar text ('MoveNamesSaveTable Buy sEll Play')
n$ - menu choice entered by the player
s$ - save game name
u$ - transfer market player name
v$ - transfer market player position
w$ - temporary team name and swapped team during fixture generation
 
Arrays
b(2,2) - used during match to store the team's numbers and scores
l(tt) - league positions (holds the team number in each position)
q(20) - squad positions up to q(18) - q(19) holds the available money and q(20) is the 'buy' flag to see whether you can buy a player this week
r(tt) - team ratings for each team
s(18) - player ratings
t(tt) - points totals for each team
o$(18) - player positions
p$(18,14) - player names (up to 14 characters long)
t$(tt,18) - team names (first 4 characters used to set the ink and paper attributes, followed by up to 14 characters for the name)

Functions
c(y) - convert player rating to a monetary value
r(y) - generate a random integer

