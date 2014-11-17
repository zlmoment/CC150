### Java Basic Notes

With the use of **Just-In-Time compilers**, Java enables high performance.

Names used for classes, variables and methods are called **identifiers**.

Like other languages, it is possible to modify classes, methods, etc., by using modifiers. There are two categories of modifiers:

1) Access Modifiers: default, public , protected, private

2) Non-access Modifiers: final, abstract

**Enums** restrict a variable to have one of only a few predefined values. The values in this enumerated list are called enums.

**Inheritance**: In Java, classes can be derived from classes. Basically if you need to create a new class and here is already a class that has some of the code you require, then it is possible to derive your new class from the already existing code.

**Interfaces**: In Java language, an interface can be defined as a contract between objects on how to communicate with each other. Interfaces play a vital role when it comes to the concept of inheritance.

An interface defines the methods, a deriving class(subclass) should use. But the implementation of the methods is totally up to the subclass.

#### Java - Objects and Classes

A class can contain any of the following variable types.

1) **Local variables**: Variables defined inside methods, constructors or blocks are called local variables. The variable will be declared and initialized within the method and the variable will be destroyed when the method has completed.

2) **Instance variables**: Instance variables are variables within a class but outside any method. These variables are instantiated when the class is loaded. Instance variables can be accessed from inside any method, constructor or blocks of that particular class.

3) **Class variables**: Class variables are variables declared with in a class, outside any method, with the static keyword.

**How to use Singleton Class**: http://goo.gl/mb6LSP

#### Java Basic Data Types

Variables are nothing but reserved memory locations to store values. This means that when you create a variable you reserve some space in memory.

Primitive data types are predefined by the language and named by a keyword: byte, short, int, long, float, double, boolean, char

#### Java Variable Types

**Local variables**:

1) Local variables are declared in methods, constructors, or blocks.

2) Local variables are created when the method, constructor or block is entered and the variable will be destroyed once it exits the method, constructor or block.

3) Access modifiers cannot be used for local variables.

4) Local variables are visible only within the declared method, constructor or block.

5) Local variables are implemented at **stack** level internally.

6) There is no default value for local variables so local variables should be declared and **an initial value should be assigned** before the first use.

**Instance variables**:

1) Instance variables are declared in a class, but outside a method, constructor or any block.

2) When a space is allocated for an object in the **heap**, a slot for each instance variable value is created.

3) Instance variables are created when an object is created **with the use of the keyword 'new'** and destroyed when the object is destroyed.

4) Instance variables hold values that must be referenced by more than one method, constructor or block, or essential parts of an object's state that must be present throughout the class.

5) Instance variables can be declared in class level before or after use.

6) Access modifiers can be given for instance variables.

7) The instance variables are visible for all methods, constructors and block in the class. Normally, it is recommended to make these variables private (access level). However visibility for subclasses can be given for these variables with the use of access modifiers.

8) Instance variables **have default values**. For numbers the default value is 0, for Booleans it is false and for object references it is null. Values can be assigned during the declaration or within the constructor.

9) Instance variables can be accessed directly by calling the variable name inside the class. However within **static methods and different class** ( when instance variables are given accessibility) should be called using the fully qualified name . ObjectReference.VariableName.

**Class/static variables**:

静态变量是属于类的，而不是属于类创建的对象或实例。因为静态变量被类的所有实例共用。

1) Class variables also known as **static variables** are declared with the **static keyword** in a **class**, but outside a method, constructor or a block.

2) There would only be one copy of each class variable per class, regardless of how many objects are created from it.

3) Static variables are rarely used other than being declared as constants. Constants are variables that are declared as public/private, final and static. Constant variables never change from their initial value.

4) Static variables are stored in **static memory**. It is rare to use static variables other than declared final and used as either public or private constants.

5) Static variables are created **when the program starts and destroyed when the program stops**.

6) Visibility is similar to instance variables. However, most static variables are declared public since they must be available for users of the class.

7) Default values are same as instance variables. For numbers, the default value is 0; for Booleans, it is false; and for object references, it is null. Values can be assigned during the declaration or within the constructor. Additionally values can be assigned in special static initializer blocks.

8) Static variables can be accessed by calling with the class name . ClassName.VariableName.

