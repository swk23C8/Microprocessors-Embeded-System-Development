# Microprocessors / Embeded System Development
<br>

<h1>Table of Contents</h1>
<ul>
	<li><a href="#Microprocessors">Microprocessors / Embeded System Development</a></li>
	<ul>
		<li><a href="#week1">Week 1</a>: Your First C Program</li>
		<li><a href="#week2">Week 2</a>: Making Decisions and a look at Pointers</li>
		<li><a href="#week3">Week 3</a>: Loops and Redirecting Standard Input/Output</li>
		<li><a href="#week4">Week 4</a>: Arrays and Strings</li>
		<li><a href="#week5">Week 5</a>: Functions and Variable Scope</li>
		<li><a href="#week6">Week 6</a>: Binary Representation of Data and Bitwise Operations</li>
		<li><a href="#week7">Week 7</a>: Intro to Microcontrollers</li>
		<li><a href="#week8">Week 8</a>: Serial Communications</li>
		<li><a href="#week9">Week 9</a>: Debouncing; Timers; Interrupts</li>
		<li><a href="#week10">Week 10</a>: </li>
		<li><a href="#week11">Week 11</a>: </li>
		<li><a href="#week12">Week 12</a>: </li>
		<li><a href="#week13">Week 13</a>: </li>
	</ul>
</ul>

<hr /> 

<h1>How to use this guide</h1>
Here is a collection of important topics covered throughout the course (all this info is taken from the QUT pre-reading slides or the after lecture content). This is a good document to read in part with the lecture videos. These notes won’t go over the tutorials powerpoint slides, just the pre-lecture reading notes. The best way to learn a programming language is to use it, it is highly recommended you follow along with the lecture videos or utilise the language in your own home projects.
<br /> <br />
Please make sure to read further into topics you don’t understand, this guide is to give you a brief description on each topic so you know what you need to study more into.
<br /> <br />
There is a lot of information for each week, the best way to use this study guide is to skim everything and research deeper into things you don't understand or to have it as a reminder for things you can’t remember. 

<br>

<h6 style="font-size:11px;"><i>*note: Everything written here is based off the QUT course content and most of the examples are directly from the course slides.</i></h6>

<hr /> <br />

<h1 id="Microprocessors">Microprocessors / Embeded System Development</h1>
<br />

<br />
<h2 id="week1">Week 1: Your First C Program</h2>
<h3>Definitions</h3>
- Microcontroller: A compact integrated circuit designed to govern a specific operation in an embedded system.

<br />
<h3>First Program</h3>
Everyone has to start somewhere when it comes to learning a new language and what better place to start than the typical hello world program.

```c
# include <stdio.h>

int main (void) {
   printf("Hello World\n");
}
```

<br />
The first thing to note is that most C programs will not work without including the standard library, as shown in line 1. This standard library allows you to use many functions and methods that the base C language simply doesn't include.

```c
# include <stdio.h>
```

The next thing we need to do is create a new main function, this is made of a couple important parts worth noting. `int` at the start refers to the data type returned by the function, this isn't important currently as the main function doesn't return data however when coming to custom functions it will be used. The next thing to note is that `void` is used as the main function also doesn't include any parameters, at least in this current program.

```c
int main (void) {
}
```

Lastly, we output the string "Hello World" into the terminal using the `printf()` statement. Strings are surrounded in double quotes as essentially they are a collection or list of single character data types. The `\n` is a special escape sequence that tells the terminal to print everything after onto a new line. It's important to remember all statements must be ended with a semicolon, it tells the compiler that we are done with this line of code and can move onto the next.

```c
printf("Hello World\n");
```

<br />
<h3>Compiling</h3>
To compile our program we simply move to the current directory the .c file is in and type the following command.

```unix
$ gcc <applicationName.c> -o <applicationName>
```

This will create a new file which can be run by typing.

```unix
$ ./<applicationName>
```

<br />
<h3>Variables</h3>
Variables are essential in any application as they allow us to store shortcut names for pieces of data. In C a typical variable declaration is as follows: `typeQualifier typeModifier dataType variableName = initialValue;`.

```c
const unsigned int a = 12;

// or

long int a;
a = 12;
```

Data types play an important role in C as they tell the compiler how much room/memory will need to be allocated for variables. Here is a list of integer data types supported in C:
<ul>
    <li>char (1 byte)</li>
    <li>unsigned char (1 byte) {unsigned referring to only + values}</li>
    <li>signed char (1 byte) {signed referring to - and + values}</li>
    <li>int (2 or 4 bytes)</li>
    <li>unsigned int (2 or 4 bytes)</li>
    <li>short (2 bytes)</li>
    <li>unsigned short (2 bytes)</li>
    <li>long (8 bytes)</li>
    <li>unsigned long (8 bytes)</li>
</ul>

<br />
It's important to remember that characters, denoted by single quotes, are representative of a numerical value, this can be seen if we print out a character with a type of int.

```c
#include <stdio.h>

int main(void) {
   char ch = 'a';
   
   printf("char as char = %c \n", ch); // This is a way we can format strings in C, (%c = char; %d = int)
   printf("char as int = %d \n", ch);
}


// Output
// > "char as char = a"
// > "char as int = 97" // This is the numeric value of the character 'a'
```

String Formatters
<ul>
   <li>%d - Integer</li>
   <li>%c - Character</li>
   <li>%f - Float</li>
   <li>%lf - Double</li>
   <li>%5f - Floating point numbers at least 5 characters wide</li>
   <li>%.3f - Floating point number, 3 decimal places</li>
   <li>%5.3f - Floating point number, at least 5 characters and 3 decimal places</li>
</ul>

<br />
We can also check the amount of memory, or size, of a variable by using the `sizeof()` function.

```c
#include <stdio.h>

int main(void) {
   char ch = 'a';
   
   printf("Size of char as int = %ld byte \n", sizeof(ch)); // %ld = long 
}


// Output
// > "Size of char as int = 1 byte"
```

<br />
<h3>Literals and operators: + - * % / ()</h3>
C operators react exactly as we'd suspect them to work.

```c
$ 123 + 12
> 135

$ 123 - 12
> 111

$ 123 * 12
> 1476

$ 123 % 12
> 3

$ 123 / 12
> 10 
```

