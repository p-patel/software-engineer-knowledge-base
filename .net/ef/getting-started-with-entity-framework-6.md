GETTING STARTED WITH ENTITY FRAMEWORK 6

# Overview of Entity Framework 6

## Why EF? Why This Course?
- Handles the data storage and retrieval concern
- Timeline: ADO -> ADO.NET -> EF (ORM)
- EF provides a consistent API

## What's In This Course?
- High level view of EF6
- Creating a model with code
- Using DBContext API between model and db
- Using model & EF in client & server apps

- EF6 or EF7?

## What's In The Module?
- ORM
- EF vs other ORMs - typically map from Domain Classes -> DB
- EF provides great flexibility in the mappings between domain models and DB schema - Domains Classes -> mappings <- DB schema

## EF Goals
- Productivity - Provides a framework to work with data, rather than building own custom data access layer
- First-class member of .NET stack and open source
- Work with data using consistent LINQ syntax.  LINQ also works with any other in-memory objects
- Abstracts storage of relational data, db connections, commands etc. Work with domain model objects

## Where to Use EF6?
- .NET Framework >= 3.5
- Applications, server-side services
- Also available for use on mobile devices (storage and access data directly on the device)

## High Level Look at How EF Works
- Domain classes
- DBContext API used to define model (e.g. db table/field names) and relationships
- LINQ queries on entity class objects are translated to db-specific queries using a DB Provider (queries also work with db views and sprocs)
- Query is executed and results translated to populate domain model class objects
- EF tracks changes to in-memory model
- Changes are inferred and updates executed in db on call to DBContext's SaveChanges()

## Visual or Code Based From Scratch or Existing DB
- 3 approaches to create data model:
- #1 Model-first - create model using designer tool, saved as EDMX (Entity Domain Model XML) file. Create DB or generate model code from this visual model
- #2 DB-first (legacy tool) - create visual model from DB (one-time only, no migrations on DB changes) or generate code model from DB
- #3 Code-first (most popular) - create model in code.  Create DB (i.e. DB script) from code and continue to manage changes to DB schema using Code Migrations scripts
- Using Code-first approach, conventions are used to map code model names/properties to the DB schema and for indexes and table constraints

## Where EF Fits In Your Software Architecture
- EF is referenced within the Data Logic component/layer of an application only
- The DbContext wraps DOs in the Conceptual Model within this data logic
- Business logic, application logic, domain models and UI are unaware of EF and do not reference it

## From Inception To EF6: A Short History
- 2008 - EF1 with .NET Framework 3.5 / VS2008 SP1 - Domain classes coupled with EF
- 2011 - EF4 with .NET Framework 4.0 - POCO domain classes (decoupled from EF). Code First API and DbContext add-ons as Nuget packages
- 2012 - EF5 with .NET Framework 4.5
- 2013 - EF6 - EF as a Nuget package released separately from .NET framework and open sourced

## EF7 is Coming, But EF6 Is Staying Too
- EF7 (EF Core 1.0) - EF rewrite (not backwards compatible)
- EF6 will continue to be supported
- EF7 supports non-relational data

## Summary

## Resources
- Pluralsight courses
- EF7 Development Site: github.com/aspnet/entityframework
- Blog: thedatafarm.com/blog
- EF Team Blog: blogs.msdn.com/adonet

# Creating a Code-based Model and Database
- 



