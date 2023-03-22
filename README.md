# CPP Summary
This reporsitory is just a summary for me to recall some C++ operator and function.

| S/N | Title                                                                                      |
|-----|:------------------------------------------------------------------------------------------:|
|1    |[Namespace](https://github.com/SorinoSSK/CPP-summary#namespace)                             |

## Installing Compiler

## Basic Libraries
### \<iostream\>
**1) std::cout**  
The object set an output stream where the output can be displayed on a output device such as a monitor.  
The object prints to the console/ terminal.  

E.g. We can use the above to display a message on the console.  
```
#include <iostream>

int main()
{
    std::cout << "Hello World" << std::endl;
}
```  
You may too concatenate your output by using "**<<**" to push in data to std::cout
```
int main()
{
    std::string name;
    std::cin >> name;
    std::cout << "Hello World" << name << std::endl;
}
```

**2) std::endl**  
The object declares the end on the output stream. However, you may also use "\n" to declare end of the line.  

```
std::cout << "Test" << std::endl;
std::cout << "Hey" << std::endl;
```
```
std::cout << "Test\n";
std::cout << "Hey"\n";
```

**3) std::cin**  
The object reads data from the terminal.  
```
int main()
{
    std::string name;
    std::string age;
    
    std::cin >> name;
    std::cin >> age;
}
```
However, the following code does the same as the above.
```
int main()
{
    std::string name;
    std::string age;
    
    std::cin >> name >> age;
}   
```
**4) std::getline**  
std::cin do not allow users to enter input with spaces as spaces is similar to breaking out of the input. The problem can be resolved by reading a line rather than a input by using std::getline.
```
std::string name;
std::getline(std::cin, name);
```
**5) std::cerr**  
The object prints error to the console.  
**6) std::clog**  
The object prints log messages to the console.  
**7) std::flush**
The object will hold data from being sent to the terminal immediately.
```
std::cout << "Test" << "Test2" << std::endl << std::flush;
```
**8) std::nothrow**  
The object will prevent any error from being displayed on the console.
```
int * var {new(std::nothrow) int[999999999999999999]};
```
**9) std::exception**  
```
try
{
    // Some work
}
catch(std::exception& ex)
{
    std::cout << ex.what() << std::endl;
}
```
### \<iomanip\>
**1) std::setw()**  
The object will ensure that all data passing through will be in accordance to the width specified. If the number of characters is less than the specified width, spaces will be added.
```
std::cout << std::setw(15) << "Test" << std::setw(8) << "Success" << std::endl;
```
**2) std::right**  
The object will set data to be right justified on console print. Using **std::setw()**, data printed will be right justified by default.
```
std::cout << std::right;
std::cout << std::setw(15) << "Test" << std::setw(8) << "Success" << std::endl;
```
**3) std::left**  
The object will set data to be left justified on console print. Using **std::setw()**, data printed will be right justified by default.
```
std::cout << std::left;
std::cout << std::setw(15) << "Test" << std::setw(8) << "Success" << std::endl;
```
**4) std::internel**  
The object will set data to be right justified but if sign exist, it will be left justified on console print. Using **std::setw()**, data printed will be right justified by default.
```
std::cout << std::internal;
std::cout << std::setw(15) << "Test" << std::setw(8) << "-231.14" << std::endl;
```
**5) std::setfill()**  
The object will add the specified character into the data instead of spaces to make up the width.
```
std::cout << std::left;
std::cout << std::setfill('-');
std::cout << std::setw(15) << "Test" << std::setw(8) << "Success" << std::endl;
```
**6) std::boolalpha**  
The object will convert the data to true or false if they are 1 or 0.
```
std::cout << std::boolalpha;
std::cout << "Test" << 1 << std::endl
```
**7) std::noboolalpha**  
The object will convert data to a non true/false display.
```
std::cout << std::boolalpha;
std::cout << "Test" << true << std::endl
```
**8) std::showpos**  
The object includes the display of "+" for positive number. Negative number have the symbol "-" on display while the positive number does not have its own symbol by default.
```
std::cout << std:showpos;
std::cout << 400 << std::endl;
```
**9) std::noshowpos**  
The object disable the previous setting of "std::showpos".
```
std::cout << std:noshowpos;
std::cout << 400 << std::endl;
```
**10) std::dec, std::hex, std::oct**  
The objects convert numbers to other numbering format such as hexdecimal and octadecimal. However, the objects are unables to convert double var.
```
std::cout << std::dec << 400 << std::endl;
std::cout << std::hex << 400 << std::endl;
std::cout << std::oct << 400 << std::endl;
```
**11) std::uppercase, std::lowercase**  
The objects converts the display to uppercase or lowercase. The function affects all characters, including **a** to **f** of hexadecimal.
```
std::cout << std:uppercase;
std::cout << "hey there" << std::endl;
```
**12) std::scientific**  
The object display numbering format in scientific display.
```
std::cout << std:scientific;
std::cout << 400 << std::endl;
std::cout << 500 << std::endl;
std::cout << 600 << std::endl;
```
**13) std::fixed**  
The object display numbering format in a fixed number of decimal point. 
```
std::cout << std:scientific;
std::cout << 400 << std::endl;
std::cout << 500 << std::endl;
std::cout << 600 << std::endl;
```
**14) unset std::scientific and std::fixed**  
This code will remove the setting of display to fix or scientific.
```
std::cout.unsetf(std::ios::scientific | std::ios::fixed);
```
**15) std::setprecision()**  
The object will determine the precision of values that will be printed (How many decimals point will it be printing).
```
double a = 2.0565664613684685489562666556;

std::cout << std:setprecision(10);
std::cout << a << std::endl;

std::cout << std:setprecision(20);
std::cout << a << std::endl;
```
**16) std::showpoint**  
The object enforces the display of decimal point even though the value printed is an integer.
```
std::cout << std:showpoint;
std::cout << 30 << std::endl;
```
### \<cmath\>
https://en.cppreference.com/w/cpp/header/cmath
## Code structure
### int main()
This is the main function which will be executed first by the compiler
```
int main()
{
    ...
}
```
### return 0; in main function
The return is meant for the operating system (OS) to know when the program has finish executing.
```

int main()
{
    ...
    return 0;
}
```
### Initialising Variables
There are  3 ways to initialise variable  
**1) Using of {}**  
Initialising using **{}** enables the function to work in multiple context.
```
int count{};            //This will initialise count with 0.
int age {4};

int add {count + age};  // This will perform addition before initialising to add.

// Some compiler may not compile this line of code.
int flt {2.9};          // Storing float in an integer, warning will be given.
```
**2) Using of = or functional variable initialisation, ()**  
Initialising using **=** or **()** only allows the function to work on certain/specific context.
```
int count1 = 4;
int age1 = 5;
int add1 = count1 + age1;
int flt1 = 2.9;         // Rounding will occur.

int count2(5);
int age2 (6);
int add2 (count2 + age2);
int flt2(2.9);          // Decimals will be ignored when storing into flt2.

```
### char
The variable char can be stored in two different ways, the 1st as an integer index and the 2nd as the character itself. The following code represents the same thing.
```
char value = 65;
char value{'A'};
```
To read the integer index of the character, we can use the following function **static_cast\<int\>()**.
```
char value{'A'};
std::cout << static_cast<int>(value) <<std::endl;
```
### auto
A keyword that allows the compiler to decide the variable type.
```
auto var1{12};      // Will be intepreted as integer
auto val2{12.0}     // Will be intepreted as double
auto val3{12.0f}    // Will be intepreted as float
auto val4{12.0l}    // Will be intepreted as long double
auto val5{12u}      // Will be intepreted as unsigned
auto val6{12ul}     // Will be intepreted as unsigned long
auto val2{12ll}     // Will be intepreted as long long
```
### division  
1) (floating point)/0 = (+/-)Infinity  
2) 0.0/0.0 = Nan

