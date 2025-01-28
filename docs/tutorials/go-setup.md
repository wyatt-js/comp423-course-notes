# Go Setup
* Primary author: [Wyatt Smith](https://github.com/wyatt-js)

## Prerequisites
* Some Programming Experience (like knowing about functions)
* Install VSCode
* A Command Terminal (any terminal on Linux and Mac, or PowerShell or cmd in Windows)

## Setting Up a Dev Container for Go
* Start by creating a directory for your Go project with the following command:
```
mkdir [name of project]
cd [name of project]
```
* Initialize a git repository for version control:

`git init`

* Connect your local repository to the remote repository:

`git remote add origin [repository-url]`

* Install the Visual Studio Code Dev Containers Extension
* Create the .devcontainer folder and configuration file
```
mkdir .devcontainer
cd .devcontainer
touch devcontainer.json
```
* Configure the file with the following code (fill in project name in last line):
```
{
  "name": "Go Dev Container",
  "image": "mcr.microsoft.com/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "extensions": [
        "golang.go"
      ]
    }
  },
  "settings": {
    "go.gopath": "/go",
    "go.useLanguageServer": true
  },
  "postCreateCommand": "go mod init [my-go-project]",
}
```

* Such code does the following:
    * Names your dev container
    * Specifies the Microsoft Go Dev Container base image
    * Installs the official Go VS Code plugin
    * Sets the Go workspace path and enables the Go language server
    * Initializes a Go module for the project upon container creation

* Start the dev container by selecting the following option in the VSCode Command Palette:

`> Dev Containers: Reopen in Container`

## Creating a New Project
* Create a file [name].go in which to write your code
* Add the following to the file to create the output, "Hello COMP423":
```
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```
* Such code does the following:
    * Declares a main package
    * Imports the fmt package to allow printing to the console.
    * Implements a main function to print a message to the console.
* Use the following command to compile and run the package:

`go run .`


## Subcommands
### Version Subcommand
* The version subcommand is used to check the installed version of Go:

`go version`
### Mod Subcommand
* The mod subcommand is used to track dependencies for your code. A go.mod file will track the modules that provide packages to your code. The following command will create the file:

`go mod init [module path]`

* Fill in [module path] with the path of the module that your code will be in.
### Run Subcommand
* The run subcommand is used to compile and run the go package defined as main. The following command will run the main package in the working directory:

`go run .`
### Build Subcommand
* The build subcommand is used to compile a Go package into a binary executable file.

`go build [package name]`

* This is similar to running the following command on a C file:

`gcc [file name]`

* The produced executable file can then be run with the following commands:

```
./hello # (Linux/Mac)
hello.exe  # (Windows)
```

This is different from the run command in that it produces and saves an executable file, whereas run does not save an executable, but only runs it.