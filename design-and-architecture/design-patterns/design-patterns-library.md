# Design Patterns Library
https://app.pluralsight.com/library/courses/patterns-library/

# Introduction to Design Patterns
## What They Are
- General and reusable solutions to common problems in software design
- A template or recipe for solving certain problems
- Patterns are named for identification
- Patterns deal with: application and system design, abstractions on top of code, relationships between classes or other collaborators, problems that have already been solved
- Patterns are NOT concerned with: algorithms, specific implementations or classes

## Design Pattern History
- Christopher Alexander - architect - A  Pattern Language: Towns, Buildings, Construction
- Design Patterns: Elements of Reusable Object-oriented Software - Gang of Four

## Pattern Organisation and Language
- Creational, Structural, Behavioural Patterns
- Other classifications: Security, Concurrency, Sql, User Interface, Relational, Social, Distributed

## Why Patterns Matter
- Gives our profession a shared language
- Provide good software designs

## Criticisms
X

## The PSOD Patterns Library
- implemented using .NET
- genuine and practical context
- use as a reference

## Summary
X

# Adapter Pattern
## Motivating Example
- A class that would be useful to your application does not implement the interface you require
- You are designing a class or framework and you want to ensure it is usable by a wide variety of as-yet-unwritten classes and applications
- Adapters are also commonly known as _Wrappers_
- This module refers only to _object adapters_, which do not require multiple inheritance (as _class adapters_ do)
## Graphic Example
- The 'shape' of the interface the consumer class has and the 'shape' of the interface the library class has are different.  The adapter maps the interface from the library class to the consumer class so that the library class can be used.
## Real World Example
- A real world analogy is a UK-to-US plug adapter
## Intent
- Convert the interface of a class into another interface clients expect
- Allows classes to work together that couldn't otherwise due to incompatible interfaces
- _Future-proof_ client implementations by having them depend on Adapter interfaces, rather than concrete classes directly
## Applicability
- You want to use an existing class, but its interface does not match the one you require
- You want to create a reusable class that cooperates with unrelated or unforeseen classes (i.e. classes that won't necessarily share the same interface)
- You need to use several existing subclasses, but it's impractical to adapt their interface by subclassing every one.
## Structure
- Client -> IAdapter.Operation() -> ConcreteAdapter.Operation() _calls/wraps_ -> Adaptee.AdaptedOperation()
- Client wants to use Adaptee but can't due to incompatible interface
## How It Gets Used
- Client depends on the Adapter interface, rather than a particular implementation
- At least one concrete Adapter class is created to allow the client to work with a particular class that is requires
- Future client needs for alternate implementations can be satisfied through the creation of additional concrete Adapter classes
- Effective way to achieve Open/Closed principle
## Collaboration
- Client calls operations on the Adapter instance
- Adapter instance calls Adaptee operations that carry out the request
## Consequences
- A single Adapter interface may work with many Adaptees:
* One Adaptee and all of its subclasses
* Separate adaptees via separate concrete Adapter implementations
- Can be difficult to override Adapter behaviour (with Object Adapter) - _difficult when compared to using multiple inheritance_:
* Must subclass Adaptee and override behaviour
* Then change concrete Adapter implementation to refer to Adaptee subclass
- This is because we are using composition and not inheritance
## Implementation Example
- ADO.NET's `IDataAdapter`
## Demo
- A `DataRenderer` class that accepts an `IDbDataAdapter` constructor parameter.  `DataRenderer` can be instantiated with any concrete instance of `IDbDataAdapter` to read data from any database.  `DataRender.Render(TextWriter writer)` then writes data from any concrete class that implements `IDbDataAdapter` to `writer`.
- Also `PatternRenderer` class demo that has a `IDataPatternRenderer`dependency.  `PatternRenderer.ListPatterns(IEnumerable<Pattern> patterns)` calls `ListPatterns(IEnumerable<Pattern> patterns)` on this dependency.  An adapter class implements `IDataPatternRenderer` and acts as the adapter in this scenario, wrapping any Adaptee class.
## Related Patterns
- Repository - a higher level pattern that is a very common use of the Adapter pattern
- Strategy - The Adapter pattern is often passed into a class or method (in constructor, parameter or property) that depends on it, thus implementing the Strategy pattern
- Facade - Adapter and Facade are both wrappers.  The Facade pattern attempts to simplify the interface and often wraps multiple classes, while the Adapter typically wraps a single Adaptee, and is not generally concerned with simplifying the interface.
## References
- Design Patterns - Gang of Four
- Design Patterns Explained
- Design Patterns in C#
- Head First Design Patterns (alternative view of design patterns - recommended!)
## Summary
- The Adapter pattern wraps a needed class with a class that implements a required interface
- By writing client classes so they depend on adapters, we future-proof these classes, ensuring they can be made to work with as-yet-unwritten implementation libraries
- Remember the Open/Close principle

# Bridge Pattern
## Introduction
- "Decouple an abstraction from its implementation so the two can vary independently"
- Abstraction - generally a classification of a group of things or something that exists in our problem domain - e.g. a base class or interface that abstracts away a concept that can have multiple implementations.
- Abstractions are coupled to implementation be default
- Bridge pattern: Abstraction -> Abstraction -> Implementation.  By putting the implementation behind another abstraction / level of indirection, the original abstraction and implementation are decoupled.  This allows both the abstraction and implementation to change independently with the 'glue' in-between that binds them together.  The Bridge is the bridge that is connecting the two things that are independent to each other.
## Nom Nom Burger
- Separate burger from combining with either fries & drink or milk & vegetables.  Simplifies combinations and simplifies addition of new combination options (e.g. new type of burger)
## Initial Problem
- `FAQ`, `Book`, `TermPaper` classes with common `Print()` method
- Refactor by defining `IManuscript` with `Print()` method.  Allows iterating over `IManuscript` collection and calling `Print()`.  Concrete implementations of `IManuscript` are `FAQ`, `Book`, `TermPaper`
## Wrong Solution
- New requirement: Print manuscripts backwards
- Wrong solution - inherit from existing concrete implementation classes and override `Print()` method
- This requires new subtype for each existing concrete implementation class
- Instead create an abstraction for the implementation of printing - this leads to the Bridge pattern
## Refactoring to Bridge
- `Print()` method uses `formatter.Format("Title", Title);` to output text instead
- change `IManuscript` to abstract class `Manuscript` with new `IFormatter` dependency
- existing `FAQ`, `Book`, `TermPaper` classes now inherit from `Manuscript` class and override abstract method `void Print()`.  Constructors for these subclasses take the `IFormatter` dependency and pass to base abstract class
## Standard Formatter
- create `StandardFormatter` class that implements `IFormatter` and pass into each `Manuscript` subclass constructors when instantiating
- `Manuscript` subclasses now use the `IFormatter` abstraction as an extra level of indirection to the implementation of the formatting functionality
## Reverse Formatter
- Add `BackwardsFormatter` that implements `IFormatter` that outputs text in reverse using `new string(value.Reverse().ToArray())`
- Alternatively, this implementation can be passed into `Manuscript` subclass constructors when instantiated
## Fancy Formatter
- A third `IFormatter` implementation that outputs a fancy text output
## What We Did
- UML:
Refined Abstraction (`Manuscript` subclass) "is a" Abstraction (`Manuscript`) "has a" Implementor (`IFormatter`) "is a" Concrete Implementor (`StandardFormatter`, `BackwardsFormatter`, `FancyFormatter`)
## Common Usages
- UI: multi-platform UIs will allow different shapes to be drawn using an implementation of a platform-specific Drawing API
- Persistance: persistance layer will contain an abstraction to the particular type of persistances e.g. db, file, streaming over the network etc.
- .NET Provider Model: implemented as a bridge pattern, e.g. Authorisation provider or Membership provider
- A large class hierarchy which is split on different implementations of an abstraction and combinations of these implementations with another abstraction is a good candidate for the Bridge pattern to simplify the class hierarchy and allows simpler combinations
- Summary
- We covered the meal menu that separates the meal combos from the actual burgers

# The Builder Pattern
## Introduction
- Problem 1: Too many paramters
- Problem 2: Order dependent
- Problem 3: Different constructions
- What We Built
- Variations
## Understanding Builder
- _Separates the construction of a complex object from its representation such that the same construction process can be used to create different representations_ (aka separate the logic from the data and reuse that logic)
- A Dialogue - scenario is where you have to pass many parameters to an object and set properties on it to configure the object as required
- Another Dialogue - pass ingredients and the steps to make a sandwich are used
## Problem 1
- constructor with many parameters, can also be multiple such constructors
- can change constructor parameters to properties which can be set to configure the object instead (this requires public properties to be created and user must remember all the properties)
## Problem 2
- the new solution requires the user to remember all the properties that need to be set
- setting of properties means order of creation can no longer be controlled
- can create class `MySandwichBuilder` with `CreateSandwich()` in which all the properties are set and the instance is created.  Can then call `GetSandwich()` on the builder class to retrieve the built sandwich instance
- `CreateSandwich()` can apply instance creation business logic as required
## Problem 3
- creation of each new variation of the object requires the definition of a new class which will repeat creation business logic
- alternatively, define abstract methods for each step of the creation process in base abstract class `SandwichBuilder`.  Subclasses can then implement custom logic for each step of creation
- next define `SandwichMaker` class with `SandwichBuilder` dependency and `BuildSandwich()` which defines the creation process using the creation steps previously defined by calling them on `SandwichBuilder`.  `SandwichMaker.GetSandwich()` returns sandwich instance from `SandwichBuilder`
- `MySandwichBuilder` and `ClubSandwichBuilder` subclass `SandwichBuilder` and just implement each of the creation steps (the 'ingredients'). `SandwichMaker` controls the build process through its defined creation process
- Define `SandwichBuilder` subclasses as required
## What We Built
- The UML:
Director "has a" Builder. Concrete Builder "is a" Builder. Concrete Builder "builds a" Product
- Concrete Builder defines the steps of creation, Director has the process of creation
- Director just needs the ingredients, it already knows the creation process
- Builder defines the steps and holds instance of the product
- Concrete Builder defines the ingredients - will be more than one of these
- Product is what is being built with the same types but different data
## Variations
- .NET StringBuilder does not implement the builder pattern
- Fluent syntax for building objects is not the builder pattern as it does not fulfill the Director role that enforces the creation business logic.  (_What if a `.Build()` method is called at the end to create the object and implements the creation business logic??_)
## Summary
- The goal is to separate the creation business logic from the data and reuse the business logic
- Problem 1: Too many parameters
- Problem 2: Order dependent (order properties are set and/or missing property values)
- Problem 3: Different constructions - different concrete builders that use the same director

# Chain of Responsibility
## Introduction
- Decouple sender of a message from the receiver
- An ordered list of message handlers. The sender sends the message to the first handler which handles the message or passes it to the next message handler in the chain. The message is passed down the ordered chain of handlers until a handler can handle the message.  The first handler that can handle the message does so.  Each handler is only aware of the next handler.  The sender does not know who received the message.  The order of the handler list matters.

## Traditional Usage
- `Client` class uses a `IMessageHandler` interface. Concrete handler classes implement `IMessageHandler`
- Client and handlers form an ordered chain






# The Command Pattern
# Composite Pattern
# Decorator Design Pattern
# Event Aggregator
# Facade Pattern
# Flyweight
# Interpreter Pattern
# Iterator Pattern
# Lazy Load Pattern
# Mediator Pattern
# Memento
# Model View Presenter (MVP) Pattern
# Model View ViewModel (MVVM) Pattern
# Null Object Pattern
# Observer Pattern
# The Prototype Pattern
# Proxy Pattern
# Repository
# Singleton
# Service Locator Pattern
# State Pattern
# Strategy Pattern
# Template Method
# Unit of Work
# Visitor Pattern
# Rules Pattern
# Specification Pattern
