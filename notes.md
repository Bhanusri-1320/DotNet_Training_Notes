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
## Note: Class is a user defined type/ a data type

- #### Copy Constructor:
     - If we want to create multiple instances with the same value then we use these copy constructors.
     - in copy constructor the constructor takes same class as a paramter to it.
     - If we want to pass the same value to the constructor instaed of passing the value manually
     - A copy constructor is useful when you want to create a new object that has the same values as an existing objec
```c#
     using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FirstProject
{
     class CopyConDemo
    {
        int x;
        public CopyConDemo(int i) // parameterzed con
        {
            x = i;
        }
        public CopyConDemo(CopyConDemo obj) // copy cons
        {
            x=obj.x;
        }
        public void Display()
        {
            Console.WriteLine("Value of x is: " + x);
        }
        static void Main(string[] args)
        {
            CopyConDemo c1 = new CopyConDemo(10);
            c1.Display();
            CopyConDemo c2= new CopyConDemo(c1);
            c2.Display();
        }
    }
} 
// output: 
Value of x is: 10
Value of x is: 10
```

- #### Static Constructor:
      -  If a constructor is explicitly declared by using static modifier we call that as static con. All the con we have defined till now are non-static or instance con.
      - When we difine a static con explictly even though after compilation a public con is going to be defined implictly by the complier.
      - Static con are also defined implicitly only when we have any static vars other wise we need to define them explictly.
      - ![alt text](image-1.png)
      - ![alt text](image-2.png)
      - static con are responsible for initializing static vars and these are first to execute under any class.
      - static con are never explictly called they are implictly called
      - non-static con are must be called explictly no change for implicit calling means when we create instance to that class then the con is called
      - but when we have static con we didn't call it or create an instance when we run it will only called implictly
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FirstProject
{
     class StaticConDemo
    {
        static StaticConDemo()
        {
            Console.WriteLine("Static con is executed.");
        }
        static void Main()
        {
        }
    }
}
//output: Static con is executed.
```
   - and they are first to execute means

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FirstProject
{
     class StaticConDemo
    {
        static StaticConDemo()
        {
            Console.WriteLine("Static con is executed.");
        }
        static void Main()
        {
            Console.WriteLine("Main method is executed!");
        }
    }
}
// output: 
Static con is executed.
Main method is executed!

```

- static on can't be parameterized so overloading of static con is not possible. coz they are implicitly called when they are implictly called we will not have chance to call them explictly so we can't pass parameters.

- ### Why constructors are needed in a class:
    -  ![alt text](image-3.png)
    - we nedd to con to create instance to the class but when we have implicit con to create instance why we need explicit con.
    - so implicit con will initialize the vars with default values or provided value only we want to assign diff values to the var we will use explicit con.
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FirstProject
{
     class First
    {
        int x = 100;
        static void Main()
        {
            First f1= new First();
            First f2= new First();
            First f3 = new First();
            Console.WriteLine(f1.x +" "+ f2.x +" " + f3.x);
        }

    }
}
// output: 100 100 100
```
- ![alt text](image-4.png)
- ![alt text](image-5.png)
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FirstProject
{
    class First
    {
        public int x = 100;
    }

    class Second {
        public int x;
        public Second(int x)
        {
            this.x = x;
        }
    }
    class TestCases
    {
        static void Main()
        {
            First f1= new First();
            First f2= new First();
            First f3 = new First();
            Console.WriteLine(f1.x +" "+ f2.x +" " + f3.x);

            Second s1 = new Second(10);
            Second s2 = new Second(20);
            Second s3 = new Second(30);
            Console.WriteLine(s1.x + " " + s2.x + " " + s3.x);

        }

    }
   
}
// output:
100 100 100
10 20 30
```
- ![alt text](image-6.png)
- ### Static vs Non-static con:
   - If a con is explictly decalred by using static modifier we call that con as static con where as rest of other are non static
   - con are responsible for initializing the fileds/var of a class, static fileds are initialized by static con and non-static con are initialized by non static con
   - if we have two var in a class like one is static and other is non static
   - then static var is initialized by static con and non static are initialized by non static con
   - static cons are implictly called
   - non static con must be explictly called
   - static con executes immediately once the execution of a class starts and more over it's the first block of code to run under a class. where as non static con executes only after creating instance of the class
   - static con are called once but non static con will be called every time an instance is created
  - we can also initialize the static vars in non static con  but non static vars can't be initialized in static con
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FirstProject
{
     class ConDemo
    {
        int x;// initialized by non static con 
        static int y; // initialized by static con
        static ConDemo()
        {
            // we can't initialize x here it will throw error
            Console.WriteLine("Static con");
        }
        public ConDemo()
        {
            y = 100;
            Console.WriteLine("non- static con");
        }
        static void Main()
        {
            ConDemo c1=new ConDemo();
            Console.WriteLine(y);
        }
    }
}
// output: 
Static con
non- static con
100
```
- Non-static con can be parameterized but static is parameter less
- non-static con can be overloaded but static can't be
-  Static class can only have static members i will not have any non static members
- so in non-static class if the programmer doesn't write any con then it will create an implict non static con
- static con is implicitly defined only when the class conatins any static fileds


-  ### Difference b/w Varaiable Instance and References:
       - ##  Variable of a class:
       - ## Instance of a class:
       - ## Reference of a class:
    - ## Class: Its a user-define type:
       - Class is a blueprint of  an object
       - ex: string is a class but we call it a data type
    - ## Var Instance:
```c#
namespace TestPrj
{
    class First
    {
        int x = 100;
        static void Main(string[] args)
        {
            Console.WriteLine(x);
        }
    }
}
// here we will get an error of x can't be accessed coz, x is a non static var and we are trying to access it in the static method Main 
// so we can't access the non static vars in static method we need to create the instace then access
```
- Instance of a class can be created only by a new keyword
```c#

