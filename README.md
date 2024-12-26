java cProject 2: Tank War
Due: Aug 11th (Sunday), 2024, 23:59
Language: C++
Note: C++ is compatible with C codes, i.e. you can write C codes and view
it as C++ code. However, a bonus will be given to those who use Object-Oriented
Programming (OOP) in their C++ code.
This is a group project. You may find your teammate on Canvas - People. Start
early - it’s strongly recommended that you do not leave this project to the last
minute. No late submissions are allowed!
This project is designed to hone your programming skills in C and C++. You
and your partner will implement a simplified Tank War game. You may find the
main idea of this project is a bit similar to demo project 2, Reversi. However,
instead of implementing the given functions, we will provide you maximum degrees
of freedom this time. No starter tiles, no skeleton, you are free to design your
own program structure and write everything you like.
Contents
Project 2: Tank War ......................................................... 1
1 Introduction .............................................................. 1
2 Rules ..................................................................... 1
2.1 Movement ................................................................ 1
2.2 Bullet .................................................................. 1
2.3 Life Point .............................................................. 2
2.4 Map ..................................................................... 2
2.5 Winning and Losing ...................................................... 2
3 Tasks (TO-DO List) ........................................................ 4
3.1 Features (75%) .......................................................... 4
3.1.1 Command-line Options (15%) ............................................ 4
3.1.2 PVP Mode (25%) ........................................................ 4
3.1.3 PVE Mode (15%) ........................................................ 4
3.1.4 DEMO Mode (10%) ....................................................... 4
3.1.5 Instruction Prompts and messages (10%) ................................ 4
3.2 Code Quality (10%) ...................................................... 4
3.3 README Documentation (10%) .............................................. 4
3.4 Peer Evaluation (5%) .................................................... 5
3.5 Bonus ................................................................... 5
4 Program Structure ......................................................... 5
5 Sample I/O (Minimal Example) .............................................. 5
5.1 Sample command-line options: ............................................ 5
5.2 Sample Input from stdin: ................................................. 5
5.3 Corresponding Output in stdout ........................................... 6
5.4 Sample Output of the Map ................................................ 6
6 Submission ................................................................ 7
1 Introduction
Tank War is a classic computer game. Each player controls a tank in this game,
competing to become the last survivor. This time, you are going to implement a
simplified two-player Tank War and write an AI to support Player Versus Environment
 (PVE) and DEMO modes.
2 Rules
2.1 Movement
1. Two players battle in a spare map.
2. Each player controls a tank.
3. The tank moves 1 meter/turn.
4. Each turn, the tank can choose to move left, right or forward.
2.2 Bullet1. The tank shoots a bullet every three turns (starting from the first turn), and
the bullet will be generated 2 meter ahead of the tank’s position. (The bullet
has the same direction as the tank, and it is generated after the tank moves
in its turn, otherwise the tank will be shot by itself)
2. Bullet moves straightly at the speed of 2 meter/turn.
2.3 Life Point
1. Tank has p life points. (Determined by the user, default is 5)
2. Once a tank is hit by a bullet, 2 life points will be deducted.
3. To make your life easier, just assume that the bullet moves after the tank
moves since this will avoid geometry calculations. Hint: each turn there are
three possible cases where the bullet may hit a tank in your calculation.
4. Once a bullet hits a tank, it will not go further but explode.
2.4 Map
1. Initially, the the size of the map is 20*20. (A tank can go outside the map)
2. The map shrinks by block to the center every 16 turns (the first shrink occurs
in the 16th turn), namely the map size will
be 20*20 -> 18*18 -> 16*16 …
2. As long as a tank is outside of the map, one life point will be deducted
each turn.
2.5 Winning and Losing
1. The tank whose life points are first deducted to 0 will lose.
2. If the life points of two tanks are deducted to 0 in the same turn, they have
a draw competition.
3. When two tanks crash, the tank with high life points wins.
4. To make your life easier, each turn the calculation takes place after both two
tanks move.
Here’s a flow chart of the above rules:One thing that needs to be clarified is that after a bullet is spawned, it will
move two meters in this turn. So in the flow chart above, the “Move a Bullet”
part includes the bullet that is just generated this turn.3 Tasks (TO-DO List)
Your final product is a Tank War game that accepts command-line options, has
a command-line interface and supports PVP (Player vs. Player), PVE (Player vs.
Environment/AI) and DEMO (AI vs. AI) modes, and can run on every computer. In
this part, we provide a general guideline on project goals, sample I/O format and
project structure.
Just in case you get confused by the following project description and don’t
know what features will ultimately need to be implemented, here’s a brief to-do
list (and the score for each):
3.1 Features (75%)
3.1.1 Command-line Options 代 写program、C++
代做程序编程语言(15%)
Your program should accept the following command-line options:
• -h and --help: Print a help message and exit.
• --log-file : Log the game process to a file. (The default is tankwar.log) (Hint:
You may use -l as a short option, though it’s not required)
• -m  and --mode=: Specify the game mode. The mode can be PVP, PVE or DEMO.
The default mode is PVP.
• -p  and --initial-life=p: Specify the initial life points of the tanks. The
default value is 5.
Note that both abbreviated and long options must be supported, i.e. help should
be displayed when either of the -h or --help command-line options are provided.
Hint: Check getopt.h.
$ ./tankwar --help
Usage: ./tankwar [options](optional)
Options:
 -h | --help Print this help message and exit.
 --log-file  Log the game process to a file. (Default: tankwar.log)
 -m  | --mode= Specify the game mode (PVP/PVE/DEMO). (Default: PVP)
 -p  | --initial-life= Specify the initial life points of the tanks. (Default: 5)
