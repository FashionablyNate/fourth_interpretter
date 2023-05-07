# Fourth Interpreter

This repository contains a Haskell implementation of a simple Reverse Polish Notation (RPN) interpreter based on the Forth programming language. The interpreter supports basic arithmetic operations, conditional statements, loops, user-defined functions, and comparison operators.

## Features

The interpreter supports the following commands:

| Command      | Description                                                      | Example        |
|--------------|------------------------------------------------------------------|----------------|
| +            | Add the top two elements of the stack and push the result       | 2 2 + -> 4     |
| -            | Subtract the top element from the second-to-top element and push the result | 3 2 - -> 1  |
| *            | Multiply the top two elements of the stack and push the result  | 2 3 * -> 6     |
| /            | Divide the top element by the second-to-top element and push the result | 3 2 / -> 1.5  |
| dup          | Duplicate the top element of the stack                           | 2 dup -> 2 2   |
| drop         | Delete the top element of the stack                             | 2 2 drop -> 2  |
| rot          | Rotate the top three elements towards the top of the stack (to the right) | 1 2 3 rot -> 3 1 2 |
| swap         | Swap the two values at the top of the stack                     | 7 2 swap -> 2 7 |
| /'...'/      | Comments, text between /' and '/ will be ignored                | /' This is a comment '/ |
| if [code1] else [code2] ; | Conditional statement, runs code1 if top of the stack is not zero, otherwise runs code2 | 1 if 2 else 3 ; -> 1 2 |
| while [code] ; | While loop, runs code repeatedly as long as the top of the stack is not zero | 5 while 7 swap 1 - ; drop -> 7 7 7 7 7 |
| ==, /=, <, <=, >, >= | Comparison operators, perform comparison and push 1.0 if true, otherwise push 0.0 | 50 50 == -> 1.0 |
| : func_name [code] ; | Define a function, runs code when the function is called | : add2 2 + ; |

## Usage

To use the Fourth interpreter, simply clone the repository, build the project, and execute the compiled program. The interpreter reads input from the command line.

## Examples

```haskell
-- Define a function to add 2 to a number
: add2 2 + ;

-- Call the add2 function twice on the number 5
5 add2 add2 -- Stack: [9.0]

-- Define a function to push 4 numbers onto the stack
: just_4_numbers 1 2 3 4 ;

-- Define a function to add 4 numbers together
: add4 + + + ;

-- Call the functions to push the 4 numbers and add them
just_4_numbers
add4 -- Stack: [10.0]

This was an assignment for a Programming Language Design class at Washington State University. All credits go to Grant Williams for the instructions and requirements of this assignment.