### static_cast<>  
A function to convert values.
```
static_case<int>(values);   // values will be interpreted as an integer.
```
### Ternary expression
A subtitue expression for if-else statement. The expression below are the same.
```
result = (condition) ? option1 : option2 ;
```
```
if (condition)
{
    result = option1;
}
else
{
    result = option2;
}
```
### size_t  
A representation of some unsigned int for positive numbers [sizes]. A C++ convention rather than using "**unsigned int**" e.g.
```
for (size_t i{}; i<10; i++)
{
    // Some Task
}
```
### Range based for loop
A different way to perform for loop when data size is unknown.
```
int scores [] {2,5,8,2,5,6,9};
int sum {0};

for (int i: scores)
{
    sum += i;
}
```
### cString
A character can be read as a string when it has a proper cString format. E.g. null termination, "**\0**"
```
char message[5] {'H','E','L','L','O',\0};
std::cout << message << std::endl;
```
or
```
char message[6] {'H','E','L','L','O'};
std::cout << message << std::endl;
```
or
```
char message[] {"HELLO"};
std::cout << message << std::endl;
```
### Pointers
Pointer is a variable that stores the address of another variable. The function is useful when **no modification** needs to be made and **only referencing** is required. It is declared with a "**\***".
```
int * i {};         // Stores the address of a variable of int type.
double * x {};      // Stores the address of a variable of double type.

int * y {nullptr};  // Explicitely initialise a null pointer. The above 2 examples do the same.
```
You may insert the "\*" in anyway you like and examples below do the same.
```
int*  i {};
int * i {};
int  *i {};
```
To assign a variable to the pointer, you will have to use the address operator "**&**".
```
int var {100};
int *pt_var {&var};

int var2 {200};
pt_var = &var2;         // Change addresses
*pt_var = 300;          // Stores value into the pointed address

// To read the values stored in var2 and pointed from pt_var, we can do the following
// Dereferencing pointer.
std::cout << *pt_var << std::endl;
```
When a pointer is referenced to an character array, the pointer will store the array of the first character.
```
// This pointer will force the char to be a const char
char * pt_msg {"Hello World!"};         // pt_msg will store the address of H
// If the above declaration fails, you will have to declare it with a const
const char * pt_msg {"Hello World!"};   // this performs the same as above

// However, the behaviour is a little different for character array.
std::cout << p_message << std::endl;    // This will attempt to print the entire string
std::cout << *p_message << std::endl;   // This will print a "H"
```
You may also check if a pointer is a null pointer by using
```
int *var{};
if !(var == nullptr)
{
    // Some task
}
// The following code performs the same as the above.
if (var)
{
    // Some task
}
```
### References
References reference a value from another variable. You can  declare a reference by using "**&**" at the end of the variable type. A reference differ from a pointer as a reference provides a new name for a variable while a pointer stores the address of a variable. 
```
int var {45};
int& var_reference{var};

var_reference = 25;             // var will also be modified to store 25
```
In references, the address of the reference variable is the same as the address of its original variable. ```&var_reference == &var;```
## Operators
### Scope Resolution Operator (::)
This operator is similar to "." operator in other programming languages but in C++, it is used to access "namespace, class, or struct".  
1) Accessing global variable.
```
int x = 10;
int main()
{
    cout << ::x << endl;
}
```
2) Accessing variable of a class
```
class X
{
    public:
        y = 10;
}
int main()
{
    cout << X::y << endl;
}
```
3) Accessing namespace
```
using namespace std;
int main()
{
    std::int x = 10;
}
```
https://stackoverflow.com/questions/11902791/what-is-the-difference-between-and-in-c  
### Arrow operator (->)
This operator is similar to "." operator in other programming languages but in C++, it is used to access "pointer".
```
Foo *foo = new Foo();
foo->(variable) = 10;
foo->(function)();
```
Where 
- (variable): a variable within the class pointed to Foo
- (function): a function within the class pointed to Foo  
https://stackoverflow.com/questions/11902791/what-is-the-difference-between-and-in-c  
### Dot operator (.)
This operator is similar to "." operator in other programming languages but in C++, it is used to access an instances.
```
Foo foo;
foo.(variable) = 10;
foo.(function)();
```
Where
- (variable): a variable within the class Foo
- (function): a function within the class Foo  
https://stackoverflow.com/questions/11902791/what-is-the-difference-between-and-in-c  


