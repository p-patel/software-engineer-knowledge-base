# Concurrency In Go - Tools & Techniques for Developers

## CH. 2 Modelling Your Code: CSP

## CH. 4 Concurrency Patterns in Go
### Confinement
> What are the four options for safe concurrent operation?
>> 1. Synchronise access to shared memory (e.g. mutex)
>> 1. Synchronise communication (e.g. channels)
>> 1. Immutable data
>> 1. Data protected by confinement

- Confinement ensures data is only ever available from *one* concurrent process
- Ad-hoc vs lexical confinement
- Establishing confinement allows you to write synchronous code within that context (simpler, reduced cognitive load)

### The for-select Loop
Usage:
- sending iteration variables out on a channel
- looping infinitely waiting to be stopped

### Preventing Goroutine Leaks
- goroutines are not garbage-collected - don't leave them lying about our process
- use a `done` channel in child goroutine to signal it to terminate, child goroutine can also communicate successful termination back to parent on a `terminated` channel
- use the same pattern for sending (channel) goroutine as well as receiving (channel) goutine
- *if a goroutine is responsible for creating a goroutine, it is also responsible for ensuring it can stop the goroutine* - all techniques build on the foundation of passing a `done` channel

### The or-channel
- or-channel pattern

### Pipelines
- Properties of a pipeline stage:
  - consumes and returns the same type
  - must be reified by the language so that is may be passed around (e.g. funcs in Go)
- pipeline stages are closely related to functional programming (higher order functions and monads) pipeline stages can be considered a subset of monads
