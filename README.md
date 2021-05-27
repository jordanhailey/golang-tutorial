# Getting Started with Go

## Dependency tracking
The `go.mod` file is used for dependency tracking, by running the following command, Go will generate the file for you. Note that the module's "module path" is the location where your source code will be kept, e.g. `github.com/{YOUR_ORG}/{REPO_NAME}`

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


