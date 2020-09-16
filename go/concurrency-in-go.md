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
