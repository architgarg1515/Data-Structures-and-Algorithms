Project 4: Tic Tac Toe

Objectives

    To implement a hash table ADT from scratch
    To design a hash function for game configurations
    To create and extend ADTs to serve a particular purpose
    To make sound design choices
    Optionally, to create an interactive GUI

Overview

Several artificial intelligence (AI) approaches for computer game playing involving creating dictionaries of possible game piece configurations and the moves which worked best for each configuration. Because the number of possible configurations is large (and some configurations are unlikely), it is not practical to create one large table of all the possible configurations. Instead, a common technique is to use a hash table to store game configurations which have been previously seen along with their likely outcomes.

In this project, you will implement a simple tic-tac-toe game, using a hash table to store game configurations to play smarter. Your base program will be automatic play between two computer-controlled players -- a "smart" player that learns and a "dumb" player that chooses moves randomly.
Project Specification
Your project will create the basic infrastructure for a tic-tac-toe game, including two computer players. One computer player is the "dumb" player that always chooses its moves randomly. The dumb player always goes first and is the 'X' player. The other computer player is the "smart" player that learns from experience, always goes second and plays 'O'.

You will use a dictionary of game configurations to store results of previous games so that the smart player can make informed decisions about its next move. If there is incomplete information about possibilities starting from the current configuration, the smart player makes a random choice for its next move and records the results, so that it can make a smarter choice next time.

Each hash table entry should include a game configuration and history of success when continuing from this configuration. To choose a move starting from the current configuration, construct each possible next configuration by considering all legal next moves, retrieve the corresponding configurations, and and check their win/loss histories. When the game ends and you know which player won, update the hash table with the new win/loss histories.

You will need to design a hash function which takes a game board configuration as input and converts it to an index into the hash table. A game configuration has three possible states (x, o, empty) for each board position. The representation of a game configuration is up to you. Your hash function should scatter game configurations across the hash table as evenly as possible.

Your program accepts four possible command line arguments: a history flag (-h), a save flag (-s), a display flag (-d), and a number of games to play flag (-1, -2, etc).

    You must implement the history flag. When the history flag is present in the command line, the program should print out intermediate reports.

    Intermediate reports show the board configuartion after each move. and the accumulated win/loss records of the players. Other information you may find useful may be included in intermediate reports.
    You must implement the number of games flag. If the number of games flag is present in the command line your program should play the specified number of games and then exit. Otherwise your program plays just one game.
    The configuration save flag is an extra credit option.
    The display flag is an extra credit option.

A final summary of the series of games and operations of the the tic-tac-toe program must be printed when your program terminates. The summary must contain the following information:

    statistics about the hash table: number of slots, number of entries, load factor, and number of collisions.
    statistics about wins and losses of the players
    advice about the best initial move for the smart player and outcomes resulting from that move (backed up with statistics from games played). The initial move suggestion must be based on statistics aquired during the game.

Example final summary output. This sample is provided to illustrate all required data. The data does not necessarily reflect expected results. Your format may vary provided it is readable and contains all required data.

run:
     [java] FINAL REPORT: 
     [java] 
     [java] The number of slots is: 267
     [java] The number of entries is: 218
     [java] The % full is: 81.64
     [java] The number of collisions is: 1087
     [java] Smart player has won 342 times which is 34 percent
     [java] Random has won 567 times which is 56 percent
     [java] My favorite first move is: 
     [java] ...
     [java] .OX
     [java] ...
     [java] Won 48.0 out of 71.0 which is 67.60%

Project Notes, Hints, and Requirements

    (R) -- Your project must adhere to basic good design principles, including (but not limited to) appropriate abstraction and encapsulation, logical control flow, reasonably efficient use of memory, and basic computational efficiency. If you feel it advisable to violate one of these principles (or any others), be sure to explain your reasons. We may not necessarily accept your reasons, but will consider them. You may, of course, get feedback on your design decisions before the project is due (ideally, WELL before the project is due). The safest source of such feedback is your instructor, since s/he is the one who ultimately decides how your project will be graded.
    (R) -- You must implement your own HashTable class. 
    (R) -- We all know that the center square is the most important and we all know a winning move when we see one near the end of the game, however, DO NOT build this kind of intelligence into the smart player. The smart player should use only the board configuration dictionary to decide which move to make next.
    (N) -- an example intermediate report which must be printed if the history flag is present on the command line is available here
    (N) -- A tie is not a loss and is not a win. You should reflect this in your intermediate game results.
    (R) --Your smart player must exhibit an acceptable rate of learning. The rate at which your smart player wins is incorporated into the grade calculation. To achieve maximum points for the "Learning Curve" portion of your grade, your smart player must achieve an 80% win rate.
    (H) -- use the CVS Utilities that have been provided to insure that there are no CVS or ant problems with your submittal.

Extra Credit
There are several interesting ways to extend your base project. To indicate that you implemented any of these extra credit items, submit a file named README. This will alert the TA to look for that additional functionality when grading your project.

    Add a GUI display to your program. Your GUI should display the game board and piece positions. In GUI mode, moves of one player should be controllable interactively. Include instructions so that the TA knows how to control the interactive player. Worth five points.
    In the base version, the automated player will not be "smart" until enough games have been played to sufficiently fill the game dictionary with good recommendations. Implement the capability to save and restore game configurations between executions of the program, in order to accumulate more playing experience. Your configuration save file must be named configs.txt. The file may not initially exist, in which case it should be created. You should design a file format for your configuration save file and explain why this design is appropriate. Worth five points.
    Analyze the rate at which the program learns (through building a good configuration dictionary). Play an automatic player that uses a dictionary against one that makes purely random decisions. Plot the performance of these over many games. How many games are required until the dictionary is full enough to make a noticeable difference on the outcome? Write a 1-2 page paper discussing your analysis. Worth five points.
    In tic-tac-toe, many game positions are the same for all practical purposes, due to the symmetry of the board. Specifically, some moves are reflected or rotated versions of other moves. For instance, an initial move in any of the corners leads to the same options, while a move into the center space is qualitatively different. Most real game dictionaries take advantage of symmetry to reduce the number of entries which must be stored in the table. Write a second hash function that uses symmetry to store and retrieve game configurations. Write a 1-2 page report describing your method and the resulting effect on number of table entries for sequences of games. Be sure to include a theoretical analysis of the number of unique cases in both the base and symmetric versions. Your report should be in pdf format and named 'your_logname.pdf' (insert your logname for your_logname). Worth ten points. 

