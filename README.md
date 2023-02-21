# CPP-summary
This reporsitory is just a summary for me to recall some C++ operator and function.

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

## Using Declaration (using)
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
## classes
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

## __attribute__((__packed__))
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

## Scope Resolution Operator (::)
This operator is similar to "." operator in other programming languages but in C++, it is used to access namespace, class or struct.  
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
