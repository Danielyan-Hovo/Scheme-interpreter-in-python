# Scheme-interpreter-in-python
This project is an interpreter for the Scheme dialect of the Lisp programming language, which is implemented in Python.


____This is an interpreter for a sub-set of the Scheme programming language____

This is a current high-level overview of the interpreter
     Scheme code => High-Level Interpreter => Output
     
******To use the interpreter******
We did a test to understand whether the program works correctly or not.
Your can run the program for the programs you want by writing the program 
to the input.txt file which is located in a folder named "test", execute the
"make" command on the command line, which will build the necessary files for
the program and make a test. Then use the "make clean" command on the command
line to delete the created files.

To run the program you must perform the following steps
1. execute the "make" command on the command line, which will run the program
2. then use the "make clean" command on the command line to delete the created files.


___The interpreter supports  arithmetic, logical and equality operators,
 basic math operators (cos, sin, abs, ...) , the length, remainder, 
begin, car, cdr, list operations, if/else statement  display,
 define, define-syntax, syntax_rules and lambda.

Each statement in the source file will be evaluated in turn,
and any printable results will be displayed to standard output.

_____Brief description of the program_____

The program receives a text file, divides it into action blocks.
In order to correctly organize the sequence of operations,
there is a recursively written function called compile, 
to understand which operation should be performed first.
The function is called through the compile function,
which performs the next operation of the list and returns a value.
The value returned by the function is placed instead of a sequential list.
Since Nones are generated during the return values of the functions,
there is a clean function that cleans the current list from unnecessary
values every time.
The program also uses a few more functions that are used in the 
functions listed above, this was done to have more readable code and 
concise functions.
Then, due to recursion, this operation continues until the end of operations.

_____GUI description_____
A GUI (graphical user interface) is a system of 
interactive visual components for computer software.

GUI was written using the tkinter library of the python language.
The program allows you to open the file, close it, open a new window,
save, edit, run the code, and a number of other options that you 
can see when opening the window,

**To open the window you need to write in the command line**
	*python3 gui.py:

A window will open and you can run the interpreter.py file right here and see the output
To do this, you need to do the following:
	ֆայլ => բացել => select the file you want to run, in this case it's a  text file,
	in which is written scheme code => աեղմել open =>  Աշտատացնել 



______detailed description of functions______

__paring__
Function takes a filename as an argument. Reads symbol by symbol, considers a number of cases depending on the symbol read,
divides by tokens. also solves the problem of comments, it ignores it and does not put it in the list.
Function returns the list of received tokens.

__parse__
the function receives as an argument the list returned by the parting function. checks the correctness of parentheses 
using the parentheses function. the resulting list is modified by the action block using the push function,
which sorts the actions in the list according to the nested parentheses. Function returns the received list

__change__
The function receives a list of tokens. The purpose of the function is as follows. Replaces the variables in the 
list with their value. If function , calls the corresponding function, placing the value instead of the list.
Function returns the newly received list 

__clean__
Function takes a list. It is possible that None values were generated during operations in the list, 
the rm function is called, which removes that value from the list. After that, there may be redundant 
nested lists in the new list. The clean function corrects the embeddedness of the list. 
Function Returns the newly received list

__define__
The function receives a list of tokens, depending on the length of the list, declares a variable and adds it to 
the my_var dictionary, or declares a function that is added to the dictionary by its name, arguments, and body.

__run__
Function is called when a function call that has already been declared is encountered in the program. 
The function checks the correctness of the number of arguments, the arguments in the body of the function 
are replaced by their values using the change function. according to how the function is declared (define-syntax, define)
implements the body of the function as a separate expression.

__display__
Function checks the grammar of the display function,
and then outputs the required value to the screen with standard input.

__current_action__
Current_action is a recursive function that takes a list and finds the first action to be executed, 
this is used in the compile function

__compile__
Compile is the main function of the program that performs the current operations
by calling the corresponding functions. With the help of dictionaries, the function finds
and calls the corresponding function that shoul be executed at the given moment.
Then, due to recursion, this operation continues until the end of operations.

**newline, math_, quantity_operators, arithmetic_operators, logical_operators, let
if_statement, remainder, list_, def_syntax, syntax_rules, begin, length, car, lambda_, cdr, lambda**
these functions are the functions in the scheme implemented in the python language,
these are called when we use them in the scheme file
