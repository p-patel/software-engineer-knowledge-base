# Learn Go Programming - Golang Tutorial for Beginners
https://www.youtube.com/watch?v=YS4e4q9oBaU

## Variables
- variable declaration and initialisation options
- function vs package variables
- cannot redeclare variables within the same scope (however variable shadowing is possible)
- cannot declare unused variables - results in a compiler error
- variable naming - lowercase first letter scoped to package, uppercase first letter visible outside of package
- variable naming convention - short-lived variables tend to have short names; longer-lived longer, more descriptive names; acronyms are all in uppercase
- explicit type conversion functions, **NB. int to string conversions are done using functions in the `strconv` package**. `string(anIntVariable)` will encode the stream of bytes to their Unicode characters which typically is not what is intended

## Primitives
- boolean, numeric and text types
- default zero-value initialisations
### Boolean
- `var n bool = false`
### Numerics
- signed ints - `int`, `int8`, `int16`, `int32`, `int64`, unsigned ints - `uint8`/`byte`, `uint16`, `uint32`
- both operands of an arithmetic operation must be of the same type
- arithmetic operations will return result of the same type as operands
- bit operators - `&` (AND), `|` (OR), `^` (XOR), `&^` (AND NOT aka bit clear)
- bit shifting - `a << x`, `a >> x` shift a left/right x places
- floating point types - IEEE-754 standard `float32`, `float64` e.g. `var n float64 = 13.7e72`, `var n float32 - 2.1E14`
- complex number types - `complex64` (32-bit real, imaginary parts), `complex128` (64-bit real, imaginary parts) e.g. `var n complex64 = 1 + 2i`, `var n complex64 = 2i`, use with `real(n)`, `imag(n)` and `complex(5, 12)` functions.
### Text
- text types - `string` (UTF-8). **NB. strings are aliases for bytes**, strings are immutable, `+` for string concatenation
- can convert strings to collection (slice) of bytes using `b := []byte(s)`, lots of functions in Go work with generic byte slices rather than strings
- `rune` any UTF-32 character (use single-quotes), is an alias for `int32`

## Constants
- naming convention `const myConst int = 42` - no difference in casing to variable names
- constant values must be calculable at compile-time, e.g. not the result of a function call
- constants can be shadowed inc. a different type (just like variables)
- type inference (just like variables)
- untyped constants in Go will replace the constant value separately in every expression in the program, using appropriate type inference in each expression.  **Therefore the same constant value may be inferred as a `int16` in one expression and a `int64` in another expression**
- enumerated constants - `iota`, `_`
- enumerated expressions - using `iota` expressions

## Control Flow
### If statements
- simple example (curly braces are **NOT** optional)
```
if true {
  fmt.Println("This test is true")
}
```
- with an initialiser (initialiser is added before the semicolon and the if statement's boolean expression after the semicolon.  Note that the initialised variables are scoped to the if block
```
if pop, ok := statePopulations["Florida"]; ok {
  fmt.Println(pop)
}
```
- comparison example
```
if guess < number {
  fmt.Println("Guess is too low!")
}
if guess > number {
  fmt.Println("Guess is too high")
}
if guess == number {
  fmt.Println("You got it!")
}
```
- logical operators - `||`, `&&`, `!`
```
if guess < 1 || guess > 100 {
  fmt.PrintLn("The guess must be between 1 and 100")
}
```
- short-circuiting - when one condition in a `||` statement returns turn (or one condition in a `&&` statement returns false) the remaining conditions are not checked
- if, else
```
if guess < 1 || guess > 100 {
  fmt.PrintLn("The guess must be between 1 and 100")
} else {
  // do some other stuff here
}
```
- if, else if, else
```
if guess < 1 {
  fmt.PrintLn("The guess must be 1 or greater")
} else if guess > 100 {
  fmt.PrintLn("The guess must be 100 or less")
} else {
  // do some other stuff here
}
```
### Switch statements
- example, switch statements do not 'fall-through' by default
```
switch 2 {
case 1:
  fmt.Println("one")
case 1:
  fmt.Println("two")
default:
  fmt.Println("not one or two")
}
```
- compare with a range (cases number be unique, otherwise will cause a compiler error)
```
switch 2 {
case 1, 5, 10:
  fmt.Println("one, five or ten")
case 2, 4, 6:
  fmt.Println("two, four or six")
default:
  fmt.Println("another number")
}
```
- switch initialiser (same as in if statements)
```
switch i:= 2 + 3; i {
}
```
- tagless syntax (cases can overlap, first match will execute)

- fall-through cases - use `fallthrough`


