### New Operator (new)
The operator represent storage space allocation. Thus, you are declaring that the resources (memory) will be managed by the user when new is declared.  
```Foo* foo1 = new Foo;```  
https://stackoverflow.com/questions/12248703/creating-an-instance-of-class

### Prefix and postfix increment or decrement
```
int items {6};
std::cout << items++ << std::endl;      // this will print 6
std::cout << items << std::endl;        // this will print 7

items = 6;
std::cout << ++items << std::endl;      // this will print 7
```

## Terminology
### Scope
Scope is use as a reference of a domain a variable is in. The existence of scope allows users to declare functions of the same name as long as they reside in a different scope. For instance scope can be divided into 6 different scope type:  
1) Global scope  
The variable is visible throughout the file it is declared in.
2) Namespace scope  
The variable can be visible across different code block such as classes, functions, and more.
3) Local scope  
The variable is visible in the function it is declared in.
4) Class scope  
The variable is visible within the class be it public, private, or protected.
5) Statement scope  
The variable is visible throughout block condition such as "for, if, while, or switch" statement.
6) Function scope  
The variable is visible throughout the function it is declared in.

### POD
POD is an abbrevation for "Plain Old Data" which represent a class without :
1) user defined destructor
2) copy assignment (=)
3) non-static data members that are not a POD
4) user-declared constructors
5) no private data
6) no protected data
7) no virtual base classes
8) no virtual functions

In summary, it is a class that does not store any data. It is a passive entity.
```
struct Point
{
    float x, float y;
}
```
https://stackoverflow.com/questions/30745753/passive-objects-in-c

