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
## What's In This Module?
- CRUD using objects
- Querying using Find and SQLQuery
- Working with Graphs of Related Data
- Project Queries

## Inserting Objects
- Use `Add()` \ `AddRange()` to add domain objects against a DbSet of a DbContext
- `context.Database.Log` property used to configure logging
- `Database.SetInitializer(new NullDatabaseInitializer<NinjaContext>())` to disable database initialisation by EF (useful for production environments)
- EF will add each new object using a separate `INSERT` db query, third-party libs available to improve performance by inserting objects in a single query
- SQL Profiler / EF Profiler tools

## Querying Simple Objects
- Query DbSet of a DbContext
- Query using LINQ methods or LINQ syntax
- LINQ queries with hard-coded queries will produce SQL queries with hard-coded query conditions, LINQ queries with parameters will produce parameterised SQL
- Enumerating a query in a `foreach` will execute the query, NB. the db connection will remain open for the entire `foreach` code block so minimise the code in this block

## Updating Modified Objects
- Update object in connected model, then call `context.SaveChanges()`
- Update object in disconnected model, then use context.Entry(object).State` to set objects state, otherwise a DbContext will not be able to identify an object retrieved using a different DbContext has been modified

## Retrieving Data with the Find and SqlQuery Methods
- `.Find(keyval)` looks for object using the key field, will not query the db if the matching object already exists in DbContext (`Find()` uses `SingleOrDefault()` to query objects) 
- `context.SomeObject.SqlQuery()` to run queries/sprocs (returned data must match object shape)

## Deleting Simple Objects
- `Remove()` sets an objects to be deleted when `context.SaveChanges()` is called
- In disconnected model, use `dbContext.Entry(object).State` to set object state to delete an object. This requires querying the db for a record, just to set the object for deletion
- Alternatively, `context.Database.ExecuteSqlCommand()` - a sproc is used and a key value provided. Note `context.Database` is used to execute sql command here, not a DbContext's DbSet

## Inserting Related Data
- Set related object properties, EF will track and save the related object data in the db according to the defined model

## Loading Related Data
- Eager loading - specify related model objects to always load using `DbSet.Include()`
- Explicit loading - load related model objects explicitly using `context.Entry(object).Collection(i => i.ObjectProperty).Load();`
- Lazy loading - set property that is to be lazily loaded to be `virtual`.  EF will overload the class property to load property data when required by model queries. **This requires performance analysis as the queries can become expensive**
- Projections covered next...

## Projection Queries
- Specify properties in the LINQ select clause to define a custom projection that does not map to the data object shape.  This is returned as a .NET anonymous type