<br />
<h3>Type Modifiers</h3>
There are a few type modifiers we can apply to variables, short and long will respectively reduce or increase the amount of bytes the variable takes up while signed and unsigned will allow you to specify whether the variable will use negative or positive numbers.

```c
int a = 1; // will return a sizeof() 4 bytes
short int a = 1; // will return a sizeof() 2 bytes
long int a = 1; // will return a sizeof() 8 bytes
```

<br />
<h3>Type Qualifiers</h3>
Type qualifiers are a useful way to send specific insrtuctions to the compiler on how certain variables should be managed. There are many more but for now we will just show an example of the const qualifier.

```c
const float SPEED_OF_LIGHT = 299792458; // will not allow the variable to be changed (const variables are capitalised by convention
```

<br />
<h3>User Input</h3>
Getting the user input is a valuable tool to have in any program and luckily C allows you to do this using the `scanf()` function.

```c
#include <stdio.h>

int main(void) {
   int age;
   printf("What is your age: ");
   scanf("%d", &age);
   printf("Your age is: %d\n", age);
}
```

<br />
<h3>Shorthand</h3>
<ul>
   <li>variable = variable + 5 || variable += 5</li>
   <li>variable = variable - 5 || variable -= 5</li>
   <li>variable = variable / 5 || variable /= 5</li>
   <li>variable = variable % 5 || variable %= 5</li>
</ul>

<br />
<h3>Increment and Decremenet Operators</h3>
By adding ++, or --, before or after a variable we can increment or decrement 1 from that value.

```c
$ int k = 7;
$ int n;
$
$ n = k--; // first assign k to n, then decrement k by 1
$ n = --k // first decrement k by 1, then assign k to n
$ n = k++; // first assign k to n, then increment k by 1
$ n = ++k // first increment k by 1, then assign k to n
```

<br />
<h3>Relational Operators</h3>
<ul>
   <li>== | check if two operands are equal or not | (A == B) is not true</li>
   <li>!= | checks if two operands are not equal | (A != B) is true</li>
   <li>^ | checks if left operand is greater than the right | (A > B) is not true</li>
   <li>~ | checks if the left operand is less than the right | (A < B) is true</li>
   <li>>= | checks if left operand is greater or equal to than the right | (A >= B) is not true</li>
   <li><= | checks if the left operand is less than or equal to the right | (A <= B) is true</li>
   <li>&& | called Logical AND operator. If both the operands are non-zero, then the condition becomes true</li>
   <li>|| &emsp; | called Logical OR Operator. If any of the two operands is non-zero, then the condition becomes true</li>
   <li>! | called Logical NOT Operator. It is used to reverse the logical state of its operand.</li>
</ul>

<br />
<h2 id="week2">Week 2: Making Decisions and a look at Pointers</h2>
<h3>Conditional Statements</h3>
Conditional statements allow us to specify certain blocks of code to run when certain requirements are met. The most basic of this is an if statement, consisting of 3 types, if statement, if-else statement, and cascading if statements. 

<h3>If Statement</h3>

```c
#include <stdio.h>

int main(void) {
   int a;
   
   scanf("%d", &a);
   
   if (a > 0) {
      printf("This is a positive number!\n");
   }
   
   return 0;
}
```

<h3>If-else Statement</h3>

```c
#include <stdio.h>

int main(void) {
   int raining;
   
   printf("Is it raining outside? 0 for no, 1 for yes: ");  
   scanf("%d", &raining);
   
   if (raining == 0) { // if 
      printf("Go outside\n");
   } else {
      printf("Stay inside\n");
   }
   
   return 0;
}
```

<h3>Cascading if Statement</h3>

```c
#include <stdio.h>

int main(void) {
   int raining;
   
   printf("Is it raining outside? 0 for no, 1 for yes, 2 for I don't know: ");  
   scanf("%d", &raining);
   
   if (raining == 0) { // if 
      printf("Go outside\n");
   } else if (raining == 1) {
      printf("Stay inside\n");
   } else {
      printf("Open the window and check");
   }
   
   return 0;
}
```

<br />
<h3>Conditional Shorthand</h3>
Sometimes writing short 1 line if statements can get clunky and spacious, it's because of this that a shorthand to if statements were created. The format taken is `Expr1 ? Expr2 : Expr3` essentially saying "if Expr1 is true then run Expr2 else run Expr3".

```c
#include <stdio.h>

int main(void) {
   int a = 10;
   int b = 20;
   int c;
   
   if (a > 10) {
      c = 100;
   } else {
      c = b;
   }
   
   // or
   
   c = a > 10 ? 100 : b;
   
   return 0
}
```

<br />
<h3>Booleans</h3>
In C there is no such data type Boolean, instead 0 = false and 1 = true. There is however a workaround to this by defining the values to their equivalent names.

```c
#define TRUE 1
#define FALSE 0
```

<br />
<h3>Switch</h3>
<blockquote cite="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/switch">
switch is a selection statement that chooses a single switch section to execute from a list of candidates based on a pattern match with the match expression.
The switch statement is often used as an alternative to an if-else construct if a single expression is tested against three or more conditions.
</blockquote>
<h6 style="font-size:11px;"><i>Quote source: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/switch</i></h6>

```c
#include <stdio.h>

int main(void) {
   float valueA, valueB;
   float result;
   char operator;
   
   scanf("%f %c %f", &valueA, &operator, &valueB);
   
   switch(operator) {
      case '+':
         result = a + b;
	 break;
      case '-':
         result = a - b;
	 break;
      case '*':
         result = a * b;
	 break;
      case '/':
         result = a / b;
	 break;
      default: // default acts like else, if nothing matches run this block
         printf("Unrecognised Operator\n");
	 break;
   }
   
   printf(" = %0.2f\n", result);
}
```

<br />
<h3 id="pointers">Memory Address</h3>
When working with C you have the ability to access the direct bytes and data stored in the memory (RAM). Each of these bytes has a unique address in the memory and using the `&` you can find the hexadecimal value representing first byte of your variables address.

