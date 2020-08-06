# The Go Programming Language - Alan Donovan, Brian Kernighan

## Preface

- http://blog.golang.org

...

## Tutorial
### 1.1 Hello World
- Book source code repo at https://gopl.io
- Examples to demonstrate the Go way of writing code; avoid bias of writing code in styles from previous languages
- Go natively handles Unicode
- an unused package import will result in a compiler error
- effectively new lines are convered into semicolons so where newlines are placed matters for parsing of Go code
- see `gofmt` tool, `gofmt fmt` subcommand; `goimports` tool
> What does `gofmt fmt` do?

> What does `goimports` do?

### 1.2 Command-Line Arguments
- Go uses half-open intervals - includes the first index but excludes the last index
- Either index omitted in `s[m:n]` defaults to either 0 or len(s)
- Review Go statement/expression definitons
> Complete exercises

### 1.3 Finding Duplicate Lines