3.1.2 PVP Mode (25%)
• Correct Implementation of the Game Rules: 20%
• Clearly output the map after each turn: 5%
3.1.3 PVE Mode (15%)
• AI can work properly: 5%
• PVE mode functions correctly: 10%
3.1.4 DEMO Mode (10%)
• DEMO mode functions correctly: 10%
3.1.5 Instruction Prompts and messages (10%)
• Print the instruction prompts and messages in the game, e.g. “You have chosen
the PVE mode”, “Player 1′s turn”, “Please input the initial position of tank
A”, etc. (5%)
• Reasonable Command-Line Interface and I/O format (5%)
3.2 Code Quality (10%)
As mentioned in the labs, your code should be well-structured, commented and not
too long, with meaningful variable names and proper indention.Moreover, take care
of possible memory leaks and other possible issues mentioned in the lecture.
3.3 README Documentation (10%)
Search online what README is. Write a README for your project. The README should
be well-structured and informative. It should include the following sections:• We provide some sample questions to help you better construct your README. You
do not need to follow these questions strictly, but generally, you should write
your README around these questions.
• (Important) How to compile and run your program? Did you use the Layered Architecture
 Pattern? If yes, briefly describe the components of each layer. If
not, explain your pattern;
• Did you use the Object-Oriented Paradigm? If yes, briefly describe the classes
you defined and their meanings. If not, state your paradigm;
• Your program’s I/O format including the log file;
• (Optional) Some typical issues and bugs you encountered in the development, and
your solutions;
• (Optional) Any other information you think is important, including bonus.
3.4 Peer Evaluation (5%)
Completing the evaluation will give you 5%. Official evaluation forms are to be
announced, so pay attention to Canvas Announcements. Note that your peer evaluation
 result and the git activity will be taken into account when grading.
3.5 Bonus
• Use Object-Oriented Programming (OOP) in your C++ code. (up to 5%)
• For other features that you think can be counted as bonus, please discuss with
the Teaching Team before implementing them.
4 Program Structure
One of the fundamental design patterns when developing an object-oriented project
is Layered Architecture Pattern. This pattern partitions all of an application’s
classes and interfaces (future and current) into layers. It brings much flexibility
 while also saving much rewriting when adjusting the code and allowing
faster debugging in case of a problem. The idea is to organize the code in terms
of layers and prevent any function for a lower layer from calling functions from
a higher layer. Functions from a higher layer can use functions in the same layer
or a layer below.
For this project, design your own layers. Here’s a link that may help you:
Layered Architecture Pattern
5 Sample I/O (Minimal Example)
This part gives a sample I/O of project 2. Please note that this is just a minimal
I/O example. As a user-friendly program, your I/O format should be more decorated
and detailed. For example, you may have some kind instructions and print the
current game board after each turn, just like what you did / will do in demo
project 2.
5.1 Sample command-line options:
./tankwar -m PVP --initial-life=5
5.2 Sample Input from stdin:0 0 19 19 2 0

In the command line options, --mode=PVP indicates that you start the PVP mode,
namely, both tanks’ initial positions and following actions are taken from user
input. --initial-life=5 indicates that the initial life point of each tank is 5.
In the first line of input, 0 0 and 19 19 are the initial positions of tank A
and tank B respectively, 2 (Right) is the initial direction of tank A, and 0 (Left)
is the initial direction of tank B. Here the directions and actions are defined
as below (feel free to change this definition in your program),
enum Direction {
 D_Left, D_Up, D_Right, D_Down
};
enum Move {
 M_Forward, M_Left, M_Right
};
6 Submission
Before submitting the project on Gitea (will be covered in lab 10), ensure the
project compiles on JOJ. The JOJ compilation test will be opened soon.
• A project submission which directly crashes when run will not be graded;
• We provide you with a CMakeLists.txt, but it’s recommended to write your own
Makefile/CMakeLists.txt;
• If the submission uses external libraries, e.g. GTK or sockets, please inform
the teaching team when uploading the code, and briefly conclude your design and
implementation in your README.
Then, in your repository, have a release with both title and tag as p2. The release
should contain:
• The source code of your project;
• A README file that includes the information mentioned above.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
