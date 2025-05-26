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

- static con can't be parameterized so overloading of static con is not possible. coz they are implicitly called when they are implictly called we will not have chance to call them explictly so we can't pass parameters.

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
             First f2 = f1; // f2 is the reference
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
       - ### Readonly-  
           - can only initialize at the time of declaration/ constructor
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

## Inheritance:
   - It's a machenism of consuming the members from one class in another class by establishing parent/child relationship b/w the classes.
   - Lets say there is a class and have some properties or memebers in it and i want the same members to be in another class also i can copy and paste those but i will effect the performance by increasing the memory right(called rewrtiing the code)
   - Thats why inheritance is used
   - Inheritance provides resuability
   - one class can have n number of childrens
- ![alt text](image-20.png)
   - Syntax:
   - <modifiers>class<child class>:<parent class>
   - parent class - Base - super class
   - child class - Derived - sub class
- Note: In inheritance child class can consume mebers of it's parent class as if it is the owner of those members(except private members of parents)
   - ### Rules of Inheritance:
   - #### 1. Parent classes constructors must be accessable to child class, otherwise inheritance will not be possible.
      - when we crate istance for child class the con will implictly call the parent con, if parent con is private or don't mention any modifiers means it will not be able to call that con
       - The child class con will mplictly call parent class con if parent has another it will call its parent etc

     ```c# 

            namespace InheritanceProject
             {
                   class class1
                    { 
                    public class1()
                             {
            Console.WriteLine("Class one");
        }
        public void Test1()
        {
            Console.WriteLine("Method1.");
        }
        public void Test2()
        {
            Console.WriteLine("Method2.");
        }
    }
           }




          namespace InheritanceProject
                 {
                  class Class2:class1
                  {
         public Class2()
        {
            Console.WriteLine("class2 ");
        }

        static void Main()
        {
            Class2 c=new Class2();
            c.Test1();
            c.Test2();
        }
                 }
         }
         
         //output:
          Class one
          class2
          Method1.
          Method2.
    ```
   - #### 2. Child class can access parent class members but parent class can never access the child class members.

   - #### 3. We can initialize the parent class var using child class instance.
    ```c#
    class1 p; // p is a varibale of class1
    Class2 c=new Class2(); // c is an instance of class2
    p = c; // initializing parent class var with child class inastance
    ```
    ```c#
    namespace InheritanceProject
          {
    class class1
    { 
        public class1()
        {
            Console.WriteLine("Class one");
        }
        public void Test1()
        {
            Console.WriteLine("Method1.");
        }
        public void Test2()
        {
            Console.WriteLine("Method2.");
        }
    }
         }


         namespace InheritanceProject
          {
     class Class2:class1
    {
        public Class2()
        {
            Console.WriteLine("class2 ");
        }

        static void Main()
        {
            class1 p; // p is a varibale of class1
            Class2 c=new Class2(); // c is an instance of class2
            p = c; //p is a reference initializing parent class with child class inastance
            c.Test1();
            c.Test2();
            p.Test1();
            p.Test2 ();
        }
    }
    }
       // output:
      Class one
      class2
      Method1.
      Method2.
      Method1.
      Method2.
  ```

    - p is the refenrce to the instance so it will not have the seperate memory allocation and p is consuming the memory of c
- ![alt text](image-21.png)
     - here even c and p consuming to same memeory using p we can't access the child class members
- ![alt text](image-22.png)

- ![alt text](image-23.png)

   - #### 4. Every class we define or predeined classes in librabries are all inherited from object class means, object is the parent class of every class 
      - since object is the parent class for every class we can access the members of object class like Four imp members of obj class
           - Equals
           - GetHashcode
           - GetType  -> gives the type of that
           - Tostring
       - Object class is the default Base class for every class in .NET frame work present inside the system namespace
```c#
                     class1 p; // p is a varibale of class1
              Class2 c=new Class2(); // c is an instance of class2
                p = c; //p is a reference initializing parent class with child class inastance
               c.Test1();
               c.Test2();
              c.Test3();
                p.Test1();
           p.Test2 ();

           Object obj=new Object();
               Console.WriteLine(obj.GetType());
              Console.WriteLine(p.GetType());
              Console.WriteLine(c.GetType());
              //output:
              Class one
             class2
            Method1.
            Method2.
            Method 3.
           Method1. 
            Method2.
             System.Object
             InheritanceProject.Class2
            InheritanceProject.Class2
```
- ## Types of Inheritance:
   - No.of child classes a parent class have or vice versa
   - Types:
    - 1. Single
    - 2. Multi-Level
    - 3. Hierarchical
    - 4. Hybrid
    - 5. Multiple
- ![alt text](image-24.png)
     

      - #### 5. In c Sharp we don't have support for multiple inheritance thru classes. what we are provided is only single ingeritenace thru classes
         - means multiple and hybrid are not supported thru classes
         - if it has more than one parent then not supported
         - If the parent class con is parameterized then we need to call the parent class con explictly from the child class con other wise it will throw error
```c#
namespace InheritanceProject
{
    class class1
    { 
        public class1(int i)
        {
            Console.WriteLine("Class one "+i);
        }
        public void Test1()
        {
            Console.WriteLine("Method1.");
        }
        public void Test2()
        {
            Console.WriteLine("Method2.");
        }
    }
}




using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace InheritanceProject
{
     class Class2:class1
    {

        public void Test3()
        {
            Console.WriteLine("Method 3.");
        }
        public Class2(int a):base(a) // explictyl calling the parent con
        {
            Console.WriteLine("class2 ");
        }

        static void Main()
        {
            class1 p; // p is a varibale of class1
            Class2 c=new Class2(10); // c is an instance of class2
            p = c; //p is a reference initializing parent class with child class inastance
        }
    }
}

// output:
Class one 10
class2
```
  - #### 6 In first rule we have learned that child class con will implictly call the parent class con if the parent class con is parameter less and if the parent class con is parameterized then the program has to explictly call the parent class con using base keyword.
       - reference the above code

- ## How to use Inheritence:
      - Entity: which is associated with set of attributes it can be living or non living object
      - When we develop any app it mainly deals with entities
      - ex: Bank app-> customer is entity, school app-> student is the entity and phone -> attributes are its features
      - Step 1:  Identify the entities that are associated with the application we are developing. 
             - Eg: School->students, staff etc are attributes
      - step 2: Identify the attributes of each and every entity
            - ex: student - id, name, address, phone, class , marks, grade
      - so when we have more entities like Teaching staff and non-teaching staff then we will define 3 seperate classes for all 3 right 
      - but these can have some common features so when we define them seperately that causes memory space usage waste 
      - so we can define in one class and access them in child class
      - we use classes for representing entities
    - step 3: Identify the common attributes of each entity and put them in a hierarchial order(re-usability)
    - step 4: Define the class representing the entities that are put in hierarchial order.


## Method Overloading:
   - It's approach of defining multiple methods of same name under a class by changing parameters. by changing type / number / order of parameters
   - public void Test()
   - public void Test(int i)
   - but a change in return type will not be allowed here
   - public string Test() // invalid change in return type in not allowed
```c#
namespace OverLoadProject
{
    class Program
    {
        public void Test()
        {
            Console.WriteLine("1st method...");
        }
        public void Test(int i)
        {
            Console.WriteLine("2nd method..."+i);
        }
        public void Test(string s)
        {
            Console.WriteLine("3rd method..."+s);
        }
        public void Test(string s,int i)
        {
            Console.WriteLine("4th method..." + s+" "+i);
        }
        public void Test( int i,string s)
        {
            Console.WriteLine("4th method..." + i + " " + s);
        }

        static void Main(string[] args)
        {
            Program p=new Program();
            p.Test();
            p.Test(10);
            p.Test("HI");
            p.Test("Hi", 10);
            p.Test(2, "hello");
        }
    }
}
//output:
1st method...
2nd method...10
3rd method...HI
4th method...Hi 10
4th method...2 hello

```
  - ## Why do we overload the methods:
       - method overloading comes under polymerphism
       - polymerphism means when the input chnages the output will also changes
       - in our code also wihtout parameters and with int as input and string as input will give diff outputs but the same method 
       - and accessspecifiers can be diff no need to be same(public/private/protected etc)
       - whenever the input changes the output will automatically changes
- ![alt text](image-25.png)
       - In the above ex the method is saem but when inputs are changing the output is also changing means method overloading
       - Method overloading means a method with multiple behaviour
       - coz if we use diff method names we will get confused and need to remember every method so method overloading helps with this

