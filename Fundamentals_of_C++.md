# Fundamentals of C++

## Module 1 - Introductio to C++

C++ is a modern, powerful language.

- Functional programming
- Procedural programming
- Object oriented programming

Code written in C++ is usually faster than equivalent code written in any other language.

The type safety, which is built into the language, enables developers to write stable code and catch many errors at compile time.

### History of C++

- 1979, Bjarne Stroustrup start to work on "C with classes" in Bell Labs
- 1983, "C with classes" renamed as C++
- 1985, C++ 1.0 released
- 1989, C++ 2.0 released
- 1998, First ISO standard C++ 98 released
- 2003, C++ 3.0 released
- 2011, C++ 11 released (Major revision)
- 2020, C++ 20 released

### Futures of C++

- Object Oriented
- Dynamic Memory Allocation
- Rich Library of functions
- Compiler based
- Portable language

### Why C++

- C++ is an object-oriented programming language
- C++ use multi-paradigm programming approach
- C++ provides the user complete control over memory management

### Comments

- Comments improve the readability of the code and makes the code more clear and understandable
- C++ supports two comment styles
    + Single line comment: Syntax: ```//``` (For eg: ```//This is a single line comment```)
    + Multi line comment: Syntax: ```/*  */``` (For eg: ```/*This is a multi line comment*/```)
    
### Identifiers

- Identidiers are the names given to class, variables and methods
    + Rule 1: Identidiers manes can start with an alphabet, an underscore (_), or a dollar sign and followed by alphabets or numbers
    + Rule 2: Identifiers are case sensitive and have no maximum length
- Valid Examples: `userName`, `user_name`, `_sys_var1`, `$currency`
- Invalid Examples: `1username`, `user name`

## Module 6 - Pointers

### Pointers

- A pointer is a variable that is used to store the address of another variable.
- Like other variables or constants, it has to be declared before using it in the program.
- Syntax for variable declaration: ```data_type *var_name;```
- Example

```C++ 
int *iptr; // pointer to an integer
double *dptr; // pointer to a double
float *fptr; // pointer to a float
char *cptr; // pointer to a character
```

### Using pointers in C++

- We define a pointer variable.
- Assign the address of a variable to a pointer.
- Finally access the value at the address available in the pointer variable.
- This is done by using a unary operator * that returns the value of the variable located at the address specified by its operand.
                    
```C++
#include <iostream>
using namespace std;
int main(){
    int var = 20; // actual variable declaration.
    int *iptr; // pointer variable.
    iptr = &var; // store address of var in pointer variable.
    cout << var << endl; // value 20 will be displayed.
    cout << iptr << endl; // address of var variable will be displayed.
    cout << *iptr << endl; // access the value at the address available in the pointer variable.
    return 0;
}
```

Output

```
20
0x7ffe1d5c6dcc
20
```

### Void *Pointers

- The type void * is said to be a special pointer that can hold an address of any object.
- It indicates that the associated value is an address but the type of the variable at that address is unknown.
- Example:

```C++
double d = 24.5;
void *vptr = &d;
//d can be any type
vptr= = d;
//vptr can be a pointer to any type
```

### Const Pointer

- A pointer can be made constant. It is said to be a const pointer.

```C++
int age = 50;
int* const iptr = &age; //pointer is constant
```

Example:

```C++
int value1 = 5;
int value2 = 6;
int* const ptr = &value1; //the const pointer is initialized to the address of value1
ptr = &value2; // error, because once initialized, a const pointer can not be changed.
ptr = 6; // allowed, ptr points to a non-const int
```
### Double Pointers

- A pointer pointing to another pointer. It is said to be double pinter.

```C++
int age= 50;
int *ptr = &age; // pointer pointing to the type integer;
int **pptr = &ptr; // pointer pointing to another pointer ptr
```

Example:

```C++
int value1 = 5;

int *ptr = &value1;
*ptr = 20; // value1 = 20

int **pptr = &ptr;
**ptr = 30 // value1 = 30
```

### Pros and Cons of Pointers

Pros:
- Direct memory access
- Dynamic memory allocation
- Helps to build complex data structures like a linked list, stack, queues, trees, graphs etc.
Cons:
- Possibilities of segmentation fault due to non-intialization of pointers
- Dynamically allocated memory needs to be explicitly de allocated
- Slower than normal variables

### Dynamic memory allocation

The required size of an array is unpredictable, Dynamic memory allocation provides ways to allocate memory space while executing the program or to free space when it is not required.
- Dynamic memory allocated in the heap
- Dynamic memory has to be de allocated if it is no longer needed, to avoid memory leaks.
- Use void* pointers as generic pointers to point to any data types.
- Operators used in C++ for dynamic memory:
    + new
    + delete

#### ```new``` Operator

- ```new``` operator is used to allocated memory dynamically.

syntax

``` type variable = new type; ```

or

``` type variable = new data_type[10]; ```

Example

```C++
int *ptr = new int(5);
// or
int *arrptr = new int[10];
```

Example

```C++
#include <iostream>
using namespace std;

int main(){
    int *ptr;
    ptr = new int; // allocating memory to the pointer variable ptr.
    cout << "Enter the Value: "<< endl;
    cin >> *ptr;
    cout << "Value entered is "<<*ptr<<endl;
    return 0;
}
```
Output
```
Enter the Value:
20
Value entered is 20
```