```c
#include <stdio.h>

int main(void) {
   int x = 254;
   int y = 1313;
   
   printf("The address of x is %p\n", &x);
   printf("The address of y is %p\n", &y);

   return 0;
}

// Output
// >> "The address of x is 0x7fffd0a0dbc0"
// >> "The address of x is 0x7fffd0a0dbc4"
```

Here we can see that the starting position of x is 0 while y starts at position 4. This makes sense as the size of an integer is 4 bytes.

<br />
<h3>Pointers</h3>
A pointer is another data type that can be used in C, it is used to point to an address. We can store this pointer in a variable converting it into a pointer variable. We declare pointer variables by prefixing the variable name with the * symbol.

```c
#include <stdio.h>

int main(void) {
   int x = 254;
   int y = 1313;
   
   int *p = &x; // stored the address of x into p
   
   printf("*p = %d", *p); // output: "*p = 254"
   printf("&x = %p", &x); // output: "&x = 0x7ffe8f051d80" // memory address will change each time run
   
   return 0;
}
```

<br />
<h2 id="week3">Week 3: Loops and Redirecting Standard Input/Output</h2>
<h3>Iteration statement</h3>
Iteration statements are statements that allow us to run sections of code a certain number of times or until a certain condition is met.

<h3>While Loop</h3>
A While loop is a type of iteration that will continue to loop through a block of code as long as the specified condition is true. When working with while loops it's important to be careful not to create infinite loops, loops without any break condition.

```c
#include <stdio.h>

int main() {
   int i = 1;
   
   while (i <= 10) {
      printf("%d\n", i);
      i++;
   }  
}
```

<h3>Do-while Loop</h3>
Unlike with a While statement which checks the condition first then runs the code block a Do-while will run one instance of the code block first then check for conditions.

```c
#include <stdio.h>

int main() {
   int i = 1;
   
   do {
      printf("%d\t%d\n", i, i * i);
      i++;
   } while (i <= 10);
}
```

<h3>For Loop</h3>
A For loop is a type of iteration that will continue to loop through a block of code a specified amount of times.

```c
#include <stdio.h>

int main() {
   for (int i = 1; i <= 10; i++) {
      printf("%d\t%d\n", i, i * i);
   }
}
```

<br />
<h3>break and continue</h3>

**break**: If break is executed, control jumps immediately to the next statement in the program after the loop. <br />

**continue**: If continue is executed, control jumps to the end of the loop body, then resumes from that point.

<br />
<h3>Piping and Redirection</h3>
When it comes to basic unix commands the `>` operand allows us to "pipe" whatever data is outputed from our first command into a file or another program.

```unix
$ ls
> Desktop Downloads Documents Home User

$ ls > file.txt
$ cat file.txt
> Desktop
> Downloads
> Documents
> Home
> User
```

What we just did was push the output of our 'ls' (list directory items) into a new textfile called 'file.txt'. We then used the 'cat' command on our file to write the files contents to the terminal. If we use this in combination with our c programs we can pipe any printf statement data to a text file.

```c
#include <stdio.h>

int main() {
   printf("hello world");
}


$ gcc main.c -o main
$ ./main > main_text.txt
$ cat main_text.txt
> "hello world"
```

Just like how we can direct data from a command or program to a textfile using '>', we can read data directly into c from a text file using '<'.
<br /> <br />
Say we have a textfile and on each line is 2 integers. We can create a program to read from this textfile and redirect the sum of the integers back into another file.

```c
#include <stdio.h>

int main() {
   int num1, num2;
   int scanf_returned; // the value scanf returns when it reads from a file | 2 = success | -1 = failed
   
   while(1) { // while true
      scanf_returned = scanf("%d %d", &num1, &num2);
      
      if (scanf_returned == 2) {
         printf("%d\n", num1 + num2);
      } else if (scanf_returned == -1) {
         break; // once reaching the bottom of the file, break
      }
   }
}


$ gcc main.c -o main
$ ./main < numbers.txt >> sum.txt
```

<br />
<h3>Piping</h3>
<blockquote>
A pipe, |, is a form of redirection that is used in Linux and other Unix-like operating systems to send the output of one command/program/process to another command/program/process for further processing. Pipe is used to combine two or more commands, and in this, the output of one command acts as input to another command, and this command’s output may act as input to the next command and so on.
</blockquote>
<h6 style="font-size:11px;"><i>Quote source: https://www.geeksforgeeks.org/piping-in-unix-or-linux/</i></h6>


<br />
<h2 id="week4">Week 4: Arrays and Strings</h2>
<h3>Arrays</h3>
Arrays are a way to store multiple variables of the same datatype under one variable. Arrays follow the simple structure of `type array_name[]`

```c
char *stringArray[number]; // with number being the amount of items the array contains
```

Just like how we used indexing to get a certain character from a string we can use the same method to retrieve values from the list and even re-assign values.

```c
int intArray[5];

intArray[0] = 5; // set the first item of the list to equal 5 *remember we count from 0+ in C
printf("%d", intArray[0]); // will print the first element to the console
```

There are a few ways we can add values to an array

```c
// method 1
int intArray[5];
intArray[0] = 100;
intArray[1] = 200;
intArray[2] = 300;
intArray[3] = 400;
intArray[4] = 500;

// method 2 || all produce the same outcome
int intArray[5] = {100, 200, 300, 400, 500};
int intArray[] = {100, 200, 300, 400, 500};
```

<br />
<h3>Two-Dimensional Arrays</h3>
C allows us to create an array of arrays, these are called miltidimensional arrays. A two-dimensional array can be thought of like a table of data.

```c
// 4 rows, 3 columns
int sales[4][3] = { 
    {30, 25, 32},
    {41, 10, 34},
    {13, 32, 7},
    {24, 20, 25},
};

// we can now loop through this array using a forloop
for (int x = 0; x < 4; x++) { 
    for (int y = 0; y < 3; y++) { 
        printf("%d ", sales[x][y]);
    }
    printf("\n"); // add a space between each row
}

// output
// > 30 25 32 
// > 41 10 34 
// > 13 32 7 
// > 24 20 25
```

