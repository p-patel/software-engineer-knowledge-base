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
- bit shifting - `<< x`, `>> x` shift left/right x places
- floating point types - IEEE-754 standard `float32`, `float64` e.g. `var n float64 = 13.7e72`, `var n float32 - 2.1E14`
- complex number types - `complex64` (32-bit real, imaginary parts), `complex128` (64-bit real, imaginary parts) e.g. `var n complex64 = 1 + 2i`, `var n complex64 = 2i`, use with `real(n)`, `imag(n)` and `complex(5, 12)` functions.
### Text
- text types - `string` (UTF-8). **NB. strings are aliases for bytes**, strings are immutable, `+` for string concatenation
- can convert strings to collection (slice) of bytes using `b := []byte(s)`, lots of functions in Go work with generic byte slices rather than strings
- `rune` any UTF-32 character (use single-quotes), is an alias for `int32`













