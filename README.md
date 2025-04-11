Introduction
Welcome to the unbeatable tic-tac-toe project! This document is to give you the step-by-step
process of how to develop this game in Python! Throughout this project, we wi

learn about

and use the minimax algorithm to make our opponent virtua

y unbeatable. This lab is meant to

be approachable, but keep in mind that the algorithms we'

be exploring today are a li
le more

complex than stu

you may have seen before, so take your time and ask lots of questions!

We will
not be programming this entire game from scratch, because there's a lot of boring stu
involved like drawing the UI and stu

on the screen that isn't important to us. Instead, you wi
be focusing on implementing the game logic, using problem solving to fi gure out how we can
implement this game!
Learning Objectives
● User Input: Whenever the user clicks, we want to place an X on the board if they clicked
in a valid location. We also want to add keyboard inputs that a

ow us to close the game

or play another round with a keypress!
● Minimax Algorithm: In this lab, you wi

learn about a very common AI algorithm ca
ed
the minimax algorithm! This algorithm is useful for competitive puzzles such as

tic-tac-toe and chess because it simulates the possible game states and chooses the
best move based on what is most likely to make our opponent win, while considering the
player wi

do everything to make our opponent lose. It's not super complex on this scale

of a project, so it makes a fantastic introduction to the algorithm!

Project Setup
Here is a quick list of links to the resources you may need for the project. Keep in mind that
having the PyCharm editor wi

keep you from needing to insta

pip and Pygame manua
y!
There are instructions below that elaborate on why we use these tools and the steps needed
to insta
them.
Python Insta
er: Link
PyCharm IDE: Link
pip Instructions: Link
Pygame Instructions: Link
Here is the repository for the project, which has the template project for this lab. You have to
have these fi les or you wi

not be able to fo

ow along!

Project Repository: Link
Why Python? What is Pygame?
In hopes to make this workshop accessible to as many students as possible, Python has been
chosen for this workshop due to its low barrier to entry. We encourage students to have
introductory programming knowledge for this workshop, but we also don't want you struggling
with unfamiliar syntax while you're trying to fo

ow along! Also, most computers, including lab
computers, have some sort of Python IDE available. It is encouraged that you use your personal
devices so you have complete freedom to insta

and use any so

ware you want, but these

choices are in an a

empt to make the project as approachable as possible.

Pygame is a co

ection of cross-platform Python modules designed for creating video games! It
includes many useful computer graphics and sound libraries to make game development easier
in Python and is a very popular tool. Since Python is one of the most popular languages when it
comes to implementing AI algorithms, we wi

be using it with Pygame to make our lives a li
le

bit easier when making our game!
Insta
ing Python
Many devices o

en come with Python insta

ed, but just in case you can read how to insta

Python here!

1. First, start by downloading the Python insta

er for your device here. You can click the
download link to download the latest version of Python, and make sure you're
downloading the correct insta

er for your operating system!

2. Go to your Downloads folder (or wherever you downloaded the Python insta

er to) and
run it. Make sure to click the "Add Python to PATH" checkbox if it's shown in your
insta
er!
Insta
ing PyCharm
The development environment that wi

be used during the lab is PyCharm! Most universities

and co
eges o
er PyCharm to students for free using an educational license. However, if you
don't have access to the paid version through your institution, PyCharm Community Edition is
perfectly acceptable and works rea
y we
!

Using PyCharm wi

make the process of "insta

ing" the needed libraries much easier (meaning
you can do it from within the editor and don't have to use terminal commands), so it is the
suggested IDE for this project! Other IDEs may have the same feature, but Pycharm is the one
I'm aware of, persona
y.

You can download both the paid version and Community Edition of Pycharm here!
If you don't want to use PyCharm, the insta

ation process of the libraries needed are specifi ed

below.
Insta
ing pip
Genera
y, pip is included with any Python insta

ation from the o

cial site, so you most likely

won't have to insta

it. However, if you realize you don't have pip insta

ed, you can read about

how to insta
it here!

You can check if you have pip with the fo

owing commands:

# Mac / Linux
python3 -m pip --version
# Windows
py -m pip --version

Insta
ing Pygame
If you use PyCharm you can a