## Polymorphism:
   - ## Method Overriding:
     - It's an approch of re-implementing a parent classes method under the child class with the same signature.
     - class1
        Test()
    - class2 : class1
       Test()
    - #### Diff b/w overloading and overriding: 
     - #### Method overloading: 
        - we define the multiple methods with same name by changing their parameters.
        - This can be performed either within a class as well as b/w parent child classes also
        - While overloading a parent classess method under the child class, child class doesn't nrequire to take the permission from the parent class.
        - Overloading is all about defining multiple behaviour of parent method under child class.
     - #### Method overriding:
        -  we defince multiple methods with same name and same paramneters.
        - This can be performed only within parent and child class and can never be performed in same class
        - While overriding a parent's method under child class , child class erquires a permission from it's parent class.
        - Overriding is all about changin the behaviour of parent method under child class.

- #### Notes: If we want to overide a perent's method under the child class first that method shoul be declared by using virtual modifier in parent class.
      - public virtual void Test() // this parent class method is giving permission to override this method in child class
      - public override void Test() // child class is overriding the parent method
```c# 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace OverLoadProject
{
     class LoadParent
    {
        public void Show()
        {
            Console.WriteLine("Parent show Method is called");
        }
        public void Test()
        {
            Console.WriteLine("Parent's Test Method is called");
        }
    }

    class LoadChild : LoadParent
    {
        public void Show(int i)
        {
            Console.WriteLine("Child class show method is called..");
        }
        static void Main()
        {
            LoadChild c=new LoadChild();
            c.Show();
            c.Test();
        }
    }
}
// here Test method can't be overrided becayuse it doesn't have any permission to that like not having virtual modifier
```
- 
```c#
 using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace OverLoadProject
{
     class LoadParent
    {
        public void Show()
        {
            Console.WriteLine("Parent show Method is called");
        }
        public virtual void Test()
        {
            Console.WriteLine("Parent's Test Method is called");
        }
    }

    class LoadChild : LoadParent
    {
        public void Show(int i) // overloading
        {
            Console.WriteLine("Child class show method is called..");
        }
        public override void Test() // overriding
        {
            Console.WriteLine("Overriden child method is called");
        }
        static void Main()
        {
            LoadChild c=new LoadChild();
            c.Show();
            c.Test();
        }
    }
}
// output:
Parent show Method is called
Overriden child method is called
``` 

- ### Method Hiding/Shadowing:
   - Is an approach of reimplementing a parent classes method under the child class exactly with same name and signature
   - In method overriding child class re-implements it's parent class methods which are declared as virtual, where as in this case child class can re-implement any parent's method even the method is not declared as virtual.
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace OverLoadProject
{
     class Parentclass
    {
        public virtual void Test1()
        {
            Console.WriteLine("Method Test1 from parent class");
        }
        public void Test2() // not virtual can't override
        {
            Console.WriteLine("Method Test2 from parent class");
        }
    }
    class ChildClass : Parentclass
    {
        public override void Test1() { // overriding
            Console.WriteLine("Method Test1 from child class"); 
        }
        //method hiding on non virtual method if we want to change the behaviour

        public new void Test2() // method hiding/shadowing
        {
            Console.WriteLine("Method Test2 from child class");
        }
        static void Main()
        {
            ChildClass c=new ChildClass();
            c.Test1();
            c.Test2();
        }
    }
}
//output:
Method Test1 from child class
Method Test2 from child class
```
   - we can re-implement a parent classes method under child class using 2 approaches:
      1. Method Overriding
      2. Method Hiding/shadowing
    - To call parent methods from child class after re-implementing the classes
    - 1. After re-implementing the parent classes method under child class if we want to use the parent class methods we can create instance for parent class and call with that instance
    - ```c# 
          static void Main()
         {
      ChildClass c=new ChildClass();
      Parentclass p=new Parentclass();
      p.Test1();  // parent class method will be called
      p.Test2();
      c.Test1();
      c.Test2();
       }
      ```
      - 2. By using the base keyword also we can call the parent's method from child class after reimplementing.but keywords like this and base can't be used from static blocks.

```c#
             namespace OverLoadProject
             {
               class Parentclass
                  {
                        public virtual void Test1()
                           {
                       Console.WriteLine("Method Test1 from parent class");
                          }
        public void Test2() // not virtual can't override
        {
            Console.WriteLine("Method Test2 from parent class");
        }
                }
    class ChildClass : Parentclass
    {
        public override void Test1() { // overriding
            Console.WriteLine("Method Test1 from child class"); 
        }
        //method hiding on non virtual method if we want to change the behaviour

        public new void Test2() // method hiding/shadowing
        {
            Console.WriteLine("Method Test2 from child class");
        }
        public void ParentTest1()
        {
            base.Test1();
        }
        public void ParentTest2()
        {
            base.Test2();
        }
        static void Main()
        {
            ChildClass c=new ChildClass();
            //Parentclass p=new Parentclass();
            //p.Test1();
            //p.Test2();
            c.Test1();
            c.Test2();
            c.ParentTest1();
            c.ParentTest2();
        }
    }
}
// since we can't use base kw in static block we wrote another method to call parent methods
```
   - Diff b/w overriding and hiding:
       - when we create refernce of parent class with child instance with parent class instance we can't call child class memebers but overriden members can be called
       - so hiding methods can't be called in child with parent instance but overriden members can be called
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace OverLoadProject
{
     class Parentclass
    {
        public virtual void Test1()
        {
            Console.WriteLine("Method Test1 from parent class");
        }
        public void Test2() // not virtual can't override
        {
            Console.WriteLine("Method Test2 from parent class");
        }
    }
    class ChildClass : Parentclass
    {
        public override void Test1() { // overriding
            Console.WriteLine("Method Test1 from child class"); 
        }
        //method hiding on non virtual method if we want to change the behaviour

        public new void Test2() // method hiding/shadowing
        {
            Console.WriteLine("Method Test2 from child class");
        }
        public void ParentTest1()
        {
            base.Test1();
        }
        public void ParentTest2()
        {
            base.Test2();
        }
        static void Main()
        {
            ChildClass c=new ChildClass();
            Parentclass p = c;
            Parentclass p1=new Parentclass();
            p1.Test1(); // classs the parent class Test1 coz it is not initialized by child class instance
            p.Test1(); // call child class method coz overriden
            p.Test2(); // calls parent class method coz hiding
            c.Test1();
            c.Test2();
            c.ParentTest1();
            c.ParentTest2();
        }
    }
}
// output:
Method Test1 from parent class
Method Test1 from child class
Method Test2 from parent class
Method Test1 from child class
Method Test2 from child class
Method Test1 from parent class
Method Test2 from parent class
```
- ## Operator Overloading:
    - Method overloading is an approach of defining multiple behavoir to a method and those behaviours will vary based on the paramters of the method
![alt text](image-26.png)
   - Operator overloading is an approach of defining multiple behaviours to an operator and those behaviours will vary based on the operand types b/w which the operator is used.
   - ex:  -> + is an addition when used b/w 2 numbers operands
          -> + is a concatenation operator when used b/w 2 strings operands
        Num + Num => Addition
        String + String => COncatenation
![alt text](image-27.png)
![alt text](image-28.png)
![alt text](image-29.png)
   - If we want to define our own operator syntax
![alt text](image-30.png)
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace OverLoadProject
{
     class Matrix
    {
        int a,b, c, d;
        public Matrix(int a,int b,int c, int d)
        {
            this.a= a; this.b = b;
            this.c= c; this.d= d;
        }
        public static Matrix operator +(Matrix a, Matrix b)
        {
            Matrix obj = new Matrix(a.a + b.a, a.b + b.b, a.c + b.c, a.d + b.d);
            return obj;
        }
    }

    class TestMatrix
    {
        static void Main(string[] args)
        {
            Matrix m1 = new Matrix(1,2,3,4);
            Matrix m2 = new Matrix(10, 8, 6, 4);
            Matrix m3 = m1 + m2;
            Console.WriteLine(m3);
        }
    }
}
// output:
OverLoadProject.Matrix
```
- here it is printing the class name bacause of writeLine method
- writeline is an overloaded method if the input is int it will give some o/p if i/p is obj then it will behave like 
- ![alt text](image-31.png)
- so when the input is object it will gives the type
- we can override the ToString method here coz, its from object class which is a super class of every class
- by overriding the ToString class we can and an send whater output we wnat i,e we can change the behaviour
- after overriding the ToString method:
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace OverLoadProject
{
     class Matrix:Object
    {
        int a,b, c, d;
        public Matrix(int a,int b,int c, int d)
        {
            this.a= a; this.b = b;
            this.c= c; this.d= d;
        }
        public static Matrix operator +(Matrix a, Matrix b)
        {
            Matrix obj = new Matrix(a.a + b.a, a.b + b.b, a.c + b.c, a.d + b.d);
            return obj;
        }
        public override string ToString()
        {
            return a+ " "+b+"\n"+c+" "+d+"\n";
        }
    }

    class TestMatrix
    {
        static void Main(string[] args)
        {
            Matrix m1 = new Matrix(1,2,3,4);
            Matrix m2 = new Matrix(10, 8, 6, 4);
            Matrix m3 = m1 + m2;
            Console.WriteLine(m1);
            Console.WriteLine(m2);
            Console.WriteLine(m3);
        }
    }
}
// output:
1 2
3 4

10 8
6 4

11 10
9 8
```