9) When declaring class variables as public static final, then variables names (constants) are all in upper case. If the static variables are not public and final the naming syntax is the same as instance and local variables.

#### Java Loops

The variable used in a switch statement can only be a byte, short, int, or char.

#### Strings

As with any other object, you can create String objects by using the new keyword and a constructor.

```java
char[] helloArray = { 'h', 'e', 'l', 'l', 'o', '.'};
String helloString = new String(helloArray);  
```

#### Java - Arrays

**Declaring** Array Variables: dataType[] arrayRefVar;   // preferred way.

**Creating** Arrays: arrayRefVar = new dataType[arraySize];

So: dataType[] arrayRefVar = new dataType[arraySize];

or

dataType[] arrayRefVar = {value0, value1, ..., valuek};

The java.util.Arrays class contains various static methods for **sorting** and **searching** arrays, **comparing** arrays, and **filling** array elements. 

#### Java - Regular Expressions

http://goo.gl/C7uN1

### Java - Methods

**Method Overloading**:

When a class has two or more methods by same name but different parameters, it is known as method overloading. It is different from overriding. In overriding a method has same method name, type, number of parameters etc.

**Variable Arguments(var-args)**:

JDK 1.5 enables you to pass a variable number of arguments of the same type to a method. The parameter in the method is declared as follows:

```
typeName... parameterName
```

**The finalize( ) Method**:

It is possible to define a method that will be called just before an object's final destruction by the garbage collector. This method is called finalize( ), and it can be used to ensure that an object terminates cleanly.

#### Java - Inheritance

Inheritance can be defined as the process where one object acquires the properties of another. 

When we talk about inheritance, the most commonly used keyword would be **extends** and **implements**. 

With use of the extends keyword the subclasses will be able to inherit all the properties of the superclass except for the private properties of the superclass.

The implements keyword is used by classes by inherit from interfaces. Interfaces can never be extended by the classes.

A very important fact to remember is that Java only supports only single inheritance. However, a class can implement one or more interfaces.

IS-A and HAS-A relationship.

#### Java - Overriding

In object-oriented terms, overriding means to override(不顾，不理) the functionality of an existing method.

A method declared final cannot be overridden.

A method declared static cannot be overridden but can be re-declared.

Constructors cannot be overridden.

When invoking a superclass version of an overridden method the **super** keyword is used.

#### Java - Polymorphism (多态)

We already have discussed method overriding, where a child class can override a method in its parent. An overridden method is essentially hidden in the parent class, and is not invoked unless the child class uses the super keyword within the overriding method.

This behavior is referred to as **virtual method invocation**, and the methods are referred to as virtual methods. **All methods in Java behave in this manner, whereby an overridden method is invoked at run time, no matter what data type the reference is that was used in the source code at compile time.**

Java中其实没有虚函数的概念，它的普通函数就相当于C++的虚函数，动态绑定是Java的默认行为。如果Java中不希望某个函数具有虚函数特性，可以加上final关键字变成非虚函数

重载，英文名是overloading，是指在同一个类中定义了一个以上具有相同名称，但是型构不同的方法。在同一个类中，是不允许定义多于一个的具有相同型构的方法的。

#### Java - Abstraction

**Abstract Class**:

An abstract class is one that cannot be instantiated. All other functionality of the class still exists, and its fields, methods, and constructors are all accessed in the same manner. You just cannot create an instance of the abstract class.

If a class is abstract and cannot be instantiated, the class does not have much use unless it is subclass. 

**Abstract Methods**:

If you want a class to contain a particular method but you want the actual implementation of that method to be determined by child classes, you can declare the method in the parent class as abstract.

The abstract keyword is also used to declare a method as abstract. An abstract method consists of a method signature, but no method body.

Abstract method would have no definition, and its signature is followed by a semicolon, not curly braces.

```
public abstract class Employee
{
   private String name;
   private String address;
   private int number;
   
   public abstract double computePay();
   
   //Remainder of class definition
}
```

Declaring a method as abstract has two results:

1) The class must also be declared abstract. If a class contains an abstract method, the class must be abstract as well.

2) **Any child class must either override the abstract method or declare itself abstract.**

#### Java - Encapsulation (封装)

#### Java - Interfaces

An interface is a collection of abstract methods.