ow the IDE to insta

Pygame automatica

y for you on your

project. Otherwise, you can read about insta

ing Pygame here. First you should try the general

insta
ation command regardless of OS:
python3 -m pip install -U pygame --user
Then you can verify the insta

ation with:
python3 -m pygame.examples.aliens
Alternate Commands
If the previous command didn't work, you can try this alternate command to use pip to insta
Pygame on Windows:
py -m pip install -U pygame --user
Then you can verify the insta

ation with:
py -m pygame.examples.aliens
There isn't an alternate Mac command, but I suggest referring to the link above for more
details on how to insta

Pygame on your device. If you're on Linux, please refer to the link

above for how to insta

Pygame on your specifi c Linux distribution.

Ge
ing the Project Files
The fi les needed for this project are included in the project repository, which can be found
here. The steps to get and set up the fi les are the fo
owing.

1. Open the repository link.
2. Click the green bu

on towards the top-right of the screen that's labeled Code.
3. Select the option from the popup menu that's labeled Download ZIP (link here wi
directly download the ZIP folder as we
).

4. Now that you have the fi les in your Downloads folder, and extract them.
○ If you're on Windows, right click the folder and select Extract A
.

○ If you're on Max, double click on the folder and it wi

extract the fi les

automatica
y.

5. Open the extracted folder, you wi

see two items in the folder: a folder ca

ed src and a

fi le ca
ed README.md. The only thing we care about here is the src folder.
6. Open up PyCharm, create a new project named something along the lines of
MinimaxTicTacToe or UnbeatableTicTacToe. Name it whatever you like as long as you
wi
recognize it in the future!
7. Right click the root folder (it wi

have the same name as your project), and select Open

In and then select Explorer (Windows) / Finder (Mac). This wi

open the project folder

in your fi le browser!
8. Copy the src folder into the root folder of your project,
then go back to PyCharm. It should now appear a
er a

moment in your project's fi le system!
○ Note: If your src folder does not appear in the
project, you may need to reset the content root.
○ To do this go to File > Se

ings > Project: [Project
Name] > Project Structure, click + Add Content
Root, and select the project folder.
○ Double check with your workshop instructor
before you try changing the content root!
Your fi le system should look like the image on the right:
9. Make sure to insta

Pygame on the project if it isn't done already. To check, open

src/tictactoe.py. If Pygame needs to be insta

ed, line 1 wi

have a red underline. Hover

over the line of code and select Insta

package pygame. A

er a few moments, the

underline should disappear!
10. Verify your project compiles by selecting the tictactoe.py fi le and run it using the play
bu
on. Make sure your run confi guration is set to Current File!

Once your project is up and running, the
screen should look like the screenshot
shown on the le
. You wi
not be able to

mark ce
s or do anything except close the
program with the Escape key, which is
exactly how it should be!
If your project does not compile for any
reason, please te

your instructor
immediately so they can help you debug the
problem! It's always be

er to fi x it right

away rather than a

er we start working on

the project!

What is Tic-Tac-Toe?
Although it is probably unlikely that you have never played tic-tac-toe before, we review the
mechanics of the game because it wi

be important to us if we want to design our game!

Tic-tac-toe is traditiona

y a pen-and -pencil game that involves two players who take turns

marking the ce

s in a three-by-three grid with either X or O. The player who succeeds in
placing three of their markings in a horizontal, vertical, or diagonal row fi rst is the winner!
Tic-tac-toe is considered to be a solved game, which means its outcome can be predicted from
any state of the game assuming that both players play perfectly each move. This means that in
the situation where both players pick the best moves the game wi

always result in a draw!
This is the reason when we apply the minimax algorithm to the opponent, which wi

choose the
next best move based on the current state of the game, it becomes unbeatable! I have litera
y
never been able to best this tic-tac-toe opponent without adding handicaps to its algorithm.
In our version of tic-tac-toe, the player is the X marking, and the opponent is the O. Genera
y,
X gets the fi rst turn, so our player always goes fi rst. However, this project could easily be
modifi ed to randomly select or alternate the markings of the player and opponent! If this were
an actual game, it would probably make the most sense to a

ow the player to select how they