namespace TestPrj
{
    class First
    {
        int x = 100;
        static void Main(string[] args)
        {
            First f; // f is variable of class
            f=new First(); // f is instance of a class
            Console.WriteLine(f.x);
        }
    }
}
```

- ![alt text](image-7.png)

- how many instances we create that many times a new memory will be allocated
- means how many instances we create that many copies we will have
- ![alt text](image-8.png)
- ![alt text](image-11.png)

      - ## Var Reference:
         - If we assign one instance to another then that will have the same memory and will be pointing to the saem memory location
         - ```c#
              First f1=new First(); // f is instance of a class
             First f2 = f1;
           ```
         - f1 and f2 will point to the same memory location and f2 is a pointer to f1
![alt text](image-9.png)
![alt text](image-10.png)
         - Reference of a class is called pointer tot the instance and every modification we perform on the members using instance reflect when we access those members thru reference and vice-versa
- ### Access Specifiers: 19-05-25
    -It's a special kind of modifiers using which we can define the scope of a type and it's member
    - who can controll and who can access are defined by this
    - c# supports 5 access sepcifiers
      - # Private - accessable only within the class it is defined nd child class can't even access it
      - # Internal - can be accessed inside the prj with child or non child but not outside the prj
      - # Protected - Can be accessable to child class but not for non child from any where like from another prj but only through child class
      - # Procted internal - is a combination of protected and internal, if any of these 2 is accessable then this will be accessable.
      - # Public - we can call it from any where doesn't have restrictions
    - any member of a class defined with any scope is accessable within the class
    - The restrc=ictions will start outside the class
 ```c#
 // Case-1: Consuming members of a class from same class of same prj
       namespace Accessdemo
         {
             public class Program
                {
        private void Test1()
        {
            Console.WriteLine("Private Method.");
        }
        internal void Test2()
        {
            Console.WriteLine("Internal Method.");
        }
        protected void Test3()
        {
            Console.WriteLine("Protected Method.");
        }
        protected internal void Test4()
        {
            Console.WriteLine("Protected Internal Method.s");
        }
        public void Test5()
        {
            Console.WriteLine("Public Method.");
        }
        static void Main()
        {
            Program p=new Program();
            p.Test1();
            p.Test2();
            p.Test3();
            p.Test4();
            p.Test5();

        }
             }
               }
      // output:
      Private Method.
      Internal Method.
      Protected Method.
      Protected Internal Method.s
      Public Method.
```
     
- The restrictions will strart when we go outside the class

```c#

// Case-2: Consuming members of class from child class of same prj

