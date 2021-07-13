# practice-go

Following [Golang](golang.org)

## **Notes**

Create a go module

```sh
$ go mod init example.com/hello
```

#

Run go code, must be inside main()

```sh
$ go run .
```

#

Help for fo commands

```sh
$ go help
```

#

Install all dependencies

```sh
$ go mod tidy

```

#

Replace module import path

```sh
$ go mod edit -replace example.com/greetings=../greetings
```

#

> Exported function must bein Upper camel case and private in-file functions must be in lower camel case

#

> '\_' is blank identifier, similar to js

#

> Files ending with \_test tells go test command, it contains tests.

#

> Test function names have the form TestName, where Name says something about
> the specific test. Also, test functions take a pointer to the testing
> package's testing.T type as a parameter. You use this parameter's methods
> for reporting and logging from your test.

#

Run all tests in files with \_test suffix in a module

```sh
$ go test
```

#

Run all tests in files with \_test suffix in a module, verbose, more info

```sh
$ go test -v
```

#

To turn the porgram into an executable

```sh
$ go build
```

#

Outputs install path of go build

```sh
$ go list -f '{{.Target}}'
```

#

To set Windows Path env varibale with go bin address to run executables from any path in terminal

```sh
$ set PATH=%PATH%;C:\Users\DELL\go\bin\
```

#

To compile and install packages to bin

```sh
$ go install
```

#

> Every Go program is made up of packages.
> Programs start running in package main, specifically in func main()

#

> Import path convention: the package name is the same as the last element of the import path.
> Ex: "math/rand" package comprises files that begin with the statement package rand.

#

Factored import statement

```sh
import (
	"fmt"
	"math"
)
```

#

A name/func is exported if it begins with a capital letter
Exported

```sh
func Hello() {}
```

Unexported

```sh
func hello()
```

#

Function

```sh
func add(x int, y int) int {
	return x + y
}
```

#

Consecutive function params

```sh
x int, y int => x, y int
```

#

Ex: swap func

```sh
func swap(x, y string) (string, string) {
	return y, x
}
```

#

Named return Value

```sh
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}
```

> A return statement without arguments returns the named return values. This is known as a "naked" return.
> Only use naked returns in small func else will harm redability

#

Declaration var:

```sh
var c, python, java = true, false, "no!"
fmt.Println(i, j, c, python, java)
```

or using `:=` inside a func

```sh
c, python, java := true, false, "no!"
```

> Outside a function, every statement begins with a keyword (var, func, and so on) and so the := construct is not available.

#

Basic types

-   bool
-   string
-   int int8 int16 int32 int64
-   uint uint8 uint16 uint32 uint64 uintpt
-   byte // alias for uint8
-   rune // alias for int32 // represents a Unicode code point
-   float32 float64
-   complex64 complex128

#

Print: %T for type, %v for of bool, int, uint, byte, rune, float, complex, %q for string

```sh
fmt.Printf("Type: %T Value: %v\n", ToBe, ToBe)
```

#

Variables without explicit initialization get zero values

-   0 for numeric types,
-   false for the boolean type, and
-   "" (the empty string) for strings.

#

Type converstion

```sh
var i int
j := i // j is an int
```

#

> Const can't be declared with `:=`.

#

For: parts: init statement, consdition expression , post statement

```sh
for i := 0; i < 10; i++ {
    sum += i
}
```

or

```sh
sum := 1
for ; sum < 1000; {
    sum += sum
}
```

or (kinda like while)

```sh
sum := 1
for sum < 1000 {
    sum += sum
}
```

#

Infinite loop

```sh
for {
}
```

> Varibales declared in init statement are only scoped inside the loop

#

If:

```sh
if x < 0 {
    return sqrt(-x) + "i"
}
```

#

Initialization before if, scoped only inside it (if or else bock)

```sh
if v := math.Pow(x, n); v < lim {
    return v
} else {
    fmt.Printf("%g >= %g\n", v, lim)
}
```

#

Switch:

```sh
import (
	"fmt"
	"runtime"
)
switch os := runtime.GOOS; os {
    case "darwin":
        fmt.Println("OS X.")
    case "linux":
        fmt.Println("Linux.")
    default:
        // freebsd, openbsd,
        // plan9, windows...
        fmt.Printf("%s.\n", os)
}
```

> Doesn't need break in every case, added automatically. Sustitute for else if/elif.

#

Switch canall functions

```sh
switch i {
    case 0:
    case f():
}
```

#

Switch without condition is same as with condition true

```sh
switch {}
```

#

Defer: delays

