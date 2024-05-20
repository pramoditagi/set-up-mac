# Setting Up Your Mac for Development

This guide will walk you through setting up your Mac for software development. Whether you're a beginner or an experienced developer, these steps will help you get your environment ready for coding.

## Step 1: Install Xcode Command Line Tools

We don't need to install Xcode as we are not developing any Apple based applications. Instead we need Command Line Tools. This is required to run commands in Terminal. It's just a package which contains most of the commands.

To install Xcode Command Line Tools, just run the below code in Terminal.

Open Terminal and run the below command.

```bash
xcode-select --install
```

## Step 2: Install Homebrew

Homebrew is a popular package manager for macOS that makes it easy to install and manage software packages. To install Homebrew, open Terminal and run the following command.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the on-screen instructions to complete the installation.

## Step 3: Install Git

Git is a version control system used by many developers. You can install Git using Homebrew. In Terminal, run the below command.

```bash
brew install git
```

Verify the installation by checking the Git version.

```bash
git --version
```

We need to git setup username and email to keep track of the user who commits/saves the changes in Github.

To setup username and email in Git, run the following commands once the git is installed and verified.

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@yourdomain.com"
```

## Step 4: Install Node.js

If you're working with JavaScript or TypeScript, you'll need Node.js and npm (Node Package Manager). Install Node.js using Homebrew or directly you can install using [Download NodeJS](https://nodejs.org/en/download) and follow on screen instructions.

```bash
brew install node
```

Verify the installation using below commands:

```bash
node --version
npm --version
```

## Step 5: Install Visual Studio Code

Visual Studio Code (VS Code) is a popular code editor developed by Microsoft. It's lightweight, extensible, and great for web development. Download and install VS Code from the official website: [Visual Studio Code](https://code.visualstudio.com/) or install it using Homebrew using below command.

```bash
brew install --cask visual-studio-code
```

Follow on screen instructions and complete the installation.

Once the installation is complete, run the below command to verify if VS Code is installed properly and can be accessible through command line.

```bash
code .
```

## Step 6: Show branch name and present working directory in Terminal

Sometimes we might need to know on which branch we are working upon and what is the current directory where we are committing the changes.

Every time running the command like git branch or pwd is an unnecessary task.

To simplify this, copy and paste the below code in.zshrc pr .bashrc file and save it.

Open the .zshrc file using below command.

```bash
code ~/.zshrc
```

and paste the following code.

```bash
parse_git_branch() {
    git branch 2> /dev/null | sed -n -e 's/^\* \(.*\)/[\1]/p'
}
COLOR_DEF='%f'
COLOR_USR='%F{243}'
COLOR_DIR='%F{197}'
COLOR_GIT='%F{39}'

NEWLINE=$'\n'

setopt PROMPT_SUBST
export PROMPT='${COLOR_USR}%n@%M ${COLOR_DIR}%d ${COLOR_GIT}$(parse_git_branch)${COLOR_DEF}${NEWLINE}%% '
```

Once the code is saved in the file, just simply restart the Terminal. Voila! branch name and current directory will be visible in Terminal.

## Step 7: MySQL Installation Guide for macOS

This guide outlines the steps to install MySQL and MySQL Workbench on macOS using Homebrew.

##### Step 1: Check Available MySQL Versions

To check the available MySQL versions, run the following command in your terminal:

```
brew search mysql
```

This command will display the available MySQL versions. For example, you may see versions like `mysql@5.6`, `mysql@5.7`, or `mysql@8.0`.

##### Step 2: Choose and Install MySQL Version

Choose the desired MySQL version based on your requirements and execute the following command to install it. Replace `mysql@<version>` with the version you want to install (e.g., `mysql@5.6`):

```
brew install mysql@<version>
```

##### Step 3: Start MySQL Service

After installing MySQL, start the MySQL service using the following command, replacing `<version>` with the version you installed:

```
brew services start mysql@<version>
```

##### Step 4: Install MySQL Workbench

Install MySQL Workbench, a graphical tool for MySQL database development, using the following command:

```
brew install --cask mysqlworkbench
```

##### Step 5: Update MySQL Workbench (Optional)

To update the current MySQL Workbench installation to the latest version, use the following command:

```
brew upgrade mysqlworkbench
```

## Additional Resources

- [Official Xcode Documentation](https://developer.apple.com/xcode/)
- [Homebrew Documentation](https://docs.brew.sh/)
- [Git Documentation](https://git-scm.com/doc)
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [Visual Studio Code Documentation](https://code.visualstudio.com/docs)

---