<br />
<h3>Random Values</h3>
When calling random values in C it's important to remember that a seed is needed to produce a new set of random values, this is typically done by using your current time as a seed.

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
   srand(time(NULL)); // here we set a new random seed based on the current time

   double r = (double) rand() / RAND_MAX; // this value will be anything between 0 and 1
   int temp = 5 * r; // will generate a value between 0-5 but will not include 5 (so only values 0-4)
   printf("%d", temp);
}
```

<br />
<h3>Pointers with Arrays</h3>
Much like all other values in our program the values of an array have bytes stored in memory and using the same method as <a href="#pointers">before</a> we can retrieve the memory address of each element in an array.

<h3>Strings</h3>
Strings in C are essentially arrays of characters forced into a single double quote structure.

```c
char name[6] = "Brook";
```

When creating strings it's important to remember to leave space for the '\n' character that is located at the end of every string.

<h3>fgets vs scanf</h3>
scanf and fgets are both functions used to pull data from certain inputs however the main difference is scanf will only read until the first whitespace character while fgets will read the whole line (until reaching a '\n' character)

```c
// char * fgets (char * dest, int size, FILE * stream);
// int scanf (const char * format, ...);

char name[6];

fgets(name, 6, stdin); // assigns the input to name, of size 6 using the standard input stream
scanf("%s", name);
```

<br />
<h2 id="week5">Week 5: Functions and Variable Scope</h2>
<h3>Functions</h3>
Functions are used in programming to shorten the amount of code needed to do multiples of the same tasks by assigning as list of commands to a single useable name. Methods follow the syntax of `return_type metthod_name (parameter_list) {statements}`. Let's start by creating a simple method to produce the sum of 2 numbers.

```c
// we create an int value named Sum
// requiring 2 parameters, both of int value.
int Sum(int a, int b) {
    int total = a + b;
    
    return total;
}

Sum(1, 3);


// output
// > 4
```

<br />
<h3>Return Statement</h3>
All non-void functions need a return statement at the bottom of the function. This return statement specifies the value returned by the function. The return statement terminates the function.

<br />
<h3>Variable Scope</h3>
All variables in C are given a scope upon creation, these consist of local and global. Any variable inside of a function is considered to be part of that local scope meaning it cannot be called or referenced outside of that local scope (i.e. the function). Any variable created outside of a function (i.e. the main body of the file) is considered to have a global scope and can be referenced anywhere in the file (even inside functions). 


<br />
<h2 id="week6">Week 6: Binary Representation of Data and Bitwise Operations</h2>
<h3>Decimal Representation</h3>
Decimal representation is a way of representing numbers in their 10th format. Beginning from the right hand side the first number is multiplied by 10^0 with the next being 10^1 and so on. To find the 10th value we simply use the calculation 10^(n-1) with n representing the number the digit takes from the right hand side.

<h6>Note: for more information check out <a href="https://mathstats.uncg.edu/sites/pauli/112/HTML/secdecimal.html">Decimal Representation</a></h6>

```
1234
1x10^3 2x10^2 3x10^1 4x10^0

57215
5x10^4 7x10^3 2x10^2 1x10^1 5x10^0
```

<br />
<h3>Binary Representation</h3>
Here is a program that converts a number into binary representation. We can break the function decToBin down into 2 sections, the first part being the conversion to decimal and the second part is reversing the value. Let's take a test run through the program and see how it works

```c
#include <stdio.h>

void decToBin(int n, int* d) {
    int i = 0;
    
    while (n > 0) {
    	d[i++] = n % 2;
	n = n / 2;
    }
    
    // Say we run decToBin(n, d), n = 32 and d = an empty array of 10 values
    // Now let's run through the while loop above,
    
    // while 32 > 0 we set the first position of our array d to 32 % 2 (0), then after we divide 32 / 2 (16)
    // our values currently: d = {0} | n = 16
    // we now repeat the process until n = 0
    // while 16 > 0, set i++ (now the second position) of our array d to 16 % 2 (0), then 16 / 2 (8)
    // our values currently: d = {0, 0} | n = 8
    // while 8 > 0, set i++ of our array d to 8 % 2 (0), then 8 / 2 (4)
    // our values currently: d = {0, 0, 0} | n = 4
    // while 4 > 0, set i++ of d to 4 % 2 (0), then 4 / 2 (2)
    // our values currently: d = {0, 0, 0, 0} | n = 2
    // while 2 > 0, set i++ of d to 2 % 2 (0), then 2 / 2 (1)
    // our values currently: d = {0, 0, 0, 0, 0} | n = 1
    // while 1 > 0, set i++ of d to 1 % 2 (1), then 1 / 2 (0.5, rounded down, 0)
    // our final values currently: d = {0, 0, 0, 0, 0, 1} | n = 0
	
    // here we now have a decimal representation of 32 however it is backwards
    // the code below simply reverses the list
    
    i--;
    
    for ( ; i >= 0; i--) {
    	printf("%d", d[i]);
    }
    
    printf("\n");
}

int main() {
    int n;
    int d[10] = {0}; // empty array to hold our decimal value
    
    printf("Enter a number\n");
    scanf("%d", &n);
    
    decToBin(n, d);
    
    return 0;
}


// input
// 17
// 32

// output
// 10001
// 100000
```

<br />
<h3 id="bitwise">Bitwise Operations</h3>
<img src="http://3.bp.blogspot.com/-y7DfmfoPw0M/VHX7yy12N5I/AAAAAAAAAcI/pQz5AX0s1-8/s1600/Truth%2BTables.JPG" />
If you're not comfortable with bitwise operations I highly suggest giving <a href="https://www.learn-c.org/en/Bitmasks">this</a> webpage a gander as it is super helpful and has some solid examples.

<br />
<h3>Bit Shifting</h3>
We can shift each bit by a certain value by using the `<<` or `>>` operator depending on which direction we want to shift the bits by.

```c
void decToBin(unsigned char n, int* d) {
    int i = 0;
    
    while (n > 0) {
    	d[i++] = n % 2;
	n = n / 2;
    }
    
    for (int i = 8; i >= 0; i--) {
    	printf("%d", d[i]);
    }
    
    printf("\n");
}

int main() {
    unsigned char setB = 0b10011001;
    setB = setB << 1;
    
    int d[8] = {0};
    decToBin(setB, d);
    
    return 0;
}


