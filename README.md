# CPP Summary
This reporsitory is just a summary for me to recall some C++ operator and function.

| S/N | Title                                                                                      |
|-----|:------------------------------------------------------------------------------------------:|
|1    |[Namespace](https://github.com/SorinoSSK/CPP-summary#namespace)                             |

## Installing Compiler

## Basic Libraries
### <iostream>
1) std::cout  
The object set an output stream where the output can be displayed on a output device such as a monitor.  
The object prints to the console/ terminal.
2) std::endl  
The object declares the end on the output stream.  
    
E.g. We can use the above to display a message on the console.  
```
#include <iostream>

int main()
{
    std::cout << "Hello World" << std::endl;
}
```  
3) std::cin  
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
4) std::cerr  
The object prints error to the console.  
5) std::clog  
The object prints log messages to the console.  
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
