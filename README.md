# Setting Up Your Mac for Development

This guide will walk you through setting up your Mac for software development. Whether you're a beginner or an experienced developer, these steps will help you get your environment ready for coding.

## Contents

1. [Xcode Command Line Tools](#step-1-install-xcode-command-line-tools)
2. [Homebrew](#step-2-install-homebrew)
3. [Git](#step-3-install-git)
4. [Node JS](#step-4-install-nodejs)
5. [Yarn](#step-5-install-yarn)
6. [MySQL](#step-6-install-mysql)
7. [MySQL Workbench](#step-7-install-mysql-workbench)
8. [Ruby Version Manager](#step-8-install-rvm-ruby-version-manager)
9. [Ruby](#step-9-install-ruby)
10. [Rails](#step-10-install-rails)
11. [Visual Studio Code](#step-11-install-visual-studio-code)
12. [Branch name and PWD in Terminal](#step-12-show-branch-name-and-present-working-directory-in-terminal)
13. [Additional Resources](#additional-resources)

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

## Step 5: Install Yarn

Yarn is the package manager to install JavaScript dependencies. We can use yarn to add, remove, update or configure the packages in our project.

First, you need to install Yarn using homebrew package manager. Use below command.

```bash
brew install yarn
```

Verify the installation using below command:

```bash
yarn --version
```

## Step 6: Install MySQL

MySQL is an open-source relational database management system (RDBMS) essential for running MySQL queries and managing databases. To streamline the process, we use MySQL Workbench, a user-friendly UI application that allows for direct query execution and database management.

Installing MySQL is crucial for our development environment since many of our applications rely on it. MySQL is widely used in the industry and offers compatibility with most deployment tools, making it a reliable choice for our projects.

To install MySQL, we are using homebrew. Run below commands.

```bash
brew search mysql
brew install mysql@8.0
```

Once installation is complete, just run below commands in terminal.

```bash
echo 'export PATH="/opt/homebrew/opt/mysql@8.0/bin:$PATH"' >> ~/.zshrc
export LDFLAGS="-L/opt/homebrew/opt/mysql@8.0/lib" 
export CPPFLAGS="-I/opt/homebrew/opt/mysql@8.0/include"
brew services start mysql@8.0
```

After this, close and reopen the terminal. To verify MySQL version, run below command.

```bash
mysql --version
```

After this, to start command line MySQL, run below command.

```bash
mysql -uroot
```

## Step 7: Install MySQL Workbench

After installing MySQL, it's essential to install MySQL Workbench. It is a GUI based application which can be used to run the queries, view tables, export data and many more actions through GUI.

Writing queries manually in terminal sometimes becomes difficult task as queries will be not be saved. We can use MySQL Workbench to perform all these and it's very easy to use as well.

To install MySQL Workbench, just run below command.

```bash
brew install --cask mysqlworkbench
```

Once the installation gets successful, open the MySQL Workbench application and set up database name, port, user and password etc.

## Step 8: Install RVM (Ruby Version Manager)

RVM is the Ruby Version Manager, a package manager to manage ruby versions in the system.

To install RVM, we need following things.

- GPG: GNU Privacy Guard is required to verify RVM installation keys.

Install gnupg using Homebrew:

```bash
brew install gnupg2
```

#### Steps to Install RVM

##### 1. Import the RVM GPG Keys:

To securely download and verify the RVM installation, you'll need to import the following GPG keys:

```bash
curl -sSL https://rvm.io/mpapis.asc | gpg --import -
curl -sSL https://rvm.io/pkuczynski.asc | gpg --import -
```

##### 2. Install RVM:

Once the keys are imported, run the following command to install RVM:

```bash
\curl -sSL https://get.rvm.io | bash -s stable
```

After this, follow onscreen instruction to load RVM into the shell session.

To verify whether RVM is installed properly or not, run the below command to verify.

```bash
rvm -v
```

You can check list of known versions of ruby (ruby, jruby, mruby etc.) by running below command.

```bash
rvm list known
```

## Step 9: Install Ruby

Ruby is an interpreted, high-level, general-purpose programming language. We are installing Ruby as we will be working on building Ruby projects.

Above are the prerequisites for installing Ruby in Mac.

### Note

RVM's stable branch hasn't been updated in years, so it doesn't include recent patches or support for newer dependencies like openssl@3. RVM’s head version has seen more active updates, including fixes for OpenSSL compatibility on macOS.

Here’s how to switch to the latest head version of RVM, which should include recent patches and improved support for OpenSSL on macOS

1. Get the Latest RVM (Head):
    This command will pull the latest version directly from the RVM repository, including the most recent patches and fixes:

    ```bash
    rvm get head
    ```

2. Reload RVM:
    Reload RVM to apply the updates:

    ```bash
    rvm reload
    ```

3. Now, you can install any desired version of ruby into the system using RVM.
    Run the below command to install ruby version 3.2.2 using RVM with openssl 3.

    ```bash
    rvm install ruby-3.2.2 -C --with-openssl-dir=/usr/local/etc/openssl@3
    ```

Once the installation gets successful, you can verify the list of ruby versions installed by RVM in your system by running below command.

```bash
rvm list
```

If you have installed multiple versions of ruby, all those will be listed there.

Now, verify the ruby version installed in your system by running below command.

```bash
ruby -v
```

If =\* is pointing to any of the ruby version, it means it's the default and current version of ruby which is pointing to in the system.

If there are multiple versions of ruby present in your system and if you want to set one particular version as the default version, then use --default flag with the below command.

```bash
rvm use 3.2.2 --default
```

Sometimes, we might need to use different versions of ruby as per the projects which have different versions of ruby. In that case, run below command to use the required version of ruby.

```bash
rvm use ruby-{specify-the-version}
```

Now, we have installed ruby version in the system.

## Step 10: Install Rails

Rails is a web application development framework written in the Ruby programming language. It is designed to make programming web applications easier by making assumptions about what every developer needs to get started. It allows you to write less code while accomplishing more than many other languages and frameworks.

In Rails, Gems means packages. Rails is also a package or gem. We are using rails gem to develop web applications or APIs.

Before installing Rails, we need to install Bundler.

### Install Bundler

Bundler provides a consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed.

To install bundler gem, run the following command.

```bash
gem install bundler
```

Once the installation gets successful, run the below command to verify the installed version.

```bash
bundler -v
```

#### Install Rails

To install rails, run the below command.

```bash
gem install rails
```

This will install the latest version of rails. If you want specific version of rails to be installed, then use the -v flag in the command like below.

```bash
gem install rails -v 7.1
```

We are using 7.1 version of rails as it is compatible with Ruby version 3.1.

Once the rails installation completes, run the following command to verify.

```bash
rails -v
```

Now, we are good for ruby on rails development and build projects on them.

## Step 11: Install Visual Studio Code

Visual Studio Code (VS Code) is a popular code editor developed by Microsoft. It's lightweight, extensible, and great for web development. Download and install VS Code from the official website: [Visual Studio Code](https://code.visualstudio.com/) or install it using Homebrew using below command.

```bash
brew install --cask visual-studio-code
```

Follow on screen instructions and complete the installation.

Once the installation is complete, run the below command to verify if VS Code is installed properly and can be accessible through command line.

```bash
code .
```

## Step 12: Show branch name and present working directory in Terminal

Sometimes we might need to know on which branch we are working upon and what is the current directory where we are committing the changes.

Every time running the command like git branch or pwd is an unnecessary task.

To simplify this, copy and paste the below code in.zshrc or .bashrc file and save it.

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

## Additional Resources

- [Official Xcode Documentation](https://developer.apple.com/xcode/)
- [Homebrew Documentation](https://docs.brew.sh/)
- [Git Documentation](https://git-scm.com/doc)
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [Yarn Documentation](https://classic.yarnpkg.com/lang/en/docs/)
- [MySQL Documentation](https://dev.mysql.com/doc/)
- [MySQL Workbench Documentation](https://dev.mysql.com/doc/workbench/en/)
- [Ruby Version Manager](https://rvm.io/)
- [Ruby](https://www.ruby-lang.org/en/documentation/)
- [Rails](https://guides.rubyonrails.org/getting_started.html)
- [Visual Studio Code Documentation](https://code.visualstudio.com/docs)

---
