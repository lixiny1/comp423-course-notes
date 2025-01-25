# Setting Up a Dev Container for Go
Primary author: Lixin Yang (https://github.com/lixiny1)

## Prerequisites 
### Software Requirements
* Create a **Github** account and make sure **Git** is installed
* Install **Visual Studio Code**
* Install **Docker** and make sure it's running
### Basic Knowledge
* Make sure to be familiar with **command line basics**! (COMP 211)
* Some basic understanding of **Go** and its syntax would be useful


## Part 1: Creating a New Directory
1. Open a terminal on your laptop
2. Create a new blank directory and switch to it:
```
mkdir hello-comp423
cd hello-comp423
```
3. Initialize a new Git repository. This will initialize your folder with a new, empty repository!
```
git init
```

## Part 2: Creating a Dev Container
1. Open up the newly created `hello-comp423` directory in **VS Code**
2. Press `Ctrl-Shift-P` (or `Cmd-Shift-P` if on Mac) and search for **Dev Containers: Add Dev Container Configuration Files**
3. Select **Add configuration to workspace** and select **Go** from the dropdown menu. This will add a `devcontainer.json` file to your folder!

## Part 3: Configuring the Dev Container File
1. Take a look at the `devcontainer.json` file.
    * **"name"** refers to the name of your Dev Container. In this case, the name is **"Go Dev Container"**.
    * **"image"** refers to the base image from Microsoft with Go installed.
    * Under **extensions**, we specify for the `golang.go` VSCode plugin to be installed. This will allow us to work with `.go` files within VSCode.
    * **"postCreateCommand"** will run `go version` and tell you what version of Go is running after you create the container and run this file.
    * Here is an example of what your `devcontainer.json` file should look like:
```
{
    "name": "Go Dev Container",
    "image": "mcr.microsoft.com/devcontainers/go:1-bullseye",
    "customizations": {
        "vscode": {
            "extensions": [
                "golang.go"
            ]
        }
    },
    "postCreateCommand": "go version"
}
```
!!! note
    Make sure to double check that you are installing the official Go VSCode Plugin! The code above should download the correct version.

## Part 4: Creating Go Module
1. Open up a terminal in VSCode within the Dev Container and run the following command:
```
go mod init hello-comp423
```
This command sets up the current directory as the root of a new Go module. The `go.mod` file is the center of this module and allows you to modify any dependencies that you may have.

## Part 5: Creating Your First Program!
1. Within your dev container, create a new directory called **docs**. This is where we will be storing our Go programs.
```
mkdir docs
cd docs
```
2. Create a new Go file called **main.go** within the **docs** directory. This file will contain our first Go program!
```
touch main.go
```
3. Navigate to the **main.go** file. 
```
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```
* **package main** describes the package your code is in

!!! note
     The main package in Go is special because it defines the entry point into the program.

* **fmt** is a package that we are instructing to install when this program runs. **fmt** is a standard library package in Go used in **formatting I/O**, such as printing to a console.





