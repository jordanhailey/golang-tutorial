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