## Abstract classes  and Abstract Methods:
   - ##### Abstract Methods:
   - A method without any method body is know as an abstract method, what the method constains is only declaration of the method.
   - eg: public abstract void Add(int x,int y); // abstract method
   - public void Add(int x,int y){} // non-abstarct method
   - if a class contains any abstarct methods that class should be abstract class
   - eg: abstract class Math
   {
    public abstarct void Add(int x,int y);
   }
   - If a method is declared as abstarct under any class then the child class of thet class is responsible for implementing the method.
   - The concept of abstarct methods will be nearly similar to the concept of Method overriding.
   - in method overriding:
- ![alt text](image-33.png)
   - Abstract methods:
- ![alt text](image-34.png)
   - ##### Abstract Class:
      - an abstarct class can constain abstract methods and non-abstarct methods
      - child class of abstract class:
      - should implement the all abstract methods in parent class then only it can access the non-abstract methods.
      - A class under which we define abstract methods is known as an abstract class.
- Note: To deine a method or class as abstract we require to use the abstract keyword on them.
      - To run abstarct class we need to create a child class implementing it and then we have to run it
       - we can't run the abstarct class directly.
```c#
namespace AbstractProject
{
    abstract class AbsParent
    { 
        public void Add(int x, int y) {
            Console.WriteLine(x+y);
        }
        public void sub(int x,int y)
        {
             Console.WriteLine(x-y);
        }
        public abstract void Mul(int x, int y);
        public abstract void Div(int x, int y);

    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace AbstractProject
{
     class AbsChild:AbsParent
    {
        public override void Mul(int x, int y)
        {
            Console.WriteLine(x * y);
        }
        public override void Div(int x, int y)
        {
            Console.WriteLine(x / y);
        }
        static void Main(string[] args)
        {
            AbsChild c=new AbsChild();
          AbsParent p = c;
          c.Mul(1, 2);
          c.Div(1, 2);
          p.Add(1, 2);
          p.sub(3, 1);
        }
    }
}
```

- For abstarct classes we can't create instance and but we can create the reference with child class instance
- AbsChild c=new AbsChild();
- AbsParent p=c; // is allowed
- AbsParent p=new AbsParent; // is not possible
- only with refernce of parent class created with instance of child class will call the overrided child class


- ## Working with Abstract class and method in our application:
    - Abstract Method: a method with out any method body is known as abstract method.
    - Abstract class: a class which constains both abstract and non-abstract methods.
    - eg: Entities: Rectangle, Circle, Triangle, Cone
    - Attributes of each entity:
    - Rectangle: width, length
    - Circle: Radius, pi
    - Traingle: height, width
    - cone: Radius, Height, pi
    - identify the common attributes
    - common attributes are : width, height, radius, pi
    - define a class with common attributes
    - by defining the common attributes in parent class we can access them in child class and lets say i want to calculate area for each element then i can't write the method implementation in the parent class coz the formula to calculate the area is not same for every elemnt
    - so we define an abstarct method in parent and we can override the method and deine the implementation in its parent class
    - example of abstraction:
```c#
namespace AbstractImplementation
{
  public abstract class Figure // definignthe common attributes in the class and making it as parent class
    {
        public double Width, Height, Radius;
        public const float Pi = 3.14f;
        public abstract double GetArea();
    }
    public class Rectangle : Figure
    {
        public Rectangle(double Width, double Height)
        {
            this.Width = Width;
            this.Height = Height;
        }
        public override double GetArea()
        {
            return Width * Height;
        }
    }

    public class Circle : Figure {
        public Circle(double Radius)
        {
            this.Radius = Radius;
        }
        public override double GetArea()
        {
            return Radius* Radius * Pi;
        }
    }

    class TestFigures
    {
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle(12.67,20.88);
            Circle c = new Circle(5.12);
            Console.WriteLine(r.GetArea());
            Console.WriteLine(c.GetArea());

        }
    }

}
// output:
264.5496
82.31321875
```

## Interfaces in C#:
   - an interface is user defined datatype similir to class 
   - class  is a user defined datatype
   - Diff class and Interfaces:
      - Class: can only conatin methods with method body / Non-abstarct methods only
      - Abstract class- conatins both abstract and non-abstract methods
      - Interface: constains only abstarct methods/ only methods without method body
   - Note: Every abstarct method of an interface should be implemented  by the child class of the interface
   - a class can also have an interface as parent
   - Generally a class implemts from its parent class to consume the memebrs but a class inherits the interfaces to implement the members of parent.
   - Note: A class can inherit from a class and interface at a time.
   - defining an interface vs class
- ![alt text](image-35.png)
   - The default scope of members if an interface is public wheras it's private in case of class.
   -  general way of writing abstarct methods:
   - public abstract void Add(int a,int b);
   - but in interface we don't need to specify public and abstract also we can directly write like void Add(int a,int b)  by default they are public and abstarct
   - We can't declare any fields/vars under an interface.
   - If required an interface can inherit from another interface
```c#
namespace InterfaceProject
{
    interface ITestInterface1
    {
        int x;// ❌ not allowed
        void Add(int a, int b);
    }
    interface ITestInterface2 : ITestInterface1
    {
        void sub(int a, int b);
    }
}
```
   - Every member of an interface should implement under the child class of the interface with out fail, but while implementing we don't require to use override modifier just like we have done in case of abstarct class.
   - whule overriding the abstarct methods of interfaces we don't need write override and must add public to it other wise it is considered as private
   - we can implemnt using public like blow
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace InterfaceProject
{
    interface ITestInterface1
    {
        void Add(int a, int b);
    }
    interface ITestInterface2 : ITestInterface1
    {
        void sub(int a, int b);
    }

    class ImplementationCLass : ITestInterface1
    { 
     public void Add(int a,int b)
        {

        }
    }
}
```
 - we can also implement like the other way without using public 
```c#
  void ITestInterface1.Add(int a, int b)
  {
     
  }
  ```
    - example of implemnting the interfaces
  ```c#
  namespace InterfaceProject
{
    interface ITestInterface1
    {
        void Add(int a, int b);
    }
    interface ITestInterface2 : ITestInterface1
    {
        void Sub(int a, int b);
    }

    class ImplementationCLass : ITestInterface2
    {
         public void Add(int a, int b) // one way of implementing using public
        {
            Console.WriteLine(a+b);
        }

      public  void Sub(int a, int b)
        {
            Console.WriteLine(a - b);
        }
        static void Main(string[] args)
        {
            ImplementationCLass obj = new ImplementationCLass();
            obj.Add(1, 2);
            obj.Sub(10, 2);
        }

    }
}
```
  - we can't create instance of an interface but we can create the reference
```c#
             ImplementationCLass obj = new ImplementationCLass();
             ITestInterface2 i=obj; // creating refernce of an interface
```
- ![alt text](image-36.png)

## Multiple Inheritance with Interface:
- ![alt text](image-37.png)
   - multiple inheritance is not supported thur class but can be implemented with interfaces
- ![alt text](image-38.png)
   - A class can have one immediate parent but a class can have multiple interfaces
   - Why classes can't support multiple inheritance
   - coz if a class inherits from 2 classes and if they have same method with same name and signature then the ambiguity problem will come
- ![alt text](image-39.png)
   - in Interfaces the methods are not giving for consuming but telling to implement
   - in class we can consume the parent class method in interface we have to implement it thats why interfaces support multiple inheritance
```c#

namespace InterfaceProject
{

    interface Interface1
    {
        void Test();
    }
    interface Interface2
    {
        void Test();
    }
    class MultipleInheritanceTest : Interface1, Interface2
    {
        public void Test() {
            Console.WriteLine("Inerface method implemented in child class ");
        }
        static void Main(string[] args)
        {
            MultipleInheritanceTest obj=new MultipleInheritanceTest();
            obj.Test();
        }
    }
}
```
   - even if we have the same method name and signature in both 2 interfaces we will implemet it only once that's how we implement multiple inheritance in interfaces
   - Other way to implement the multiple inheritance is:
   - we can implement two seperate methods also with interface name and create the reference of interface and assign the insatnce of child class
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace InterfaceProject
{

    interface Interface1
    {
        void Test();
        void Show();
    }
    interface Interface2
    {
        void Test();
        void Show();

    }
    class MultipleInheritanceTest : Interface1, Interface2
    {
        public void Test() {
            Console.WriteLine("Inerfaces method implemented in child class ");
        }
        void Interface1.Show()
        {
            Console.WriteLine("declared in Interface1");
        }
        void Interface2.Show()
        {
            Console.WriteLine("declared in Interface2");
        }
        static void Main(string[] args)
        {
            MultipleInheritanceTest m=new MultipleInheritanceTest();
            m.Test();
            Interface1 i1=m;
            Interface2 i2=m;
            i1.Show();
            i2.Show();
        }
    }
}
// output:
Inerfaces method implemented in child class
declared in Interface1
declared in Interface2
```