want the markings to be decided in the se
ings.
The Minimax Algorithm
So, what exactly is this minimax algorithm we've been talking about, and how is it related to AI?
The minimax algorithm is a set of decision rules used in artifi cial inte

igence and game theory,

which is intended to minimize loss and maximize gains. It is created specifi ca

y for competitive

scenarios, usua

y in the form of agents who take alternating turns, in which the assumption is
made that the agents are working towards opposite goals to make predictions about which
future states wi

be reached as the game progresses.
In the scenario of tic-tac-toe, it is assumed that the player wi
a
empt to minimize whatever
the opponent is trying to maximize (hence, "minimax" as the name), which is the opponent
winning in our case. Therefore, the opponent should choose the moves which results in the
player capable of doing the least damage. Idea

y, the opponent wi

be able to investigate

every possible outcome from the game's current state, as we

as the path taken to get to that

terminal state. It wi

then assign each state with a score, which in tic-tac-toe, there are only

three possible values: win, lose, or draw. These scores are genera

y assigned some numerical

value, such as 1, -1, and 0.
With the sma

state complexity of tic-tac-toe, we are able to use minimax in its ideal case,

where it can fu

y explore each path. This would not be realistic for a more complex game, such
as chess, where it would take too long to explore every outcome in a reasonable amount of

time without heuristics (algorithmic compromises when calculating the fu

result would be too
costly). Tic-tac-toe is also a common example for the minimax algorithm because its rules and
permutations are easy to understand and trace for the majority of students. Conveniently, the
minimax algorithm also presents a perfect situation to use recursion instead of iteration, which
can be an extremely useful algorithmic design tool that many learning programmers don't take
advantage of fu
y!

Tic-Tac-Toe Example
Let's say our game state is currently the fo

owing board and it's the opponent's turn:

The opponent can make three possible moves (r, c): (1, 1), (2, 1), or (2, 1). Which gives the
opponent the best outcome?

In this case, the move to (1, 1)! This is a very simple example of how the minimax algorithm
makes decisions. The tree is expanded a

the way down until a

terminal states are reached,

this expansion of possibilities is done with a recursive method that ca

s itself again if the

current board doesn't result in a game over yet.

Let's look at the complete co

ection of possible terminal states for this current game:

But this is only part of the minimax algorithm we described, it also needs to determine the
choices that the player wi

most likely take and then minimize the potential loss. This a
ows

the opponent to have an idea what the player wi

most likely do to try and win. Each terminal
state is assigned a value. In tic-tac-toe we use a -1 for a loss, 0 for a draw (we don't see any in
this case), and +1 for a win. You could have these values be -10, 0, and +10 if you wanted to
account for the depth when calculating the score, but we won't be doing that in our current
project.
Then, starting from the bo

om of the tree, the opponent works its way up, choosing maximum
scores for its moves, and minimum scores for the player's moves. This results in an alternating
pa
ern of maximum and minimum values for each turn. Now each of the states, even the
non-terminal ones, wi

have their own scores which are equal to the score of the most likely

outcome of the game if that move is made! It sounds a li

le bit crazy, but it actua
y works

rea
y we
and is a perfect algorithm for adversarial, turn-based puzzle game's AI opponents

just like ours!

Let's see an example for one of the trees:

Although the opponent wi

choose the moves that are most likely to benefi t it, the player wi

not. We assume the player wi

choose to put its X in (1, 1) if the center ce

is open, meaning the

opponent loses the game, so we would probably not want to make this move.

Here is an example of the completed tree for our original game state:

This is how the minimax algorithm actua

y determines that placing the O in (1, 1)! It's not
common sense like we humans innately have, but rather a complex set of steps that determine
the most likely outcome of every single move. The algorithm must go a

the way down a tree

before it can start assigning scores from the bo

om up, so doing every combination is rea
y
only a feasible solution for simple games like ours. With more complex games, we would
undoubtedly have to use some sort of heuristic or pruning to make the algorithm more e
cient.

Let's start coding already!
So, let's get started with the lab itself! Obviously, there's going to be a lot to do aside from the
minimax algorithm itself, but nothing that's too hard - I've done those tedious tasks that don't
teach anything for you! However, we do need to know how our code works in order to interact
with it, so let's take a look at a few things.
Variables
There are few important variables in our project that we wi

