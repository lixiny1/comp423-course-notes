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