## Structures in C#:
  - Class is a user defined type
  - structures are also user defined type
  - structures in c# can conatain most of the members what a class can contain like Fileds, Methods, constructors, properties etc.
  - Defining structure:

  <modifier> struct <Name>
  {
    - Define members here
  }
  - writing a structure:
```c#
  using System;
namespace StructProject
{
    struct MyStruct
    { 
        public void Display()
        {
            Console.WriteLine("Method in a structure.");
        }
        static void Main(string[] args)
        {
            MyStruct m1=new MyStruct();
            m1.Display();
        }
    }
}
// output: Method in a structure.
```

- ### Diff b/w class and Structure:

   - 1. Class is a reference type  and structure is a value type
   - 2. for class the memory will be allocatred in Managed Heap but for struct the memory will be allocated in stack
   - 3. We use classes for representing an entity with larger vloume of data and struct for smaller valoume of data.
- ![alt text](image-41.png)
   - 4. In case of class "new" kw is mandatory for creating the instance wheas in case of a structure it is only optional.
```c#
 static void Main(string[] args)
 {
     MyStruct m1;
     m1.Display();
 }
 ```
   - like above also it will give the same output but when we initialize any value like
   int x=10 at trhat we will get an error 
   - 5. Fields of a class xan be initialized at the time of declaration whereas it's not possible with fields in structures
   - we either have to initialize it with the help of constructor
```c#
using System;
namespace StructProject
{
    struct MyStruct
    {
        int x=100; // will throw error here
        public void Display()
        {
            Console.WriteLine("Method in a structure.  "+x);
        }
        static void Main(string[] args)
        {
            MyStruct m1=new MyStruct();
            m1.Display();
        }
    }
}
```
  - we can't initialize like int =10;
  - but we can initialize after creating the instacne like
  - MyStruct m1=new MyStruct();
    m1.x=10;
    m1.Display();
- ![alt text](image-42.png)
- ![alt text](image-43.png)
- ![alt text](image-44.png)
- ![alt text](image-45.png)

## Enumeration or Enum Types:
  - A set of named constant values
  - a enum is a user defined data type, so it always better to define an enum directly under the namespace, but it is also possible to define a Enum under aclass or atructure also.
  - enums will come under value type category
  - <modifiers> enum <Name>
  {
    - List of named constant values
  }
  -  ex: we want to user to select only the options that we provided like when we ask the user to select a week day but the user can select any any but we want them to select only mon-fri so we will define an enum with the values
- ![alt text](image-46.png)
- we can also access like  Days d=0; // Monday
 - Days d= (Days)3 // Thursday
```c#
namespace StructProject
{
    public enum Days
    { 
        Monday, Tuesday, Wednesday,Thursday, Friday
    }
    class TestClass
    {
        static void Main(string[] args)
        {
            //Console.BackgroundColor = ConsoleColor.Green; // 
            Console.WriteLine("Hello world");
            Days d=Days.Tuesday;
            Console.WriteLine(d);
            Console.WriteLine((int)d);
            Days d1=(Days)4; // Friday
        }
    }
}
```

  - we can also assign them int value so that we can access them with int value
-  ![alt text](image-47.png)
  - Lets say we want to change that index like by default index starts from 0 if we want to change we can chane also like this
```c#
namespace StructProject
{
    public enum Days
    { 
        Monday=1, Tuesday, Wednesday,Thursday, Friday
    }
    class TestClass
    {
        static void Main(string[] args)
        {
            //Console.BackgroundColor = ConsoleColor.Green; // 
            Console.WriteLine("Hello world");
            Days d1 = (Days)3;
            Days d=Days.Tuesday;
            Console.WriteLine(d +" "+ d1);
            Console.WriteLine((int)d);
        }
    }
}
// output:
Hello world
Tuesday Wednesday
2
```
   - if we give moday=1, the remaining will follow by incrementing
   - we can also give our own indexes like
   - Monday=1, Tuesday=11, Wednesday=21,Thursday=35, Friday // like this
   - we can pick all the values with foreach loop
```c#
namespace StructProject
{
    public enum Days
    { 
        Monday=1, Tuesday, Wednesday,Thursday, Friday
    }
    class TestClass
    {
        static void Main(string[] args)
        {
            //Console.BackgroundColor = ConsoleColor.Green; // 
            //Console.WriteLine("Hello world");
            //Days d1 = (Days)3;
            //Days d=Days.Tuesday;
            //Console.WriteLine(d +" "+ d1);
            //Console.WriteLine((int)d);
            foreach(int i in Enum.GetValues(typeof(Days)))
                Console.WriteLine(i+": "+(Days)i);
            foreach(string s in Enum.GetNames(typeof(Days)))
                Console.WriteLine(s);

        }
    }
}
// output:
1: Monday
2: Tuesday
3: Wednesday
4: Thursday
5: Friday
Monday
Tuesday
Wednesday
Thursday
Friday
```
   - If we want to change the index values from int to byte we can do by telling the type like 
```c#
 public enum Days:byte
    { 
        Monday=1, Tuesday, Wednesday,Thursday, Friday
    }
```

  - default value type is int but it supports byte, short, int, long, uint, ushort, ulong and sbyte

```c#

namespace StructProject
{
    public enum Days:byte
    { 
        Monday=1, Tuesday, Wednesday,Thursday, Friday
    }
    class TestClass
    {
        static void Main(string[] args)
        {
            //Console.BackgroundColor = ConsoleColor.Green; // 
            //Console.WriteLine("Hello world");
            //Days d1 = (Days)3;
            //Days d=Days.Tuesday;
            //Console.WriteLine(d +" "+ d1);
            //Console.WriteLine((int)d);
            foreach(byte i in Enum.GetValues(typeof(Days)))
                Console.WriteLine(i+": "+(Days)i);
            foreach(string s in Enum.GetNames(typeof(Days)))
                Console.WriteLine(s);

        }
    }
}
// output:
1: Monday
2: Tuesday
3: Wednesday
4: Thursday
5: Friday
Monday
Tuesday
Wednesday
Thursday
Friday
```

  - 

-----------------------------------------------------------------------------------------

### Integral Data Type in C#:
  1. byte
Size: 1 byte (8 bits)

Range: 0 to 255

Description: Represents an 8-bit unsigned integer.

Example:

csharp
Copy
Edit
byte a = 100;
2. short
Size: 2 bytes (16 bits)

Range: -32,768 to 32,767

Description: Represents a 16-bit signed integer.

Example:

csharp
Copy
Edit
short b = 15000;
3. int
Size: 4 bytes (32 bits)

Range: -2,147,483,648 to 2,147,483,647

Description: Represents a 32-bit signed integer (commonly used for most integer calculations).

Example:

csharp
Copy
Edit
int c = 100000;
4. long
Size: 8 bytes (64 bits)

Range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807

Description: Represents a 64-bit signed integer.

Example:

csharp
Copy
Edit
long d = 123456789012345;
5. uint
Size: 4 bytes (32 bits)

Range: 0 to 4,294,967,295

Description: Represents a 32-bit unsigned integer (no negative values).

Example:

csharp
Copy
Edit
uint e = 4000000000;
6. ushort
Size: 2 bytes (16 bits)

Range: 0 to 65,535

Description: Represents a 16-bit unsigned integer (no negative values).

Example:

csharp
Copy
Edit
ushort f = 50000;
7. ulong
Size: 8 bytes (64 bits)

Range: 0 to 18,446,744,073,709,551,615

Description: Represents a 64-bit unsigned integer (no negative values).

Example:

csharp
Copy
Edit
ulong g = 123456789012345678;
8. sbyte
Size: 1 byte (8 bits)

Range: -128 to 127

Description: Represents an 8-bit signed integer.

Example:

csharp
Copy
Edit
sbyte h = -100;




--------------------------------------------------------------------------------------

## Properties in C#:

   - Property is a memeber of class using which we can expose values associated with a class to the outside environment.
- ![alt text](image-48.png)
   -  In the above example the circle class is public but we can't access the radius coz  by defailu it is private
- ![alt text](image-49.png)
    - By using c now i can't access radius coz its private and lets say i want to access the radius
    - one way is using public vars means declaring it as public like below
- ![alt text](image-50.png)    
    - and we can even modify the value also
- ![alt text](image-51.png)
    - so anyone can get the value and set the value
    - so it will be a problem coz anyone can get the value and set the value i loose controll on the field/var
    - so i want to give permission only to watch or get the value but not modify it
    - so never declare a value as public we will loose the hold on the value
    - so i only want to get the value that can be done with methods
