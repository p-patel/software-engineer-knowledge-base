C# Fundamentals

https://app.pluralsight.com/course-player?clipId=a378cd76-5548-4933-8f1c-b233c7b8afae

# Introducing C# and .NET
## Understanding .NET and .NET Core
...

# Working With Reference Types and Value Types
- **Create a reference repo for C# (and for every language) that contains unit tests to understand the behaviour of the language.**  E.g. are parameters passed by value or reference by default, operator behaviour for different operand types, strings etc, etc.

## Passing Parameters By Value
> How are parameters passed in C# by default (without any modifiers)?
>> In C# all parameters are always passed by value by default.  This is by design to avoid unexpected side effects

## Returning Object References

## Returning Parameters by Reference
> How do you pass parameters by reference in C#?
>> Use the `ref` modifier.  This must be used on both the method parameter and calling code parameter.  This was done so both the caller and called code are aware that the parameter is being passed by reference

> What is the difference between `ref` and `out`?
>> `out` is the same as `ref` and also passes the parameter by reference.  The difference is that an `out` paramater must be assigned a value in the method as it is assumed to be uninitialised in the calling code.

## Working With Value Types


## Looking for Reference Types and Values Types
- Reference types: classes, string (but often behaves as a value type)
- Value types: structs (e.g. DateTime, enums, int, float, double, boolean)
- press `F12` on any type to view type metadata to see if a type is defined as a class or struct

## The Special Case of Strings in .NET
- Strings are an immutable reference type
- String operations will return a new copy of a string
- Why were strings made immutable in C#???

## Taking Advantage of Garbage Collection
- .NET runtime provides a garbage collector to manage the release of memory

# Building Types

## Overload Methods
- return type is not part of the method signature (so can't overload a method with a different return type)

## Defining Properties
- property vs field
- add logic in the getter/setter within a property

## Defining Property Getters And Setters
- Auto properties using `get;` `set;`
- public property vs public field - very few differences; can apply different access modifiers to the getter and setter of a property; areas of serialisation and reflection in .NET will treat public properties differently to public fields; 

## Defining Readonly Members
- Can only write to in the constructor / variable initialiser
- Provides certainty that the members value won't change for the rest of the object's lifetime

## Defining const Members
- public const members are treated as static members i.e. referenced by using class name

## Introducing Events and Delegates
- Not in style with server frameworks, popular in forms and desktop programming
- Build on top of the delegate type

## Defining a Delegate
- A type; different from a class or struct definition
- delegate points to and invokes different methods with the specified signature and return type
- delegate type is defined and then variable defined, assigned to and used/called
- enables indirection of a called method
- `public delegate string DoSomething(int value)` defines a delegate **type**
- this delegate type can then be used to declare a local variable or class member delegate which can be assigned to and used to invoke methods with a level of indirection

## Using Multi-cast Delegates
- multi-cast - delegate can invoke multiple methods
- uses `+=` operator 
- delegates provide ability to declare variables that can be used as methods

## Defining An Event
- define a class event member `public event GradedAddedDelegate GradeAdded` using a defined delegate **type**
- defining the member using `event` and not just as a delegate type on its own means the member cannot be directly assigned to using `+` and instead can only be added/removed to/from using `+=` and -=`

## Subscribing To An Event
- `event` members can be used with `delegate` members to implement events and event handling
- raising an event - this is invoking the event class member (delegate)
- handling an event - this is calling the methods added to the delegate invocation list using the `+=` operator
- use `-=` operator to remove methods to the event delegate

## Summary
- Added additional field and member types: properties, delegates, events