```sh
func main() {
	fmt.Println("Wicked")
	defer fmt.Println("world")
	fmt.Println("hello")
	fmt.Println("Check")
}
```

Outputs:

```sh
Wicked
hello
Check
world
```

> The deferred call's arguments are evaluated
> immediately, but the function call is not executed
> until the surrounding function returns.

#

Defers are stacked:

````sh
func main() {
	fmt.Println("counting")

	for i := 0; i < 10; i++ {
		defer fmt.Println(i)
	}

	fmt.Println("done")
}
Outputs:
```sh

counting
done
9
8
7
6
5
4
3
2
1
0
````

#

> Stacked: function returns, its deferred calls are
> executed in last-in-first-out order

#

> Go has pointers. A pointer holds the memory address of a value.
> `*` => works like value at address
> `&` => address of

#

Assigning pointers

```sh
i := 42
p = &i
*p = 21 // i = 21
```

#

Struct

```sh
type Vertex struct {
	X int
	Y int
}
func main() {
	v := Vertex{1, 2}
	v.X = 4
	fmt.Println(v.X)
    // through pointer
    p := &v
	p.X = 1e9
	fmt.Println(v)
}
```

#

Array

```sh
var a [10]int
```

> Can't be resized

#

Array literal

```sh
[3]bool{true, true, false}
```

#

Slices

```sh
primes := [6]int{2, 3, 5, 7, 11, 13}
var s []int = primes[1:4] // [l,h] => l to h-1
fmt.Println(s)
```

#

> Slices are refferences, change slice, changes orignal array, like pointers

#

Slice literal

```sh
[]bool{true, true, false}
```

#

Defaults in slices

```sh
a[0:10]
a[:10]
a[0:]
a[:]
```

> default values are [0:length]

#

Slices: A slice has both a length and a capacity.

> Capacity of a slice is length or orignal array from which it is slices.

```sh
s := []int{2, 3, 5, 7, 11, 13}
len(s)
cap(s)
```

#

Reassign slices

```sh
s := []int{2, 3, 5, 7, 11, 13}
s = s[:0] // []
s = s[:4] // [2 3 5 7]

```

#

Slices: Nil

```sh
var s []int // s == nil
```

#

Create slices with make

```sh
a := make([]int, 5)  // len(a)=5
b := make([]int, 0, 5) // len(b)=0, cap(b)=5
b = b[:cap(b)] // len(b)=5, cap(b)=5
b = b[1:]      // len(b)=4, cap(b)=4
```

#

> Slices can contain any type, including other slices.

#

SLices: append

```sh
var s []int // []
s = append(s, 0) // [0]
s = append(s, 1, 2, 3, 4) // [0 1 2 3 4]
```

#

Range for loop

```sh
var pow = []int{1, 2, 4, 8, 16, 32, 64, 128}
func main() {
	for i, v := range pow {
		fmt.Printf("2**%d = %d\n", i, v)
	}
}
```

syntax

```sh
for i := range pow
for i, _ := range pow
for _, value := range pow
```

> Range return index and element

#

Maps: A map maps keys to values. Zero value is nil.

```sh
type Vertex struct {
	Lat, Long float64
}
var m map[string]Vertex
func main() {
	m = make(map[string]Vertex)
	m["Bell Labs"] = Vertex{
		40.68433, -74.39967,
	}
	fmt.Println(m["Bell Labs"])
}
```

#

Map Literals

```sh
type Vertex struct {
	Lat, Long float64
}

var m = map[string]Vertex{
	"Bell Labs": Vertex{
		40.68433, -74.39967,
	},
	"Google": Vertex{
		37.42202, -122.08408,
	},
}
var m = map[string]Vertex{
	"Bell Labs": {40.68433, -74.39967},
	"Google":    {37.42202, -122.08408},
}
```

#

Mutating Maps
insert

```sh
m[key] = elem
```

Retrieve

```sh
elem = m[key]
```

Delete

```sh
delete(m, key)
```

Test if key is present

```sh
elem, ok = m[key]
```

or

```sh
elem, ok := m[key]
```

> ok is true, if key exists, false otherwise and elem is zero value.

#

Assign function as values

```sh
hypot := func(x, y float64) float64
```

#

Functions are closures

```sh
func adder() func(int) int {
	sum := 0
	return func(x int) int {
		sum += x
		return sum
	}
}
```

#

#

## To Dos

-   What is a lsice?
-   What is panicking?

-   Study later:
    -   https://golang.org/doc/effective_go#multiple-returns
    -   https://blog.golang.org/maps