be using quite a lot to implement

our algorithm. Thankfu

y they're quite simple, but we have to know exactly how they work if we

want to use them later!
● board (List): A 3x3 two-dimensional list that holds the values of either 'X', 'O', or
None. For instance, our board from the earlier examples would be:
[['X', 'X', 'O' ],
['O', None, None],
['O', None, 'X' ]]
Is initia
y populated with the None value.

● choice (Tuple): A pair of int values (row, column) representing the choice the
opponent wi

be making for its next turn. Initia

y is equal to None.

Before we get into designing the minimax part of this project, we're going to do a few warm up
tasks that involve basic functions of the game, such as rese

ing the game, drawing the game

board by placing the X and O marks appropriately, and a

owing the player to place X marks

by clicking on empty ce

s on the board!

Methods
There are also quite a few methods that help us out as we

! You don't need to know exactly

how a
of these work, but you are encouraged to read through and understand the code if you
are curious.
● draw_x(row, column): A helper method to the draw_game method that draws the X
image at the given ce

's position.

● draw_o(row, column): A helper method to the draw_game method that draws the O
image at the given ce

's position.
● draw(): A method that is ca

ed every frame of the game, ca
ing a
other needed draw

functions such as draw_grid and draw_game.
● draw_grid(): A helper method to the draw method that draws the grid lines of the
tic-tac-toe board onto the screen.

● The main loop at the end of the game ca

s the draw method and takes in user input

until the player either closes the window or presses the escape key!
Task 1: Implement the reset method.
The fi rst thing we want to be able to do is reset the board by pressing the R key. It's a simple
thing, but it'

be a lot easier to test our game if we don't have to stop and re-run it every single

time we want to play another round of tic-tac-toe.
A
we have to do is reset the board and choice variables to their initial states. However, make
sure to declare them as global variables inside the method or you'

accidenta

y create local

variables instead of changing the ones we declared at the top of our program!

Task 2: Complete the draw_game method.
The next task is also very simple! We need to decide if we need to draw an X marking, an O
marking, or nothing at a

for each ce

of the board. To do so, complete the fo

owing tasks:

1. Loop through each row and column in the board.
2. If the value in the ce

is an X, ca

the draw_x method for this ce

. If the value in the ce

is an O, ca

the draw_o method instead.

3. If the value is neither an X or an O, don't draw anything in this ce
.

Task 3: Complete the user_click method.

Task 3 is a li

le more work than the previous tasks, but much of the rea

y weird stu
is wri
en

for you. You'

only be writing the things related to the game logic, not determining the exact

position of the click or what ce

it was within! The method has the fo

owing tasks:
1. If the game is already over, then we shouldn't process this click as we don't want the
player placing additional Xs on the board. We wi

declare the is_game_over method

properly in Task 4, so don't worry!
2. Once the ce

the click was within (if any) is determined, check if the ce

is empty or not.

3. If the ce

is empty, set that ce

of the board to an X. The draw_game method wi
start

drawing it from then on.
4. Check if the game is over again a

er the X is placed. If it isn't over, then we wi
ca
the

computer_turn method to te

the opponent to make its choice. As previously, we wi

declare the computer_turn method properly in a future task!
Once you fi nish this task you should now be able to see the board and add Xs to it by clicking!

Task 4: Implement game logic helper methods.
In order to make our game work, we need a few helper methods to assist our other, more
complex algorithms. Of course, the code to these helper methods could be included directly,
but it wi
quickly make our code messy and repetitive, which is why we declare them
separately!
We need a method to check if the game is over to decide if we keep playing and to determine if
a given board has reached a terminal state, a method to score terminal states for the minimax
algorithm, and lastly, a method to duplicate the board whenever we are exploring di
erent

possible moves so we don't accidenta

y modify the board we are currently playing with!

