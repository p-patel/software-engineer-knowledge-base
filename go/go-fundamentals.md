# Go Fundamentals
https://app.pluralsight.com/course-player?clipId=239ad4b1-f10c-4349-ad95-0eea5070577f

## Course Introduction
### What We'll Cover In This Course
- Theory and Hands-on Code
- Reviewing Docker's Go github repo

## Introducing Go
### Explaining Go
- Written by Robert Griesemer, Rob Pike, Ken Thompson
- Open-source
- Started as a systems language
- Like C, but simpler
- Inc. garbage collection
- ~25 language keywords

### Installing Go on Windows
- Use Windows installer or Chocolatey

## Hello World
### Setting Up Our Workspace
- 3 workspace dirs - `.\src`, `.\packages` and `.\bin`
- set workspace env var in System Variables `GOPATH`.  check with `go env` command

### Writing Our First Program
- create `.\src\hello-world.go`
- `package main` creates an executable binary
- `func main() { }` program entrypoint (no arguments)

### Functions Primer
- first-class citizens in Go
- `func <name>(<args>) { <code> }

### Printing Hello World
- `import ("fmt" "runtime")`, then `fmt.Println("Hello from", runtime.GOOS)`

### Running Our First Program
- ```
cd %GOPATH%
go run hello-world.go
```

### Recap and More Detail
- Go is case-senstive
- exported names must start with an uppercase letter
- C-style comments syntax

## Variables and Constants
### Module Intro