- ![alt text](image-52.png)
    - If we want to provide only set access to the value, then they can use the setRadius() method
- ![alt text](image-53.png)
    - So the diff b/w declaring the filed as public and writing 2 methods for getting and setting is that 
    - If we want to give only get access we can remove one method and give only get access with get method so we have the control of the field with get ans set methods.
    - we can combine the two get and set access methods and write under a single block claaed as property
    - syntax: 
    <modifier> <type> <Name>
    {
        [get{stmt's}] // Get Accessor
        [set{stmt's}] // set Accessor
    }
    public double RadiusProperty
    {
        get{ // Represents a value  returning method without param
            return radius;
        }
        set // non value returning method with  param
        {
            radius=value
        }
    }
- ![alt text](image-54.png)
  - when we have the same name as variable and property general convention is to use _ in front of the var so that we can use the name for the property
- ![alt text](image-55.png)
   - Lets say we want to restict the values like while setting the value should be grater than theprevoius radius value
   - we can write some conditions ex: bank we want to withdraw the amout that is greater than in our bank 
- ![alt text](image-56.png) 
   - adding the consition is also not posible with the public var so this is a manin adv of property
- ![alt text](image-57.png)

- ### Implementing Properties:

```c#
public class Customer
{
    int _Custid;
    bool _Status;
    String _Cname;
    double _Balance;
    public Customer(int Custid, bool Status, string Cname, double Balance)
    {
        this._Custid = Custid;
        this._Status = Status;
        this._Cname = Cname;
        this._Balance = Balance;
    }
    public int Custid // property will take the value as parameter implictly with type od propoerty like here property is int so value will also be int
        {
          get { return _Custid; }
          set { _Custid = value; }
        }

}


namespace PropertiesProject
{
     class TestCustomer
    {
        static void Main(string[] args)
        {
            Customer obj = new Customer(101, false, "John", 5000.00);
            obj.Custid = 102;
            Console.WriteLine(obj.Custid);
        }
    }
}

// output:
102
```
   - lets say we have this methods and we want to add one condition like if the customer status is inactive they should not be able to modify their name
```c#
public class Customer
{
    int _Custid;
    bool _Status;
    String _Cname;
    double _Balance;
    public Customer(int Custid, bool Status, string Cname, double Balance)
    {
        this._Custid = Custid;
        this._Status = Status;
        this._Cname = Cname;
        this._Balance = Balance;
    }
    public int Custid
    {
        get { return _Custid; }
    }
    public bool Status {
        get { return _Status; }
    }
    public string Cname 
    {
        get { return _Cname; }
        set { _Cname = value; }
    }

    public double Balance
    {
        get { return _Balance; }
        set { _Balance = value; }
    }
}


namespace PropertiesProject
{
     class TestCustomer
    {
        static void Main(string[] args)
        {
            Customer obj = new Customer(101, false, "John", 5000.00);
            Console.WriteLine("Customer Id: "+obj.Custid);
            Console.WriteLine("Customer Name: "+obj.Cname);
            obj.Cname += "Smith";
            Console.WriteLine("Modified Customer Name: " + obj.Cname);
            Console.WriteLine("Customer Balance: "+obj.Balance);
            if(obj.Status==true)
            Console.WriteLine("Customer Status is: Active");
            Console.WriteLine("Customer Status is: In-Active");
        }
    }
}

// output:
Customer Id: 101
Customer Name: John
Modified Customer Name: JohnSmith
Customer Balance: 5000
Customer Status is: In-Active
```
   - If we make the vars public then we will not be able to add the conditions if we want
   - after applying the condition:
```c#
  public string Cname 
{
    get { return _Cname; }
    set {  if(_Status==true)
        _Cname = value; }
}
```
   - If the user is try to perform any withdrawal/deposit then also we have to check if the status is active or not
```c#
 public double Balance
 {
     get { return _Balance; }
     set { 
         if(_Status==true)
           _Balance = value; }
 }
 ```
 ```c#
 public class Customer
{
    int _Custid;
    bool _Status;
    String _Cname;
    double _Balance;
    public Customer(int Custid, bool Status, string Cname, double Balance)
    {
        this._Custid = Custid;
        this._Status = Status;
        this._Cname = Cname;
        this._Balance = Balance;
    }
    public int Custid
    {
        get { return _Custid; }
    }
    public bool Status {
        get { return _Status; }
        set { _Status = value; }
    }
    public string Cname 
    {
        get { return _Cname; }
        set {  if(_Status==true)
            _Cname = value; }
    }

    public double Balance
    {
        get { return _Balance; }
        set { 
            if(_Status==true &  value>=500) 
              _Balance = value; }
    }
}


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace PropertiesProject
{
     class TestCustomer
    {
        static void Main(string[] args)
        {
            Customer obj = new Customer(101, false, "John", 5000.00);
            Console.WriteLine("Customer Id: "+obj.Custid);
            Console.WriteLine("Customer Name: "+obj.Cname);
            obj.Cname += "Smith";
            Console.WriteLine("Modified Customer Name: " + obj.Cname);
            Console.WriteLine("Customer Balance: "+obj.Balance);
            if(obj.Status==true)
            Console.WriteLine("Customer Status is: Active");
            Console.WriteLine("Customer Status is: In-Active");
            obj.Status = true; // activating the account
            obj.Balance =obj.Balance+ 500.00; // Assignment succeds, so blow stms prints new blns
            Console.WriteLine("Modified Balance: "+obj.Balance);
            obj.Balance -= 5200; // Assignment fials, so prints old blns only
            Console.WriteLine("Balance when assignment failed: "+obj.Balance);
        }
    }
}


// output:
Customer Id: 101
Customer Name: John
Modified Customer Name: John
Customer Balance: 5000
Customer Status is: In-Active
Modified Balance: 5500
Balance when assignment failed: 5500
```

   - Lets say we want to add one more attribute called city and we want the user to select only some particlar values then
   - and we want the state name to be modified only by the child class any ine can get the state value but for modifying it has to be a child class
   - In C# we declare the var then we define a property for that var coz, var stores the value and property only provides access to the var.
   - but in latest c# we can even define a property wihtout defining var called Auto-Implemented or Automatic Property take that in the constructor as param
   - in the below example coutry is the automatic property
   - If the value of any var is not going to change means we can directly assign to the propoerty
- ![alt text](image-58.png)
   - and with this auto-implemented prop we can't add conditions
```c#
using PropertiesProject;

public class Customer
{
    int _Custid;
    bool _Status;
    String _Cname,_State;
    double _Balance;
    Cities _City;
    public Customer(int Custid, bool Status, string Cname, double Balance, Cities City, string State, string country)
    {
        this._Custid = Custid;
        this._Status = Status;
        this._Cname = Cname;
        this._Balance = Balance;
        this._City = City;
        this._State = State;
        this.Country=country; // assigning value to property
    }
    public int Custid
    {
        get { return _Custid; }
    }
    public bool Status {
        get { return _Status; }
        set { _Status = value; }
    }
    public string Cname 
    {
        get { return _Cname; }
        set {  if(_Status==true)
            _Cname = value; }
    }

    public double Balance
    {
        get { return _Balance; }
        set { 
            if(_Status==true &  value>=500) 
              _Balance = value; }
    }
     
    public Cities City
    {
        get { return _City; }
        set { 
            if(_Status==true)
            _City = value;
        }
    }
    public string State
    {
        get { return _State; }
        protected set
        {
            if(_Status==true)
                _State = value;
        }
    }
    public string Country // Auto-Implemented or Automatic property
    {
        get;
        set;
    }

}

namespace PropertiesProject
{
     class TestCustomer
    {
        static void Main(string[] args)
        {
            Customer obj = new Customer(101, false, "John", 5000.00, Cities.Hyderabad, "Telangana","India");
            Console.WriteLine("Customer Id: "+obj.Custid);
            Console.WriteLine("Customer Name: "+obj.Cname);
            obj.Cname += "Smith";
            Console.WriteLine("Modified Customer Name: " + obj.Cname);
            Console.WriteLine("Customer Balance: "+obj.Balance);
            if(obj.Status==true)
            Console.WriteLine("Customer Status is: Active");
            Console.WriteLine("Customer Status is: In-Active");
            obj.Status = true; // activating the account
            obj.Balance =obj.Balance+ 500.00; // Assignment succeds, so blow stms prints new blns
            Console.WriteLine("Modified Balance: "+obj.Balance);
            obj.Balance -= 5200; // Assignment fials, so prints old blns only
            Console.WriteLine("Balance when assignment failed: "+obj.Balance);
            Console.WriteLine("Current City: " + obj.City);
            obj.City = Cities.Bengaluru;
            Console.WriteLine("Modified City: "+obj.City);
            Console.WriteLine("Current State: "+obj.State);
            //obj.State = "Karnataka"; // not possible coz, this class is not child class
            Console.WriteLine("Current Cuntry: "+obj.Country);
        }
    }
}


using System;
namespace  PropertiesProject
{ 
    public enum Cities
    {
        Delhi, Mumbai, Chennai, Kolkata, Bengaluru, Hyderabad
    }
}

// output:
Customer Id: 101
Customer Name: John
Modified Customer Name: John
Customer Balance: 5000
Customer Status is: In-Active
Modified Balance: 5500
Balance when assignment failed: 5500
Current City: Hyderabad
Modified City: Bengaluru
Current State: Telangana
Current Cuntry: India
```

------------------------------------------------------------------------------------

## Indexers in c#
  - It a member of class 
  - once we define a index in class the class will start working as a virtual array  
  - When we have a class and there are some vars in the class the class is public so we can create the instance and but we can't access the vars coz they are defaultly private 
  - by using indexers we can access the vars by convering the class into an array can access the vars using index
  - syntax:
  <modifier> <type> this[<parameter List>]
  {
    [get{<stmts>}] // Get Accessor
    [set{<stmts>}] // Set Accessor
  }
  - this is useing tell we are using index on current class
```c#
using System;
namespace IndexerProject
{
    public class Employee
    {
        int Eno;
        double Salary;
        string Ename, Job, Dname, Location;
        public Employee(int Eno, double Salary, String Ename, string Job,string Dname, string Location)
        {
            this.Eno = Eno;
            this.Salary = Salary;
            this.Ename = Ename;
            this.Job = Job;
            this.Dname = Dname;
            this.Location = Location;
        }

        public object this[int index]
        {
            get {
                if(index==0)
                return Eno;
                else if (index == 1)
                 return Salary;
                else if (index == 2)
                    return Ename;
                else if (index == 3)
                    return Job;
                else if (index == 4)
                    return Dname;
                else if (index == 5)
                    return Location;
                return null;
            }

        }

    }
}


namespace IndexersProject
{
     class TestEmployee
    {
        static void Main(string[] args)
        {
            Employee emp = new Employee(1001,20000.00,"Scott","Manager","Sales","Mumbai");
            Console.WriteLine("Eno: "+emp[0]);
            Console.WriteLine("Salary: " + emp[1]);
            Console.WriteLine("Ename: " + emp[2]);
            Console.WriteLine("Job: " + emp[3]);
            Console.WriteLine("Dname: " + emp[4]);
            Console.WriteLine("Location: " + emp[5]);



        }
    }
}

// output:
Eno: 1001
Salary: 20000
Ename: Scott
Job: Manager
Dname: Sales
Location: Mumbai
```
  - the above is only for getting means get accessor
  - implementing set accessor
```c#
set
{
    if (index == 0)
        Eno = (int)value;
    else if (index == 1)
        Salary = (double)value;
    else if(index == 2)
        Ename = (string)value;
    else if(index==3)
        Job= (string)value;
    else if(index==4)
        Dname = (string)value;
    else if(index==5)
       Location = (string)value;
}

 emp[1] = 50000.00;
 Console.WriteLine("Modified Salary: "+emp[1]);
 // output:
 Modified Salary: 50000
 ```

 ---------------------------------------------------------
 ## Delegates in C#:
  - Its's a type safe function pointer.
  - A delegate holds the reference of a method and then calls the method for execution.
  - we call the method in 2 ways like:
     - with instance of the method if the method is non-static
     - by name if the method is static
     - can also call the method using delegate
  - To call a method by using a delegate we have 3 steps:
        1. Define a delegate
         [<modifier] delegate void|type <Name>([<Parameter List])
        - return type of delegate should be same as delegate
        - parameters of delegate should be same as method
        - public delegate void AddDelegate(int x,int y); // delegate for the AddNums method
          public void AddNums(int a,int b)
        - delegate is a userdefined type and its a reference type
        - we can define the delegate under the class but not suggested define under the namespace
        2. Instansaction of delegate
        - AddDelegate ad = new AddDelegate(p.AddNums);
        - pass the method as the parameter to the delegate
- ![alt text](image-59.png)
         3. Callthe delegate by passing required parameter values, so that internally the method which is bound with the delegate gets executed.
```c#
namespace DelegatesProject
{
    // step-1: defining delegate
    public delegate void AddDelegate(int x, int y);
    public delegate string SayDelegate(string s);
    class Program
    {
        public void AddNums(int a, int b)
        {
            Console.WriteLine(a + b);
        }
        public static string SayHello(string name)
        {
            return "Hello " + name;
        }
        public static void Main(string[] args)
        {
            Program p = new Program();
            p.AddNums(100, 200);
            Console.WriteLine(SayHello("Sara"));
            // calling method using delegates
            // step-2: Instantating the delegate
            AddDelegate ad = new AddDelegate(p.AddNums);
            SayDelegate sd=new SayDelegate(SayHello);
            // step-3: call the delegate with the params
            string str = sd("Alia");
            Console.WriteLine(str);
            ad(1, 2);
            // or we can also call delegate like this
            string str2 = sd.Invoke("Priyanka");
            Console.WriteLine(str2);
        }
    }
}
// output: 
300
Hello Sara
Hello Alia
3
Hello Priyanka
```

## MultiCast Delegates:
   - we can call the static and non-static methods using delegates.
   -  A delegate holds the refercne of a method
   -  so multi cast delegate will hold the reference of multiple delegates
   -  In a class if we have multiple methods with the same signature we can  call all the methods using one delegate
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DelegatesProject
{
    public  delegate void RectDelegate(double Width, double Height);
     class Rectangle
    {
        public void GetArea(double Width, double Height)
        {
            Console.WriteLine("Area of Rectangle: "+Width * Height);
        }
        public void GetPerimeter(double Width, double Height)
        {
            Console.WriteLine("Perimeter of Rectangle: "+2*(Width+Height));
        }
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle();
            r.GetArea(2.12, 3.68);
            r.GetPerimeter(2.78, 3.58);
            RectDelegate r1 = new RectDelegate(r.GetArea);
            RectDelegate r2 = new RectDelegate(r.GetPerimeter);
            r1(1, 2);
            r2(3, 5);
        }
    }
}

// output:
Area of Rectangle: 7.8016000000000005
Perimeter of Rectangle: 12.719999999999999
Area of Rectangle: 2
Perimeter of Rectangle: 16
```
  - so here we are calling the 2 methods with one delegate coz 2 methods have same signature means while initializing the delegate we can pass either of the 2 or the 2 coz it will accept the signature of the declared delegate 
  - by creating one delegate and instaining 2 delegates we can be able to achieve the multicast delegates
  - even if i change the access modifier i will work coz , access modifier will not come under method signature
  -  private void GetPerimeter(double Width, double Height)
 {
     Console.WriteLine("Perimeter of Rectangle: "+2*(Width+Height));
 }
   - giving same output with the above change also
   - even if i change the order of parameters also
   -  private void GetPerimeter(double Height, double Width)
 {
     Console.WriteLine("Perimeter of Rectangle: "+2*(Width+Height));
 }
   - giving the same output

-----------------------------------------------------------------------------\

##  Anonymous Methods in C#:
   - In delegates we bind the method with it while inastacating
   - so anonymous method means binding the unamed method with the delegate or block of code with delegate
```c#

namespace DelegatesProject
{
    public delegate string GettingsDelegate(string name);
     class AnonymousMethods
    {
        public static string Greetings(string name)
        {
            return "Hello " + name ;
        }
        static void Main(string[] args)
        {
            // GettingsDelegate gd = new GettingsDelegate(Greetings);
            //Console.WriteLine(gd("Sara"));
            // instead of all the above code we can write like

            GettingsDelegate gd = delegate (string name) // direclty passing a block of code 
            {
                return "Hello " + name;
            };
            Console.WriteLine(gd("Alia"));
        }
    }
}
// output :
Hello Alia
```

  - a method without a name is called anonymous method which constains only method body
  - it is only suggested for few lines of code not for large code
  - the return type of the anonymous method is same as the delegate
Note: Creating window form app in c#
- new project-> search for windows form app-> open -> view open toolbox -> drag and drop the buttons or whatever
- Lets say we added a button to the form and when we i click on this button i should add the another button in the center of the form
- to generate this when we double click on the button in the form wohtout running it should opens a even handler to write the code
- so button has to be added dynamically so i can't drag and drop
- create the instance for button
```c#
namespace WinFormsApp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {

            Button b = new Button(); // creating instance to the button class 
            b.Text = "Click Me"; // adding the text to the button
            b.Size = new Size(100,50); //defining the size of the button
            b.Location = new Point(150, 150); // adding x and y coordinates where the button is located
            this.Controls.Add(b); // adding the button to the form
        }
    }
}

```
// output:
- ![alt text](image-60.png)

- so when i click on the middle button i want to show some text
- for adding the text in button in the form(place the button at the time of designing) when we double click it will take us to the event handler but how to add for this?

----------------------------------------------------------------------------

## Lambda Expressions:
  - is a shorthand for writing the anonymous methods
```c#
namespace DelegatesProject
{
    public delegate string GreetingsDelegate(string name);
     class LambdaExpressions
    {
        //public static string Greetings(string name)
        //{
        //    return "Hello " + name+"!";
        //}
        static void Main(string[] args)
        {
            // without anonymousmmethod
            //GreetingsDelegate obj = new GreetingsDelegate(Greetings);
            //Console.WriteLine(obj("sara"));
            // with anonymous method
            //GreetingsDelegate obj = delegate (string name)
            //{
            //    return "Hello" + name + "!";
            //};
            // with lambad expression:
            GreetingsDelegate obj =  (name)=>
            {
                return "Hello " + name + "!";
            };
            sConsole.WriteLine(obj("sara"));
        }
    }
}
// output:
Hello sara!
```
   - In lambad expression we don't need to specify the parameter type coz its already specified in the delegate
   - Anonmous methods are simplifies by using lambda expressions

-----------------------------------------------------------------

## Func, Action and Predicate Delegates:
  - ### Generic Delegates:
     - Predefined Delegates:
       - func
       - action
       - predicate

- example without predefined elegates:
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DelegatesProject
{
    class GenericDelegates
    {
        public delegate double Delegate1(int x, float y, double z);
        public delegate void Delegate2(int x, float y, double z);
        public delegate bool Delegate3(string str);

        public static double AddNums1(int x, float y, double z)
        {
            return x + y + z;
        }
        public static void AddNums2(int x, float y, double z)
        {
            Console.WriteLine( x + y + z);
        }
        public static bool CheckLength(string str)
        {
            if(str.Length>=5)
                return true;
            return false;
        }

        static void Main(string[] args)
        {
            Delegate1 d1 = AddNums1;
            Console.WriteLine(d1(100,34.5f,12.5768));
            Delegate2 d2 = AddNums2;
            d2(12,45.36f,98.364);
            Delegate3 d3 =CheckLength;
            Console.WriteLine(d3("Hello"));
        }
    }
}

```
  - generally a delegate hold the refernce of the method and class the method and till now we have defined the delegate and used them but we have predefined delegates
  - we have 3 predefined delegates:
    - func delegate: is used for value returning
       - Func<int,float,double,double> obj1= AddNums1;
       - here int, float, doublt are -> inputs and double -> output type

    - action delegate: used for void delegates means it returns nothing
        -  Action<int, float, double> obj2= AddNums2;
        - here it retunrs void so the mentioned types in genrics are params types

    - predicate: used for bool return type
         - Predicate<string> obj3 = CheckLength;
         - it will return the bool type and input is string

- with predefined delegates:

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DelegatesProject
{
    class GenericDelegates
    {
        //public delegate double Delegate1(int x, float y, double z);
        //public delegate void Delegate2(int x, float y, double z);
        //public delegate bool Delegate3(string str);

        public static double AddNums1(int x, float y, double z)
        {
            return x + y + z;
        }
        public static void AddNums2(int x, float y, double z)
        {
            Console.WriteLine( x + y + z);
        }
        public static bool CheckLength(string str)
        {
            if(str.Length>=5)
                return true;
            return false;
        }

        static void Main(string[] args)
        {
            //Delegate1 d1 = AddNums1;
            //Console.WriteLine(d1(100,34.5f,12.5768));
            //Delegate2 d2 = AddNums2;
            //d2(12,45.36f,98.364);
            //Delegate3 d3 =CheckLength;
            //Console.WriteLine(d3("Hello"));

            // with predefined delegates:
            Func<int,float,double,double> obj1= AddNums1;
            Console.WriteLine(obj1(12,23.56f,123.4645));

            Action<int, float, double> obj2= AddNums2;
            obj2(10, 12.56f, 53.489);

            Predicate<string> obj3 = CheckLength;
            Console.WriteLine(obj3("Hello world"));
        }
    }
}
```
  - here without defining and instaninting the delegates we are using the predefined delegates
  - replacing the method with lambda expression

```c#
     Func<int, float, double, double> obj1 = (x, y, z) =>
     {
         return x + y + z;
     };
     Console.WriteLine(obj1(11, 12.21f, 25.151));

     Action<int, float, double> obj2 = (x, y, z) =>
     {
         Console.WriteLine(x + y + z);
     };
     obj2(10, 23.15f, 18.236); 

     Predicate<string> obj3 = (str) =>
     {
         if (str.Length >= 5)
             return true;
         return false;
     };
     Console.WriteLine(obj3("Hello world"));


 ```
  - 

----------------------------------------------------------------

## Extension Methods in C#:
- This a new feature added in c# 3.0.
    - Lets say there is a class with 10 methods ex:string class and when we want to add more methods into it we don't have to source code
    - so when we want to add new methods into class problems are:
        - Source is not avaible for most of the classes like string
        - and the class might not have permissions to add new methods
    - To over come this problem we can use inheritance like defining a new class what ever methods we want can be declared in the child class and we also have the methods in the actual class or we can access them also, for inheriting we don't need the source code and also don't need any permissions to add new methods 
- ![alt text](image-61.png)
   - Inheritance is a mechanism using which we can extend the functionalities of a class 
   - but there are some problems with this also:
   - 1. If it is a sealed class we can't apply inheritance on it
   - 2. If it is a structure we can't apply inheritance on it also
   - 3. we can only call the child and parent cclass methods using child class instance
   - so to overcome this problem microsoft introduced extension methods
- # Defination: It's a machenism of adding new methods into an existing class or structure also with out modifying the source code of the original type and we don't require any persmissions from original type and origial type doesn't require any re-compilation.
    - How to add the methods:
       1. take one new class and that muts be static
       2. define the methods in new class
       3. after that we can bind the 5 methods with the original class/structure
- ![alt text](image-62.png)

```c#
using System;
namespace ExtensionMethodsProject
{
    class Program
    {
        public void Test1()
        {
            Console.WriteLine("Method 1");
        }
        public void Test2()
        {
            Console.WriteLine("Method 2");
        }
        static void Main(string[] args)
        {
          Program p= new Program();
            p.Test1();
            p.Test2();
            p.Test3();
        }
    }
}


namespace ExtensionMethodsProject
{
    static class StatClass
    {
        // means the method test3 belongs to the program class
        public static void Test3(this Program p) // binding the program p with with method
        {
            Console.WriteLine("Method 3 ");
        }
    }
}


// output:
Method 1
Method 2
Method 3
```

  - Extension methods are declared as static so we can call them by name of the class but once they are bound with class they will become non-static that's why we are calling it with instance of the original class
  - If an extension method is defined with the same name and signature as in the original class then if we call the method with original class instance the orignal method will get called.
  - If we want the extension method with parameters we can add the parameters
  - "public static void Test3(this Program p, int i){}"
  - it will ignore the "this Program p" and considers from next params and binding parameter must be first 
  - We can write the extension methods for the classes which doesn't even have source code available like for int also we can write some method since int is a predefined structure
```c#
 public static long Factorial(this Int32 x) // x is the parameter here it will take the input 
 {
     long sum = 1;
     for (int i = 1; i <= x; i++)
         sum *= i;
     return sum;
 }

   int i = 5;
Console.WriteLine(i.Factorial());

// output:
120
```
  - We can add extension methods in sealed classes also
  - string  is a sealed class
```c#
using System;
namespace ExtensionMethodsProject
{
    class Program
    {
        public void Test1()
        {
            Console.WriteLine("Method 1");
        }
        public void Test2()
        {
            Console.WriteLine("Method 2");
        }
        static void Main(string[] args)
        {
          Program p= new Program();
            p.Test1();
            p.Test2();
            p.Test3(9);
            // extension of int 
            int i = 5;
          Console.WriteLine(i.Factorial());
            // adding extension method for sealed class(string)
            string str = "HeLLo How aRe You";
            String s1 = " ";
            // let's say i want to convert it in to proper class
            Console.WriteLine(str.ToProper());
            Console.WriteLine(s1.ToProper());
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ExtensionMethodsProject
{
    static class StatClass
    {
        // means the method test3 belongs to the program class
        public static void Test3(this Program p, int i) // binding the program p with with method
        {
            Console.WriteLine("Method 3 " + i);
        }

        // adding Extension factorial method for int srtucture
        public static long Factorial(this Int32 x) // x is the parameter here it will take the input 
        {
            long sum = 1;
            for (int i = 1; i <= x; i++)
                sum *= i;
            return sum;
        }

        // Adding Extension properCase method for string class
        public static string ToProper(this string OldStr)
        {
            String NewStr = null;
            if (OldStr.Trim().Length > 0)
            {
                OldStr = OldStr.ToLower();
                string[] arr = OldStr.Split(" ");
                foreach (String s in arr)
                {
                    char[] carr=s.ToCharArray();
                    carr[0] = Char.ToUpper(carr[0]);
                    NewStr += new String(carr)+" ";
                }
                return NewStr;
            }
            return OldStr;
        }
    }
}

// output:
Method 1
Method 2
Method 3 9
120
Hello How Are You


```


--------------------------------------------------------------------------------

## Diff b/w String and StringBuilder:
   - Strings are immutable 
   - Means Once we delacre and initialize a string we ca't modify or perform actions on it
   - when we initialize a string the memory will be allocated in head memory
   - and when we concatinate one value with that string then it will create one more string in the new memory location
   - so 2 copies will be there now the string var will point to the new memory location
- ![alt text](image-63.png) 
- ![alt text](image-64.png)
    - so the string value is never going to override it will create a new copy again in the memory with the conctinated string
    - when is suggested to go for string is when it requires very less modifications
    - So it is better to use a string builder when every if we perform many modifications
    - coz String builder is mutable
    - StringBuilder sb=new StringBuilder("Hello");
    - here we are giving 5 chars but internally 16 chars memory will be allocated for this sb for allowing future modifications
- ![alt text](image-65.png)
    - we can't use conct(+) symbol on string builder we can use append to add 
- ![alt text](image-66.png)
     - It will be going to add like this in the memory 
-  ![alt text](image-67.png)
     - again adding new value
     - will be stored like this in the memory
- ![alt text](image-68.png)
     - So initlially when we initialize the memory of 16 chars will be allocate right so when we add more chars than 16 it will resize the memory to 32 chars
     - so the capacity will get doubles when we add more chars the that capacity
     - so whenever we want to make frequent changes it is suggest to go for string builder
     - stringBuilder is present in System.Text nameSpace
     - string is present under system nameSpace.
```c#
using System;
using System.Text;
using System.Diagnostics;

namespace StringExample
{
    class Program
    {
        static void Main(string[] args)
        {
            String s = "";
            for(int i=1;i<=100000;i++)
            {
                s = s + i;
            }
        }
    }
}
```
   - here in this code 1lakh times s will get modified means it will create 1lakh +1 copies
   - lets say we did the same logic with stringBuilder class and we want see how much time each taks takes
   - so do this we are provided with a class called as stopWatch
```c#
using System;
using System.Text;
using System.Diagnostics;

namespace StringExample
{
    class Program
    {
        static void Main(string[] args)
        {
         
            String s = "";
            Stopwatch sw1 = new Stopwatch();
            sw1.Start();
            for (int i=1;i<=100000;i++)
            {
                s = s + i;
            }
            sw1.Stop();
            StringBuilder sb = new StringBuilder();
            Stopwatch sw2 = new Stopwatch();
            sw2.Start();
            for (int i = 1; i <= 100000; i++)
            {
                sb.Append(i);
            }
            sw2.Stop();

            Console.WriteLine("Time taken for String: " + sw1.ElapsedMilliseconds);
            Console.WriteLine("Time taken for StringBuilder: " + sw2.ElapsedMilliseconds);

        }
    }
}

// output:
Time taken for String: 6142
Time taken for StringBuilder: 1
```
   - so when we have more modifications to do never go with string go with string builder
   - In string builder it will initally starts with 16 char memory so if we know the capacity already we can assign it while defining only like below
   -   " StringBuilder sb = new StringBuilder(10000); " // will starts with 10000 capacity and doubles if this capcity exceeds
   - by giving the capacity it will increase the capacity little but

   -------------------------------------------------------------------------

## Exceptions and Exception Handling:
   - ###### Exception:
      - In our application we come across 2 types of errors:
          1. Complie time errors - an error occurs due to syntaxial errors like semicolon, doublequotes and braces and these are not dangrous
          2. Run time errors - errors occure at the time execution of program like wrong implementation of logic, wrong inputs supply and missing required resouces
          ex: Wrong Implementation of Logic: Lets say i have an array of lenght 5 and when i write a for loop that executes for 6 times then that will be a run time error.
          Wrong Inputs Supply: lets say we told the use to enter an integer value but use enters like string/bool/double etc.
          Missing Required Resources: Lets say we write a program to open a file on hard disk and read it but if doesn't exist that will be this error

    - SO these run time errors are dangrous coz the program stops abnormally where the error occurs and will not go to the next line
    - SO when a program stops abnormally it is the responsibilty of the Exceptions
    - What is Exceptions:
       Exception is a classes
       - diff errors have diff class names like IndexOutOfBoundsException
       - DivideByZeroException - if we try to divide a num by 0 
       - OverFlowException - If we try to give the bigger value than the limit of var ex int ,float etc
       - FormatException: occurs when we try to convert a double into int, string to float etc
       - If any execption comes and the program stops abnormally it will display the error message so for each error diff class is being given
- ![alt text](image-69.png) 
      - Exception are divided into 2 categories:
         - ApplicationException: porgrams made exception like in our app we don't want the num to be divided by an odd num.
         - SystemException: are universal exceptions like dividing by 0
         - all the above exception classes come under systemexceptions
-  ![alt text](image-70.png)
       - so every exception class is overriding the virtula message property so that they will display the error message according to the error
------------------------------------------------------------------------------------

- ### How Exceptions will occur:
    - Like when we try to divide a num by 0 or try to convert some string to int
    -  Common Language Runtime (CLR): 
    - The CLR is a virtual machine that manages the execution of .NET applications.
    - whever there is a runtime error CLR will create instance of a matching exception class and thows it, the instance which is created by CLR will stops the execution abnormally
     - To handle this exception we have exception handling
     - so exception handing is a process of stoping the abnormal terminatio of the program
     - Adv of Exception Handling:
- ![alt text](image-71.png)
- ![alt text](image-72.png)
    - To handle exception we have to keep the code in try and catch blocks
- ![alt text](image-73.png)
- ![alt text](image-74.png)
    - In try block we keep the code which causes exception or which doen't need to be executed when exception occurs
    - in catch block correct actions/ error message displaying
    - catch block will execute only when there is any exception other wise it will skip
    - At any line there is an exception from that line only controll jumps to the catch block
    - If an exception occurs at any line of code it will look for the matcing catch block if found the matching catch block abnormal termination stops and executes the catch block and executes the lines sfter catch block
    - If it doesn't found the matching catch block abnormal termination will occur again 
    - Finally: we can use the finally block after catch like even the exception occurs or not it will defenatly executes
    - some imp code will be written in this block(like closing the file, closing db connections etc)
- ![alt text](image-75.png)
    - try block evey line will execute if there is no exception in the code
    - catch block will execute if there is any exception in code
    - finally block will execute in both the cases
    - the finally block will execute even if no matching catch block is found and the program is about to terminate abnormally due to an unhandled exception, as long as the runtime isn't forcibly stopped (e.g., by Environment.FailFast(), a system crash, or power failure).
    - so even if the programs stops abnormally the finally block will executes unit there is a power off or forcefully dtops the program.
    - Lets say in our program we have finally block and after the finally block also we have one statement so when the excpetion occurs or not the finally block will execute and also the statement after the finally bloxk executes the what is the use of writing the finally block we can directly write the statements after the catch block 
```c#
try
{
    // some stmt's
}
catch(Exception e)
{
    // some
}
finally
{
    print("finally");
}
print("end of program");

```
   - in both the cases like exception occurs or not the finally and end of program will be printed
   - Then what will be use of finally block?
```c#
class Program{
svm()
{
try
{
    //some
    if()
    return; // exists from the main method
    // some stms
}  
catch(Exception e)
{
    //
}
finally
{
    print("Finally");
}
print("end ");
}// end of method
} // end of program
```
   - in the above program when return is executed the controll will jump to the end method
   - but even though the finally block will execute bu the end stmt will not execute
   - so at any case finally will always execute but we can't guarante the stms outside it so this is the use of finally
   - we can also write try and finally block without catch block, but exceptions will not caught and abnormal termination will occur but even abnormal termination occurs finally block will executes

### Application Exceptions:
   - when the exceptions are raised by CLR they are called system exceptions and the consitions are predefined in this
   - Application exceptions are thown by the programer as per ur requirment
- ![alt text](image-76.png) 
   - so when the programer wants to throw the exception they can create the instance and thow like shown above
   - if they don't provide any message the message in the parent Exception class will be displayed
- ![alt text](image-77.png) 
   - the above is the example of throwing the application exception
   -  we can also define the exception class of our own 
- ![alt text](image-78.png)
   - in the above ex we can see that the exception class is ApplicationException but we can also define our own exception like dividedByZero exception
   - how to define own our exception class:
        1. inherit from any exception class best is applicationException
```c#

  public class DivideByOddNOException: ApplicationException
  {
     public override string Message
     {
        get
        {
            return "Attempted to divide by odd number";
        }
     }
  }
//  using th exception class
 throw new DivideByOddNOException();

```
- ![alt text](image-79.png)