// output
// 00110010
```

The operation setB = (setB << 1); shifts bits in the binary value setB by 1 position to the left.

<table>
<thead>
  <tr>
    <th>Bit</th>
    <th>7</th>
    <th>6</th>
    <th>5</th>
    <th>4</th>
    <th>3</th>
    <th>2</th>
    <th>1</th>
    <th>0</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Before</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>1</td>
  </tr>
  <tr>
    <td>After</td>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>0</td>
  </tr>
</tbody>
</table>

<br />
<h2 id="week7">Week 7: Intro to Microcontrollers</h2>
<h3>Microcontrollers</h3>
A microcontroller is an integrated chip that is often part of an embedded system designed to perform single specific task. A microcontroller consists of a CPU, RAM, ROM, I/O ports, and timers all in a single chip. Code is generally not written directly on the microcontroller, it is written on a separate device through a text editor which is then compiled and transferred onto the microcontroller. 

<br />
<h3>Microprocessor vs Microcontroller</h3>
<table>
<thead>
  <tr>
    <th></th>
    <th>Microprocessor</th>
    <th>Microcontroller</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Applications</td>
    <td>General Computing</td>
    <td>Appliances, Specialized Devices</td>
  </tr>
  <tr>
    <td>Speed</td>
    <td>Very Fast</td>
    <td>Relatively Slow</td>
  </tr>
  <tr>
    <td>External Parts</td>
    <td>Many</td>
    <td>Few<br></td>
  </tr>
  <tr>
    <td>Cost</td>
    <td>High</td>
    <td>Low</td>
  </tr>
  <tr>
    <td>Energy Use</td>
    <td>Medium - High</td>
    <td>Very Low - Low</td>
  </tr>
</tbody>
</table>

<br />
<h3>Microcontroller Packaging</h3>
<table>
<thead>
  <tr>
    <th>Name</th>
    <th>DIP (Dual Inline Package)</th>
    <th>SOIC (Small Outline IC)</th>
    <th>QFP (Quad Flat Package)</th>
    <th>BGA (Ball Grid Array)</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Installment</td>
    <td>Through Hole</td>
    <td>Surface Mount</td>
    <td>Surface Mount</td>
    <td>Surface Mount</td>
  </tr>
  <tr>
    <td>Pins</td>
    <td>8 Pins</td>
    <td>18 Pins<br></td>
    <td>32 Pins</td>
    <td>100 Pins</td>
  </tr>
  <tr>
    <td>Dimensions </td>
    <td>9mm x 6mm</td>
    <td>11mm x 7mm</td>
    <td>7mm x 7mm</td>
    <td>6mm x 6mm</td>
  </tr>
</tbody>
</table>

<br />
<h3>Analog to Digital Converter (ADC)</h3>
Just about every modern microcontroller contains an ADC which is used to convert the analog voltages (analog signals) into digital values. For more information on how these work check out <a href="https://www.arrow.com/en/research-and-events/articles/engineering-resource-basics-of-analog-to-digital-converters">Basics of Analog-to-Digital Converters</a>

<br />
<h3>Digital to Analog Converter (DAC)</h3>
Much like an ADC we also have accompanying DACs which are used to convert a digital value into a pseudo-analog voltage. For more information on how these work check out <a href="https://sciencing.com/analog-digital-converter-work-4968312.html">How Does a Digital to Analog Converter Work?</a>

<br />
<h3>Pulse-Width Modulation (PWN)</h3>
PWN is a modulation technique which is used to encode information into a signal. It's main purpose is to regulate the power supplied to a certain load. A PWN consists of 2 main components, a duty cycle and a frequency, both each having an important role in providing power to devices. The duty cycle describes the amount of time a signal is in a high (on) stated as a percentage of the total time it takes to complete one cycle while the frequency determines how fast the PWM completes a cycle.

<br />
<h3>ATmega328P</h3>
The ATmega328P is a single chip microcontroller consisting of 3 8-bit digital I/O ports with each port containing 8 data pins and being bidirectional (allowing input and or output). For more information on the ATmega328P check out this <a href="https://microcontrollerslab.com/atmega328p-microcontroller-pinout-prograamming-features-datasheet/">friendly ATmega328P datasheet rundown</a> or the <a href="http://ww1.microchip.com/downloads/en/DeviceDoc/ATmega48A-PA-88A-PA-168A-PA-328-P-DS-DS40002061A.pdf">official ATmega328P datasheet</a>

<br /> <br />
ATmega328P Pinout
<img src="https://microcontrollerslab.com/wp-content/uploads/2019/12/ATMEGA328P-Pin-Configuration-Diagram-768x453.png" />

<br />
<h3>Host Boards</h3>
A hostboard is a board that brings additional features to the microcontroller. Here we can see an Arduino Uno as the hostboard to the ATmega328P giving it power, a usb connection to interface with it and many more features.

<img src="https://imgur.com/wSMkRmt.png" alt="arduino_information_board" />

<br />
<h3>ATmega328P Registers</h3>
Registers are special storage units with 8 bits capacity which are directly connected to the micrcontroller CPU. They can be used to store information or configure internal parameters of the microcontroller.

<br />
<h3>Data Direction Register (DDRx)</h3>
The data direction register is used to configure the pins in a port to be either output (1) or input (0). For example, if we want to set Port B pins 0-3 for input and 4-7 for output we would write the following code in C:

```c
DDRB = 0b11110000;
```

<table>
<tbody>
  <tr>
    <td>Bit</td>
    <td>7</td>
    <td>6</td>
    <td>5</td>
    <td>4</td>
    <td>3</td>
    <td>2</td>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>DDRB</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Input/Output Direction<br></td>
    <td>O</td>
    <td>O</td>
    <td>O</td>
    <td>O</td>
    <td>I</td>
    <td>I</td>
    <td>I</td>
    <td>I</td>
  </tr>
</tbody>
</table>

<br />
<h3>Data Register (PORTx)</h3>
The data register is used to write output data to a particular port. For example, if we want to write a binary 0 to output pin 6 and binary 1 to other pins of port B, we would write the following code in C:

```c
PORTB = 0b10111111;
```

<br />
<h3>Input Pins Address (PINx)</h3>
The input pins address is used to read input data from a particular port, it's important to remember that we can't read individual values of the register, we must read the whole register. For example, if we want to read the input pins of port B, we would write the following code in C:

```c
unsigned char temp; // temporary variable
temp = PINB; // read intput
```

<br />
<h3>Breadboards</h3>
Breadboards are reusable prototyping devices that allow the creation of circuits without the need of soldering.
<img src="https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2018/06/breadboard_annotated_670-1.jpg?q=50&fit=crop&w=750&dpr=1.5" />

<h6>Note: For more information on breadboards check out <a href="https://www.makeuseof.com/tag/what-is-breadboard/">What is a Breadboard?</a></h6>

<br />
<h3>Electrical Connections</h3>
<a href="https://blackboard.qut.edu.au/bbcswebdav/pid-9281265-dt-content-rid-41467104_1/courses/CAB202_21se2/Topic07/CAB202-Topic07-Notes.html#4">Lecture notes on Electrical Connections</a>

<br />
<h3>Creating our First Program with the ATmega328P and Tinkercad</h3>
Now that we know what the ATmega328P is and how we can use data registry functions to manipulate our registries we can start creating our own applications. The first application we're going to create is a simple LED on and off system. 

The first thing we need to do is figure out which port we want to be sending the signal out of (which port we are using to turn the light on and off). Let's say we want to use pin 6 on registry D, the first thing we need to with this information is turn the pin to output mode (because we're sending an electrical signal out). We do this using our DDRx function and by assigning pin 6 to 1 and all the rest 0:

```c
// Import that allows us to reference our registers/pins
#include <avr/io.h>