Task 4.1: Implement the is_game_over method.
This method checks whether a current board is a game over or not. The game is over either
with X or O wins, or there are no more moves that can be played! This method takes one
parameter that represents the board it is checking and returns the value of either 'X' or 'O' if
someone has won, 'T' if it is a tie (a
ce
s are fi
ed but there's no winner), or None if the game

is not over yet. The method has the fo

owing steps:

1. Check horizonta

y (rows) to see if anyone has won. If there's a winner, return their

marking.
2. Check vertica

y (columns) to see if anyone has won. If there's a winner, return their

marking.
3. Check diagona

y to see if anyone has won. This one wi
be a li
le more tricky! If there's

a winner, return their marking.
4. If there's no winner but a

of the ce

s have been fi

ed, return 'T' to represent a tie.
5. Otherwise, if there was no winner or tie, return None which represents that the game is
not over yet.
Task 4.2: Implement the score method.
The score method is quite simple to write. It simply checks who has won and returns the
appropriate score as we described when discussing the minimax algorithm! It takes one
parameter that represents the board being scored and returns an integer value representing
the score of that board. It has the fo

owing steps:
1. Get the winner of the board (if there is one).
2. If the winner is the opponent (O) then return a score of +1, if the winner is the player
(X) then return a score of -1.
3. If it's a tie, return a score of 0 instead.

Task 4.3: Implement the get_new_board method.
This helper method is used by the minimax method in order to create a new board with a given
move added when it's exploring a

of the possible moves, so we don't accidenta

y change the
current state of the board. It takes three parameters: the board that is being copied, the
position of the move that's being added, and the symbol of the marking (either X or O). It
makes the new board with a

the original board's values copied over, adds the move to the new

board, and returns it. The method completes the fo

owing tasks:
1. Create a new empty board that has no Xs or Os on it.
2. For each value in the original board, copy it to the new board.
3. Add the move to the new board at the designated move position with the given symbol.
4. Return the new board.

Task 5: Implement the minimax algorithm!
Now, we have fi na
y go
en to the point where we can implement our minimax algorithm,
woohoo! We have two main steps: create the minimax method and then use it in the
computer_turn method. The minimax method wi

handle exploring a

permutations of the

current game state. Once we've checked a

of the possible moves and assigned them their

respective scores, we wi

choose our fi nal choice for the opponent's move, then the

computer_turn method wi

take that move and wait for the player to take their turn before

running again.
Task 5.1: Implement the minimax method.
Now it’s time to bring everything together into the core of our AI opponent! The minimax
method is responsible for recursively exploring a

possible future moves from the current
game state and determining the best possible move for the opponent. This is the “thinking” part
of our AI, and it wi

be used to calculate the optimal play. The method needs to check if the
board is in a terminal state (win, loss, or tie). If so, it simply returns the score of that board
using the score method. Otherwise, it gathers a

the empty ce

s and recursively simulates
placing moves in each of them, fl ipping between maximizing and minimizing the score
depending on whose turn it is. The best move found is saved as the global choice variable,
which is used later in the game.
This task wi

put into practice everything we’ve done so far - including recursion, game state
evaluation, and helper methods - to complete the minimax decision-making process.
1. Declare any needed variables as global. What variables wi

you be changing from

within this method?
2. If the game is over for this board, return its score. Otherwise, continue.

3. Gather a

empty ce

s of the current board, which are the potential moves that could be

made.
4. If maximizing the score, set the current best value to the lowest possible value for
score. If minimizing the score, set it to the highest possible value for score.
5. For each possible move, generate the new board with the move and ca

the minimax

method recursively. If the value returned is be

er than the current best value, replace it

(if minimizing you should also update the current best move),
6. A
er you have fi nished looping through a

the moves, set the choice to the current best

move and return the current best score.
Task 5.2: Implement the computer_turn method.
Once we’ve implemented the minimax algorithm, we can use it to a

ow our opponent to make

its move! The computer_turn method is fairly straightforward: it simply ca

s the minimax
method, which updates the global choice variable with the best possible move for the current
board state.
If the choice is a valid ce

(not None), then we place an 'O' in that ce

on the board to

represent the opponent's move. This method is usua

y triggered a

er the player has made
their move and the game is not over, giving the opponent the opportunity to calculate its next
optimal play using the minimax algorithm.
This is the fi nal step that connects our AI’s decision-making to the actual gameplay!
1. Ca
the minimax method, which updates the choice variable with the best move.
2. If choice is valid, update the board at that position with the O marking.
