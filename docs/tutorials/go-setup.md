# Setting Up a Dev Container for Go
Primary author: Lixin Yang (https://github.com/lixiny1)

Reviewer: Ezra Heinberg (https://github.com/ezra45)

## Prerequisites 
### Software Requirements
* Create a [Github](https://github.com) account and make sure [Git](https://git-scm.com/downloads) is installed
* Install [Visual Studio Code](https://code.visualstudio.com/download)
* Install [Docker](https://www.docker.com/) and make sure it's running
### Basic Knowledge
* Make sure to be familiar with **command line basics**! (COMP 211)
* Some basic understanding of **Go** and its syntax would be useful


## Part 1: Creating a New Directory
1. Open a terminal on your laptop
2. Create a new blank directory and switch to it:
``` bash
mkdir hello-comp423
cd hello-comp423
```
3. Initialize a new Git repository. This will initialize your folder with a new, empty repository!
``` bash
git init
```


4. Create a remote repository in Github (instructions by Kris Jordan)
    * Log into your Github account and go to the **Create a New Repository** page
    * Fill in these details:
        * **Repository Name:** ```go-tutorial```
        * **Description:** "A short program written in Go!"
        * **Visibility:** Public
    * Click the box that adds a README.md file during this stage. You will need it later!
    * Click Create Repository.

5. Link your Local Repository to GitHub

```shell
git remote add origin https://github.com/<your-username>/go-tutorial.git
```

* Replace ```<your-username>``` with your GitHub username.

* Check your default branch name with the subcommand ```git branch```. If it's not ```main```, rename it to ```main``` with the following command: ```git branch -m main```.

* Push your local commits to the GitHub repo:

```shell
git push --set-upstream origin main
```
!!! info
    What is ```--set-upstream```?

    ```git push --set-upstream origin main``` pushes the main branch to the remote repository origin. The ```--set-upstream``` flag sets up the main branch to track the remote branch, meaning future pushes and pulls can be done without specifying the branch name and just writing ```git push origin``` when working on your local ```main``` branch. The corresponding short flag is ```-u```.

* In your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use ```git log``` locally to see the commit ID and message which should match the ID of the most recent commit on GitHub.



## Part 2: Creating a Dev Container

1. Open up the newly created `hello-comp423` directory in **VS Code** through File -> Open Folder
2. Press `Ctrl-Shift-P` (or `Cmd-Shift-P` if on Mac) and search for **Dev Containers: Add Dev Container Configuration Files**
3. Select **Add configuration to workspace** and select **Go** from the dropdown menu. This will add a `devcontainer.json` file to your folder!
4. Click **"Reopen in Dev Container"** if the pop up appears on the screen. If not, press `Ctrl-Shift-P` (or `Cmd-Shift-P` if on Mac) and search up **Dev Container: Reopen in Dev Container**

## Part 3: Configuring the Dev Container File
1. Take a look at the `devcontainer.json` file.
    * **"name"** refers to the name of your Dev Container. In this case, the name is **"Go Dev Container"**.
    * **"image"** refers to the base image from Microsoft with Go installed.
    * Under **extensions**, we specify for the `golang.go` VSCode plugin to be installed. This will allow us to work with `.go` files within VSCode.
    * **"postCreateCommand"** will run `go version` and tell you what version of Go is running after you create the container and run this file.
    * Here is an example of what your `devcontainer.json` file should look like:
``` bash
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
``` bash
go mod init hello-comp423
```
This command sets up the current directory as the root of a new Go module. The `go.mod` file is the center of this module and allows you to modify any dependencies that you may have.

## Part 5: Creating Your First Program!
1. Within your dev container, create a new directory called **docs**. This is where we will be storing our Go programs.
``` bash
mkdir docs
cd docs
```
2. Create a new Go file called **main.go** within the **docs** directory. This file will contain our first Go program!
``` bash
touch main.go
```

!!! note
    The main package in Go is special because it defines the entry point into the program.

3. Navigate to the **main.go** file. 

    * `package main` describes the package your code is in

    * `fmt` is a package that we are instructing to install when this program runs. **fmt** is a standard library package in Go used in **formatting I/O**, such as printing to a console.

    * `func main` describes the main function within this particular Go program. `func` is the function declaration keyword, and `main` is the name of the function that are running. 
    * `fmt.Println("Hello COMP423)` will utilize the `fmt` package you downloaded to print **"Hello COMP 423"** to your console as output. 
``` bash
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

4. Verify your Go version with the following command in your terminal to make sure that you're running the correct version
``` bash
go version
```


4. Open up the terminal and run the **main.go** program with the following command:
``` bash
go run main.go
```
Congratulations! You just wrote and ran your first Go program! However, we do have a few more things to cover.

5. Run the following line of code in your terminal:
``` bash
go build -o hello
```
Previously, running `go run main.go` simultaneously compiled and executed your program in 1 step. This is nice for testing, but doesn't leave behind a compiled binary file that you can distribute and run on any compatible system that doesn't have Go downloaded. To do that, we need the **build** command. The above line of code (**build**) will generate your **main.go** program into an executable file named `hello`. 

Now you have an executable file of your first Go program!

6. If you would like to push your changes to your local Github repository, use the following commands:
``` bash
git switch main
git add .
git commit -m "Completed first Go program!"
git push
```

Congratulations! You just created and pushed your first Go program to your repository. Now you can continue learning and coding in Go to do more cool things.






