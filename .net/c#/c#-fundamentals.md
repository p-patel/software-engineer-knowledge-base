C# Fundamentals

https://app.pluralsight.com/course-player?clipId=a378cd76-5548-4933-8f1c-b233c7b8afae

# Introducing C# and .NET
## Understanding .NET and .NET Core
...

## Working With Reference Types and Value Types
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
