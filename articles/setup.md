# Setting up your computer

Getting your tools right is an important step in becoming a developer. This guide will walk you through every step you need to take.

There are multiple options that can be used when setting up your computer. This guide is opinionated about those options. Our guidelines are:

- When possible, use what you already have instead of installing something new.
- Use the most common development tool unless it is deficient.
- Less setup is better.

## Update your system

Before anything else, update your operating system. To do that, go to the **Apple Menu > About This Mac > Software Update**.

## Security settings

Open **System Preferences > Security & Privacy** and set the following:

- Under General, set *require a password after sleep or screen saver begins to immediately*.
- Under General, set *disable automatic login*.
- Click Advanced… and select *Require an administrator password to access system-wide preferences*.
- Under Firewall, click *Turn Firewall On*.
- Under FileVault, enable *FileVault*. This will encrypt your disk. Without it, anyone with a bootable USB drive can get full access to your computer.

## iTerm2

iTerm2 is an open source replacement for Apple’s Terminal. It is highly customizable and comes with a lot of useful features.

You can get the app from the [iTerm2 downloads page](http://www.iterm2.com/downloads.html). Once downloaded, drag and drop the iTerm application file into your Applications folder.

**NOTE:** Run iTerm now to open a terminal window. For the rest of this guide, when we ask you to run something in the terminal or “on the command line”, we will be referring to typing the command into an iTerm terminal window and pressing Enter. We will often just say “run” with a command beneath, like this:

```
$ cd ~
```

When you see these commands, do not paste the `$`. This dollar sign is there to indicate the terminal prompt.

## XCode

XCode is a set of developer tools from Apple that have to be installed. To install them, go to the App Store and search for XCode, then install it. This is a big package and will take quite a while.

Once XCode is installed, run the following in your terminal:

```
$ sudo xcodebuild -license
$ xcode-select --install
```

The first line will prompt you to read the license and agree to it. It will ask for your password. The second line will prompt you to install the command line tools. Follow the instructions and you’ll have Xcode and Xcode command line tools both installed.

## Homebrew

[Homebrew](https://brew.sh/) calls itself “The missing package manager for macOS” and is an essential tool for any developer.

To install Homebrew, paste the following command in your terminal, hit Enter, and follow the steps on the screen:

```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

To be able to use Homebrew you need to start a new terminal session. Do this by opening a new terminal tab with Cmd+T (you should also close the old one), then run the following command to make sure everything is working:

```
$ brew doctor
```

### Using Homebrew

To install a package (or formula in Homebrew vocabulary) simply run:

```
brew install <formula>
```

To update Homebrew’s directory of formulae, run:

```
brew update
```

To see if any of your packages need to be updated:

```
brew outdated
```

To upgrade a package:

```
brew upgrade <formula>
```

To see what you have installed (with their version numbers):

```
brew list --versions
```

## Git and GitHub

If you do not yet have a [GitHub](https://github.com/) account, go there and register for one.

[Git](http://git-scm.com/) is the version control tool we will use in class to manage your code. To install it, run:

```
$ brew install git
```

When done, to test that it installed correctly, you can run:

```
$ git --version
```

And `which git` should output `/usr/local/bin/git`.

Next, we’ll define your Git user (this should be the same name and email you use for GitHub):

```
$ git config --global user.name "Your Name Here"
$ git config --global user.email "your_email@youremail.com"
```

This data will get added to your `.gitconfig` file.

To push code to your GitHub repositories, we’re going to use the recommended HTTPS method. So you don’t have to type your username and password every time, enable Git password caching:

```
$ git config --global credential.helper osxkeychain
```

Lastly, you want to make sure git uses a text editor that is easier for you to use than the default one. Type the following command:

```
$ git config --global core.editor nano
```

### Git and .DS_Store files

On a Mac, it is important to remember to add `.DS_Store` (a hidden macOS system file that’s put in folders) to your `.gitignore` files.

Configure your Git to globally exclude those files:

```
# specify a global exclusion list
$ git config --global core.excludesfile ~/.gitignore
# adding .DS_Store and other Mac-specific files to that list
$ curl https://raw.githubusercontent.com/github/gitignore/master/Global/macOS.gitignore -o ~/.gitignore
$ echo .vscode >> ~/.gitignore
```

### Git and the command line

We want to add two things to your command line: the ability to autocomplete Git commands and information about Git to your prompt. To do this, run:

```
$ brew install zsh-completions starship
$ echo 'fpath=(/usr/local/share/zsh-completions $fpath)' >> ~/.zshrc
$ echo 'eval "$(starship init zsh)"' >> ~/.zshrc
```

Exit the terminal and start a new window. Your command line should now look like this:

```
~
>
```

## Node.js

When we work with JavaScript, we will often need to use tools written with Node.js. To install Node, run:

```
$ brew install node
```

Once this is done, you should be able to run the following commands and get output like this:

```
$ node --version
v13.13.0

$ npm --version
6.14.4
```

The exact versions may be different; ensure Node is v13 and above and npm is v6 and above.

## Python

Python has two different major versions, Python 2 and Python 3. We will use Python 3 throughout this course. While Python 3 is widely used, Python 2 is the default still on OS X, so we will have to install Python 3, as well as a tool we will use throughout the course to manage Python projects, poetry. To install these, run:

```
$ brew install python3 poetry
```

Once this is done, you should be able to run the following commands and get output like this:

```
$ python3 --version
Python 3.7.7

$ poetry --version
Poetry version 1.0.5
```

## Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/) (VSCode) is the program we will primarily use to edit code. To install it, run:

```
$ brew cask install visual-studio-code
```

## Google Chrome

Google Chrome is the browser we will use in class. To install it, run:

```
$ brew cask install google-chrome
```
