# Getting Started with Go

## Dependency tracking
The `go.mod` file is used for dependency tracking, by running the following command in the CLI, Go will generate the file for you. Note that the module's "module path" is the location where your source code will be kept, e.g. `github.com/{YOUR_ORG}/{REPO_NAME}`

```shell
$ go mod init example.com/hello
```

## Hello World!
```go
// hello.go
package main

import "fmt"

func main() {
	fmt.Println("Hello, World!")
}
```
> [See `hello.go` source code](./hello/hello.go)

Three things happen in this sample `hello.go` file...
1. The first line declares a package `main`, packages are how functions are grouped together. This declaration is important as it tells Go to compile the package as an executable instead of a shared library. 
1. The next declaration is an import of the `fmt` package, which is useful when handling text and printing it to the console.
1. The entrypoint for the executable is contained in `func main()`.
	- **NOTE**: Shared libraries will not have any `main` package nor `main` function in the package.

## Importing remote modules
By importing a module in your file...

```go
import "rsc.io/quote"
```
> module found on [https://pkg.go.dev](https://pkg.go.dev/rsc.io/quote)

And running the command in the CLI...

```shell
$ go mod tidy
```

Go will fetch the resources and create/update a `go.sum` file which contains checksums (cryptographic hashes of the module's direct and indirect dependencies) for validating that what is downloaded into the module cache matches the dependencies required to run the module. This is very important when it comes to sharing your module / compiling on a remote server.


## Creating a module to share
All Go modules have the same basic composition.
- Go code is grouped into packages
- Packages are grouped into modules.
- Your module specifies dependencies needed to run your code, including the Go version and the set of other modules it requires.
- As modules are extended and updated, their "version" changes, this is to ensure that each module can be checked for compatability with other functions in a package and upgraded only as needed.
- **NOTE**: A function with a Capitalized first letter can be called by a function not in the same package.
- When writing functions with parameters, you have to declare the parameter type.
- Functions that return a value require that you declare the return type.
- the `:=` operator is a shortcut for declaring and initializing a variable in one line, the type of the value on the right sets the variable type.


