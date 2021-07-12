# practice-go

Following [Golang](golang.org)

## Notes

Create a go module

```sh
$ go mod init example.com/hello
```

Run go code, must be inside main()

```sh
$ go run .
```

Help for fo commands

```sh
$ go help
```

Install all dependencies

```sh
$ go mod tidy

```

Replace module import path

```sh
$ go mod edit -replace example.com/greetings=../greetings
```

> Exported function must bein Upper camel case and private in-file functions must be in lower camel case

> '\_' is blank identifier, similar to js

> Files ending with \_test tells go test command, it contains tests.

> Test function names have the form TestName, where Name says something about
> the specific test. Also, test functions take a pointer to the testing
> package's testing.T type as a parameter. You use this parameter's methods
> for reporting and logging from your test.

Run all tests in files with \_test suffix in a module

```sh
$ go test
```

Run all tests in files with \_test suffix in a module, verbose, more info

```sh
$ go test -v
```

To turn the porgram into an executable

```sh
$ go build
```

Outputs install path of go build

```sh
$ go list -f '{{.Target}}'
```

To set Windows Path env varibale with go bin address to run executables from any path in terminal

```sh
$ set PATH=%PATH%;C:\Users\DELL\go\bin\
```

To compile and install packages to bin

```sh
$ go install
```

## To Dos

What is a lsice?
What is panicking?

Study later:
https://golang.org/doc/effective_go#multiple-returns
https://blog.golang.org/maps