namespace AccessSpecifiersDemo
{
     class Two:Program
    {
        static void Main()
        {
            Two t=new Two();
            t.Test2();
            t.Test3();
            t.Test4();
            t.Test5();
        }
    }
}
// here also we can't access Test() coz its private

```
- Every member of class is by default private
- we can't apply private on a class
- we can only use public and internal on a class we can't  use others
- To access the other class members we can inherit/create instance.
- we can't access protected method in other than child class
```c#
// Case-3: Consuming members of class from non child class(Through instance) of same prj

namespace AccessSpecifiersDemo
{
     class Three
    {
        static void Main()
        {
            Program p=new Program();
            p.Test2();
            p.Test4();
            p.Test5();
        }
    }
}
// here we can't access the protected class
```
- To access the members from diff prj we need to add reference 
- right click on second prj add-> project reference->browse-> select the prj1.exe file
```c#
namespace AccessDemo2
{
    // case-3: consuming memebers from diif prj through child class
    class Four:AccessSpecifiersDemo.Program
    {
        static void Main()
        {
            Four f=new Four();
            f.Test3();
            f.Test4();
            f.Test5();
        }
    }
}
//here we can't access private and internal 
// coz private can't be accessed and internal means only within that project
```
- Protected Intenal -> is a combination of protected and internal, if any of these 2 is accessable then this will be accessable.
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using AccessSpecifiersDemo;

namespace AccessDemo2
{
    // case-4: Consuming the members of a class in other prj and through instance
    class FIve
    {
        static void Main()
        {
           Program p=new Program();
            p.Test5();
        }
    }
}
```

- ![alt text](image-12.png)

- ###  Different Kinds of Variables in a class:
    -  To store values we use  var
    - ## Types of var:
       - ### Non-static/ Instance 
          - Any var that is declared normally like int x=0;
       - ### Static
          - If a var is explicitly Declard with static modifier or else declard under any static block
       - ### Constants
       - ### Readonly
    - static and non static var ex:
```c#
namespace VariablesDemo
{ 
    class Program
    {
        int x;// non static var
        static int y; // static var
        static void Main()
        {
            int z; // static var
        }
    }
}
```

- For static var the memory will be allocated when the program complies
- but for non-static memory will be allocated only when the instance of a class is created 
- ![alt text](image-13.png)
- ![alt text](image-14.png)
- ##### Constant Var:
   - If a var is declared by using the keyword "const" we call it as const vars can't be modified once after their declaration, so it's must to initialize constanr vars at the time of declaration only 
   - const float pi=3.14f;
- ![alt text](image-15.png)
- For static var only one copu will be created
- for non-static depends on instances how many instances we create that many copies
- for const vars only one copy will be created
- ![alt text](image-16.png)
- once the execution starts static and const vars are initialized
```c#
namespace VariablesDemo
{ 
    class Program
    {
        int x;// non static var
        static int y=50; // static var
        const float pi = 3.14f;
        public Program(int x)
        {
            this.x = x;
        }
        static void Main()
        {
            Console.WriteLine(y);
            Console.WriteLine(pi);
            Program p1=new Program(100);
            Program p2=new Program(200);
            Console.WriteLine(p1);
            Console.WriteLine(p2);
            
        }
    }
}
```
- ![alt text](image-17.png)
-  The only diff b/w static and const is static can be modified and const can't be
- #### Readonly var:
    - declared using readonly keyword we call that vars as readonly var and 
    - The behavoir of readonly vars are similar to the instance vars means initialized only after the instance of class is created
    - after initializing the readonly var we can't changes its value
- ![alt text](image-18.png)
```c#
namespace VariablesDemo
{ 
    class Program
    {
        int x;// non static var
        static int y=50; // static var
        const float pi = 3.14f;
        readonly bool flag;
        public Program(int x, bool flag)
        {
            this.x = x;
            this.flag = flag;
        }
        static void Main()
        {
            Console.WriteLine(y);
            Console.WriteLine(pi);
            Program p1=new Program(100,true);
            Program p2=new Program(200,false);
            Console.WriteLine(p1);
            Console.WriteLine(p2);
            
        }
    }
}
// here the flag is created with 2 copies
```
- ![alt text](image-19.png)
- and we can only initlize the readonly var at the time of declaration or through cinstructor other than these we can't
- The only diff b/w readonly and instance is instance var can be modified but not readonly