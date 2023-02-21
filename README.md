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
std::int x = 10;

int main()
{
}
```