### Virtual Function (Inheritance)
Virtual functions allows derived classes to replace the implementation provided by the base class. In other words, the newly derived function will override the function within the base class.  
https://isocpp.org/wiki/faq/virtual-functions#:~:text=Non%2D%20virtual%20member%20functions%20are%20resolved%20statically.,(at%20run%2Dtime).

### Pure Virtual Function
Pure Virtual Function are function that must be overridden.
```
class Base {
public:
    void f1();              // not virtual
    virtual void f2();      // virtual, not pure
    virtual void f3() = 0;  // pure virtual
};
Base b; // error: pure virtual f3 not overridden
```

## Declaraction
### Using Declaration (using)
This method allows use of any function, variable, or member at the point it is used. For instance, we would like to use a function of another class within a newly declared class; we could do it in the following way:
```
class X
{
    public:
        void f(int)
        {
            ...;
        }
}
class Y
{
    public:
        using X::f;
}
```
### Declaring instances
C++ provides multiple methods to declare an instances in which each of them provide different benefits.
1) When a class is a POD-type, thus this method allows the initialisation of data when calling the instance of the class. foo1 is a pointer to Foo\*  
``` Foo* foo1 = new Foo();```
2) This method of calling a class is similar to (1) but in this case, the class is not a POD-type. foo1 is a pointer to Foo\*  
```Foo* foo1 = new Foo;```
3) This method of calling a class allows automatic storage (Data of the instance is destroyed when the instance exitted)  
```Foo foo1;```
4) This method copies the class with its initialisation to a new instance and it too allows automatic storage.  
```Foo foo1 = Foo:Foo()```
5) This method is similar to the above but you are initialising a type.  
```Bar* bar1 = new Bar(*new Foo());```
6) This method is similar too (5)  
```Bar* bar1 = new Bar(*new Foo);```
7) Similar to (6)  
```Bar* bar1 = new Bar(Foo::Foo());```
8) This method is invalid.  
```Bar* bar1 = new Bar(Foo foo);```  
Method (5) & (6) may contain memory leak.  
https://stackoverflow.com/questions/12248703/creating-an-instance-of-class
 

## Namespace
Name space is similar to a class but it works similarly to how a file work. To declare a namespace, you could perform it this way:
```
namespace nsTest
{
    class ClassX
    {
        public:
            ...
    }
    void Function(int)
    {
        ...
    }
}
```
## Classes
Classes are declared a little differently for instance:
```
class ClassX
{
    (attribute type):
        ...
    (variable);
    void Functions (variable)
    {
        ...
    }
}
```
Where 
- attribute type: public/ private/ protected
- variable: any variable
- Functions: any function name

## \_\_attribute\_\_((\_\_packed\_\_))
This function is used when memory space is a concern. There are a few instances where memory is of concern,
1) reducing the amount of data used to transmit over a network
2) memory space is limited
3) reading speed of a device  
In summary, the function removes unnecessary memory space that is not used by the variable. (Removes the concept of paging). You may initialise the function in this way:
```
typedef enum __attribute__((__packed__)) _NameX
{
    int a;
    char b;
} NameX;
```
## Variables Storing
### Local scope variable
Variable will be killed when program exits "**{}**"
```
int main (int argc, char **argv)
{
    {
        int local_scope_variable {33};
    }
    return 0;
}
```
## Dynamic memory/ Heap memory
You can allocate a set of memory space to work on by using "**new int**" until you explicitely kill the variable.
```
int *number{nullptr};
number = new int;       // This will dynamically allocate memory
// The following line will work the same as above
int *number1 {new int{67}};

*number = 77;           // This will store a value in the pointed memory

delete number;          // This will release the allocated memory
```
If declared in a local scope, the variable will not be killed after the program exits "**{}**"
```
int main (int argc, char **argv)
{
    {
        int local_scope_variable {33};
        int *number = new int;              // Will not be kill after exiting {}
    }
    return 0;
}
```
Deleting a pointer twice could cause an error in  the program thus it is always a good practice to release and set to null when you have finish using the pointer.
```
int *var {new int{300}};

delete var;
nullptr;
```
Array declaration operates a little differently and you may declare and release it in the following way. However, sizeof() will not work for this dynamic array as it is still a pointer.
```
const int size{10};
double *var {new double[size]};             // the size of the array will have to be a const variable

// Calling from var[index] will return the value instead of an address. E.g.
std::coud << var[1] << std::endl;
std::coud << var[6] << std::endl;

// The following uses pointer arithmatics but it works the same as the above
std::coud << *(var + 1) << std::endl;
std::coud << *(var + 6) << std::endl;

// Release the memory in the following way
delete [] var;
var = nullptr;
```
