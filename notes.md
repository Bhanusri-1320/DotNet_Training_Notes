# .Net:
- we don't have any full form for this .net or defination for this .net
- It is a software or product that came from microsoft can be used for developing various kinds of applications.
- ### Categories of applications:
     - Desktop app
     - web app
     - mobile app

- .net has 30+ languages, in this we can choose the language what ever we want
- csharp is an extension of c++
## C sharp:
- c -> c++ -> c sharp
- c sharp is used to develop desktop,mobile and web apps
- ### features:
  - Object oriented: security, reusability
  - platform independent - can run on multiple platforms
  - Language Independent- means csharp can be used in other 30 languages of .net and vice versa.

- ### Visual Studio.Net:
  - It's an IDE provided by microsoft for developing .net application.
  - It's used for developing, concole, windows, web applications.
  - the project comes with a default class program

 ```c#
 using System;
  namespace FirstProject
{
    class Program
    {
        static void Main(string[] args)
        {
        }
    }

}
```
- the namespace is a logical container of types
- it doesn't have a physical existance
- generally we use it for grouping the items
- so if we have 10 classes in our prj and we want to group 5 and 5 sepearte then we can use namespace
- to import a name space we use using namespace_name;
- in solution explorer we have collection of projects
- a project is collection of items(classes,structures, enums, interfaces etc)
- default class program
- we can add n number of classes to our project
- right click on project select add and newitem then it will show you the list of items that a prj can have and select class
- when we create a new class in the same project a new file is created and it will have the same namespace as the program class coz, all classes in a prj have same namespace
- every main method is the entry point.
- ### Constructors in c#:
   - it is a special method present under a class responsible for initializing the vars of that class.
   - the name of a constructure is same as class.
   - it's non-value returining method, it doesnot return anything.
   - if we want to create the instace of a class we should have constructor.
   - It's the responsibility of the programmer to define a constructor if he doesn't then the complier will create a default one.
   - when we create any instance vars in our class thay will get the default values right the implictit constructor will assign the default values to the vars depending on their data types.
   ```c#
   class Test
   {
    int i;
    string s;
    bool b;
    public Test()
    {
        i=0; // Initializing the var
        s=null;
        b=false;
    }
   }
   ```
  - implicitly defined constructors are parameter less and called as default constructors anf they are public.
```c#
  using System;
namespace FirstProject
{
    class Program
    {
        int i;bool b;
        static void Main(string[] args)
        {
            Program p=new Program();
            Console.WriteLine(p.i);
            Console.WriteLine(p.b);
        }
    }

}
// output 0 false
```
```c#
using System;
namespace FirstProject
{
    class Program
    {
        int i;bool b;
        public Program()
        {
            i = 10;
            b = true;
        }
        static void Main(string[] args)
        {
            Program p=new Program();
            Console.WriteLine(p.i);
            Console.WriteLine(p.b);
        }
    }

}
// output: 10 true
```
- when we create instance to the class it will calls the constructor
- #### Types of Constructors:
     - Default or parameter less constructor- doesn't take any parameters
     - Parameterized constructor - will take parameters
     - copy constructor - 
     - static constructor
```c#
namespace FirstProject
{
     class ParameterizedConDemo
    {
        public ParameterizedConDemo(int i)
        {
            Console.WriteLine("Parameterized Constructot is called: " + i);
        }
        static void Main()
        {
            ParameterizedConDemo p = new ParameterizedConDemo(10);
        }
    }
}
```
- ![alt text](image.png)
```c#
namespace FirstProject
{
     class ParameterizedConDemo
    {
        int x;
        public ParameterizedConDemo(int i)
        {
            x = i;
            Console.WriteLine("Parameterized Constructot is called: " + i);
        }
        public void display()
        {
            Console.WriteLine("The value of x is: "+x);
        }
        static void Main()
        {
            ParameterizedConDemo p1 = new ParameterizedConDemo(10);
            ParameterizedConDemo p2 = new ParameterizedConDemo(20);
            p1.display();
            p2.display();

        }
    }
}
// output: 
Parameterized Constructot is called: 10
Parameterized Constructot is called: 20
The value of x is: 10
The value of x is: 20
```

- #### Copy Constructor:
     - If we want to create multiple instances with the same value then we use these copy constructors.
     - in copy constructor the constructor takes same class as a paramter to it.