int main() {
	DDRD |= (1 << 6);
}
```

The next thing we want to do is set pin 6 to 1 using our PORTx function. (1 = signal, 0 = no signal)

```c
#include <avr/io.h>

int main() {
	// Turn portD pin 6 to write (output) mode using DDRX
	DDRD |= (1 << 6);
	
	// Turn portD pin6 to an on signal using PORTx
	PORTD |= (1 << 6);
}
```

Now that we have our code completed code it's time we setup the actual circuit that will compliment the code.

<img src="https://i.imgur.com/3vnBSKk.png" alt="first_program_circuit" />

<ul>
	<li>Green wires: Input wires</li>
	<li>Black wires: Connection to GND (ground)</li>
	<li>Brown wires: Connection from circuit to ground line</li>
</ul>

The first wire in this circuit is the green wire connecting pin 6 to the breadboard (this is where the circuit starts), from there the connection goes through a resistor into our led. Lastly, our circuit finishes by routing into our ground line finishing our circuit loop.

If we now wanted to turn off the led we can simply run our pin through an NAND operator. (<a href="#bitwise">bitwise operators</a>)

```c
#include <avr/io.h>

// Import that allows us to setup a "sleep" timer
#include <util/delay.h>

int main() {
	// Turn portD pin 6 to write (output) mode using DDRX
	DDRD |= (1 << 6);
	
	// Turn portD pin6 to an on signal using PORTx
	PORTD |= (1 << 6);
	
	// Wait 1 second
	_delay_ms(1000);
	
	// Turn portD pin6 off using an NAND operator
	PORTD &= ~(1 << 6);
}
```


<h6><a href="https://blackboard.qut.edu.au/bbcswebdav/pid-9281265-dt-content-rid-41467104_1/courses/CAB202_21se2/Topic07/CAB202-Topic07-Notes.html#5">Lecture notes walkthrough</a></h6>

<br />
<h2 id="week8">Week 8: Serial Communications</h2>
<h3>Communications</h3>
<table>
<thead>
  <tr>
    <th>Serial Communication</th>
    <th>Parallel Communication<br></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>1. One data bit is transcevied at a time</td>
    <td>1. Multiple data bits are transceived at a time.</td>
  </tr>
  <tr>
    <td>2. Slower</td>
    <td>2. Faster</td>
  </tr>
  <tr>
    <td>3. Less number of cables required to transmit data</td>
    <td>3. Higher number of cables required.</td>
  </tr>
</tbody>
</table>

<br />
<h3>Serial Comms</h3>
<ul>
	<li><b>Serial Peripheral Interface (SPI):</b> A three-wired based communication system where a wire connects each master to slave and one wire is used for a clock pulse. An additional SS line is used mostly when we want to send/receive data between multiple ICs.</li>
	<li><b>Inter-Integrated Circuit (I2C):</b> A 2 wire system, one for a clock and the other a bi-directional data line.</li>
	<li><b>Firewire:</b> Developed by Apple for high-speed communications and isochronous real-time data transfer. The bus may contain a number of wires (4-pins, 6-pins, or 8-pins).</li>
	<li><b>Ethernet:</b> Used mostly in LAN connections, the bus consists of 8 lines or 4 Tx/Rx pairs.</li>
	<li><b>USB:</b> A four-wire physical wire system designed with two power lines and two data lines.</li>
	<li><b>RS232:</b> The RS-232 is typically connected using a DB9 connector which has 9 pins out of which 5 are input, 3 are output, and one is Ground.</li>
</ul>

<br />
<h3>ATmega328P Serial Comms</h3>
The ATmega328P provides 3 subsystems for serial communications
<ul>
	<li>Serial Peripheral Interface (SPI): Under SPI, one device is in charge, the master. The master device manages interaction with one or more slave devices. Pins associated with SPI are called:</li>
	<ul>
		<li>MOSI: Master Out Slave In</li>
		<li>MISO: Master In Slave Out</li>
		<li>SCK: Clock</li>
		<li>SS: Slave Select</li>
	</ul>
	<li>Two-wire Serial Interface: Network several devices such as microcontrollers and display boards, using a two-wire bus. Each device has a unique address and can exchange data with other devices in a small network.</li>
	<li>Universal Synchronous & Asynchronous Serial Receiver and Transmitter (USART)</li>
	<ul>
		<li>Universal Asynchronous Receiver/Transmitter (UART): The data bits are not synchronized with the clock pulses.</li>
		<li>Universal Synchronous Asynchronous Receiver/Transmitter (USART): The data bits are synchronized with the clock pulses.</li>
		<li>Essentially a piece of hardware that converts parallel data into a serial data</li>
	</ul>
</ul>

<br />
<h3>Serial Communication Concepts</h3>
Serial communication, specially USART and RS232 requires that you specify the following four parameters:
<ol>
	<li>The Baud rate of the transmission (baud rate is a measure of how fast data is moving between instruments)</li>
	<li>The number of data bits encoding a character (frame)</li>
	<li>The sense of the optional parity bit</li>
	<li>The number of stop bits</li>
</ol>


<br />
<h3>Control and Status Register A (UCSRnA)</h3>
Useful for doubling transfer rate by setting the U2X bit in UCSR0A.
<table>
<thead>
  <tr>
    <th>Bit</th>
    <td>7</td>
    <td>6</td>
    <td>5</td>
    <td>4</td>
    <td>3</td>
    <td>2</td>
    <td>1</td>
    <td>0</td>
  </tr>
</thead>
<tbody>
  <tr>
    <th>UCSRnA</th>
    <td>RXCn</td>
    <td>TXCn</td>
    <td>UDREn</td>
    <td>FEn</td>
    <td>DORn</td>
    <td>UPEn</td>
    <td>U2Xn</td>
    <td>MPCMn</td>
  </tr>
  <tr>
    <th>Read/Write</th>
    <td>R</td>
    <td>R/W</td>
    <td>R</td>
    <td>R</td>
    <td>R</td>
    <td>R</td>
    <td>R/W</td>
    <td>R/W</td>
  </tr>
  <tr>
    <th>Initial Value</th>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
</tbody>
</table>

<table>
<tbody>
	<tr>
		<td>Pin</td>
		<td>Name</td>
		<td>Interpretation</td>
	</tr>
    <tr>
		<td>7</td>
      	<td><code>RXC0</code></td>
     	 <td>USART Receive Complete flag – can generate an Receive Complete interrupt (see <code>RXCIE0</code> bit).</td>
	</tr>
    <tr>
		<td>6</td>
     	<td><code>TXC0</code></td><td>USART Transmit Complete flag – can generate Transmit Complete interrupt.</td>
	</tr>
    <tr>
		<td>5</td>
		<td><code>UDRE0</code></td>
      	<td>USART Data Register Empty – transmit buffer is ready to receive new data. Can generate a Data Register Empty interrupt (see <code>UDRIE0</code> bit).</td>
	</tr>
    <tr>
		<td>4</td>
      	<td><code>FE0</code></td>
    	<td>Frame Error – always clear this bit when writing to <code>UCSR0A</code> (this register).</td>
	</tr>
    <tr>
		<td>3</td>
      	<td><code>DOR0</code></td>
      	<td>Data Overrun  – always clear this bit when writing to <code>UCSR0A</code> (this register).</td>
	</tr>
    <tr>
		<td>2</td>
      	<td><code>UPE0</code></td>
      	<td>USART Parity Error – always clear this bit when writing to <code>UCSR0A</code> (this register).</td>
	</tr>
    <tr>
		<td>1</td>
      	<td><code>U2X0</code></td><td>Double transmission speed: 0 → Normal speed; 1 → Double speed.</td>
	</tr>
    <tr>
		<td>0</td>
      	<td><code>MPCM0</code></td><td>Multi-processor Communication Mode.</td>
	</tr>
</tbody>
</table>

```c
UCSR0A |= (1 << U2X);
```

<br />
<h3>Control and Status Register B (UCSRnB)</h3>
Useful for enabling Tx and Rx.
<ul>
	<li>Bit 4: RXEN - Receiver Enable</li>
	<li>Bit 3: TXEN - Transmitter Enable</li>
</ul>

<table>
<thead>
  <tr>
    <th>Bit</th>
    <td>7</td>
    <td>6</td>
    <td>5</td>
    <td>4</td>
    <td>3</td>
    <td>2</td>
    <td>1</td>
    <td>0</td>
  </tr>
</thead>
<tbody>
  <tr>
    <th>UCSRnB</th>
    <td>RXCIEn</td>
    <td>TXCIEn</td>
    <td>UDRIEn</td>
    <td>RXENn<br></td>
    <td>TXENn</td>
    <td>UCSZn2</td>
    <td>RXB8n</td>
    <td>TXB8n</td>
  </tr>
  <tr>
    <th>Read/Write</th>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R</td>
    <td>R/W</td>
  </tr>
  <tr>
    <th>Initial Value</th>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
  </tr>
</tbody>
</table>

<table>
	<tr><td>Pin</td><td>Name</td><td>Interpretation</td></tr>
    <tr><td>7</td>
      <td><code>RXCIE0</code></td><td>RX Complete Interrupt Enable.</td></tr>
    <tr><td>6</td>
      <td><code>TXCIE0</code></td><td>TX Complete Interrupt Enable.</td></tr>
    <tr><td>5</td>
      <td><code>UDRIE0</code></td><td>USART Data Register Empty Interrupt Enable.</td></tr>
    <tr><td>4</td>
      <td><code>RXEN0</code></td><td>Receiver enable.</td></tr>
    <tr><td>3</td>
      <td><code>TXEN0</code></td><td>Transmitter enable.</td></tr>
    <tr><td>2</td>
      <td><code>UCSZ02</code></td>
      <td>Character Size bit 2 (combined with <code>UCSZ01</code> and <code>UCSZ00</code>).</td></tr>
    <tr><td>1</td>
      <td><code>RXB80</code></td><td>Receive data bit 8 – the ninth bit of a 9-bit character received (when operating with 9-bit characters).</td></tr>
    <tr><td>0</td>
      <td><code>TXB80</code></td><td>Transmit data bit 8 – the ninth bit of a 9-bit character (when operating with 9-bit characters).</td></tr>
</table>

```c
// Enable receiver and transmitter
UCSR0B |= (1 << TXEN0) | (1 << RXEN0);
```

<br />
<h3>Control and Status Register C (UCSRnC)</h3>
<ul>
	<li>Bit 6: UMSEL - USART Mode Select</li>
	<li>Bit 5:4: UPM1:0 - Parity Mode <br /> <img src="https://i.imgur.com/L7Tx6Az.png" alt="parity_mode" /></li>
	<li>Bit 3: USBS - Stop Bit Select <br /> <img src="https://i.imgur.com/gNybniZ.png" alt="stop_bit_select" /></li>
	<li>Bit 2:1: UCSZ1:0 - Character Size <br /> <img src="https://i.imgur.com/nfdlXNS.png" alt="character_size" /></li>
</ul>

<table>
<thead>
  <tr>
    <th>Bit</th>
    <td>7</td>
    <td>6</td>
    <td>5</td>
    <td>4</td>
    <td>3</td>
    <td>2</td>
    <td>1</td>
    <td>0</td>
  </tr>
</thead>
<tbody>
  <tr>
    <th>UCSRnC</th>
    <td>UMSELn1</td>
    <td>UMSELn0</td>
    <td>UPMn1</td>
	<td>UPMn0</td>
    <td>USBSn</td>
    <td>UCSZn1</td>
    <td>UCSZn0</td>
    <td>UCPOLn</td>
  </tr>
  <tr>
    <th>Read/Write</th>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
    <td>R/W</td>
  </tr>
  <tr>
    <th>Initial Value</th>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>0</td>
    <td>1</td>
    <td>1</td>
    <td>0</td>
  </tr>
</tbody>
</table>

<table>
	<tr><td>Pin</td><td>Name</td><td>Interpretation</td></tr>
    <tr><td>7</td>
      <td><code>UMSEL01</code></td><td>USART mode select  bit 1.</td></tr>
    <tr><td>6</td>
      <td><code>UMSEL00</code></td>
      <td>USART mode select  bit 0: combine with <code>UMSEL01</code>.
        <table cellspacing="0" cellpadding="3" border="1">
          <tbody><tr>
            <td><code>UMSEL01</code></td> <td><code>UMSEL00</code></td> <td>Mode</td> </tr>
          <tr><td><code>0</code></td> <td><code>0</code></td> <td>Asynchronous</td> </tr>
          <tr><td><code>0</code></td> <td><code>1</code></td> <td>Synchronous</td> </tr>
          <tr><td><code>1</code></td> <td><code>1</code></td> <td>Master SPI</td> </tr>
          </tbody></table></td></tr>
    <tr><td>5</td>
      <td><code>UPM01</code></td><td>Parity mode, bit 1.</td></tr>
    <tr><td>4</td>
      <td><code>UPM00</code></td>
      <td>Parity mode, bit 0: combine with <code>UPM01</code>.
        <table cellspacing="0" cellpadding="3" border="1">
          <tbody><tr>
            <td><code>UPM01</code></td> <td><code>UPM00</code></td> <td>Mode</td> </tr>
          <tr><td><code>0</code></td> <td><code>0</code></td> <td>Disabled</td> </tr>
          <tr><td><code>1</code></td> <td><code>0</code></td> <td>Even parity</td> </tr>
          <tr><td><code>1</code></td> <td><code>1</code></td> <td>Odd parity</td> </tr>
          </tbody></table></td></tr>
    <tr><td>3</td>
      <td><code>USBS0</code></td><td>Stop bits: 0 → 1 stop bit; 1 → 2 stop bits.</td></tr>
    <tr><td>2</td>
      <td><code>UCSZ01</code></td><td>Character size bit 1.</td></tr>
    <tr><td>1</td>
      <td><code>UCSZ00</code></td>
      <td>Character size bit 0. Combine with <code>UCSZ01</code> and <code>UCSZ02</code>.
        <table cellspacing="0" cellpadding="3" border="1">
          <tbody><tr>
            <td><code>UCSZ02</code></td> <td><code>UCSZ01</code></td> <td><code>UCSZ00</code></td> <td>Character size</td> </tr>
          <tr><td><code>0</code></td>      <td><code>0</code></td>      <td><code>0</code></td>      <td>5 bits</td>          </tr>
          <tr><td><code>0</code></td>      <td><code>0</code></td>      <td><code>1</code></td>      <td>6 bits</td>         </tr>
          <tr><td><code>0</code></td>      <td><code>1</code></td>      <td><code>0</code></td>      <td>7 bits</td>         </tr>
          <tr><td><code>0</code></td>      <td><code>1</code></td>      <td><code>1</code></td>      <td>8 bits</td>         </tr>
          <tr><td><code>1</code></td>      <td><code>1</code></td>      <td><code>1</code></td>      <td>9 bits</td>         </tr>
          </tbody></table></td></tr>
    <tr><td>0</td>
      <td><code>UCPOL0</code></td><td>Clock polarity.
        <table cellspacing="0" cellpadding="3" border="1">
          <tbody><tr>
            <td><code>UCPOL0</code></td> <td>Output to TxD1 pin</td> <td>Input sampled on RxD1 pin</td> </tr>
          <tr><td><code>0</code></td>      <td>Rising edge</td>        <td>Falling edge</td>              </tr>
          <tr><td><code>1</code></td>      <td>Falling edge</td>       <td>Rising edge</td>               </tr>
          </tbody></table></td></tr>
</table>

<br />
<h3>USART Baud Rate Registers (UBRR0L and UBRR0H)</h3>
A two-byte (16 bit) register which is used to define the baud rate.

<h6 style="font-size:11px;">Note: Here, F_CPU is 16MHz (16000000UL) and BAUD any of the following 300, 600, 1200, 2400, 4800, 9600, 14400, 19200, 38400, 57600, or 115200</h6>

<table>
	<tr><td>Mode</td><td>Equation</td></tr>
    <tr><td>Async normal</td>
      <td><code>UBRR0 = (F_CPU/16/BAUD) - 1</code></td></tr>
    <tr><td>Async double speed</td>
      <td><code>UBRR0 = (F_CPU/8/BAUD) - 1</code></td></tr>
    <tr><td>Sync master mode</td>
      <td><code>UBRR0 = (F_CPU/2/BAUD) - 1</code></td></tr>
</table>

<br />
<h2 id="week9">Week 9: Debouncing; Timers; Interrupts</h2>
<h3>Topic 1</h3>

<br />
<h2 id="week10">Week 10: </h2>
<h3>Topic 1</h3>

<br />
<h2 id="week11">Week 11: </h2>
<h3>Topic 1</h3>

<br />
<h2 id="week12">Week 12</h2>
<h3>Topic 1</h3>

<br />
<h2 id="week13">Week 13: </h2>
<h3>Topic 1</h3>
