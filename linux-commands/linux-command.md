# 37 common linux command you should study
This is a good article teach you about how to use 37 common command lines in linux (same for OSX, unix)

[Check tutorial here](https://www.howtogeek.com/412055/37-important-linux-commands-you-should-know/)


# How to set up a apps/tools on linux/unix.

**MacOS**
 ____
- In Mac OS, you can install via `App Store` or command line.
- To install app by the command line, you can use `brew` ([Homebrew](https://brew.sh/): is Package Manager for MacOS)

```sh
# First, you’ll need the command-line tools for Xcode installed. this is reqired before you can use most of the commands
xcode-select --install

# Install Homebrew
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"


# Install Graphical Apps With Homebrew Cask

# SEARCH APP NAME
brew search <app-name>
brew search java

# INSTALL APP
brew cask install <app-name>
# ex
brew cask install java

# REMOVE APP
brew remove name
ex: brew install java

```

- Or you can install manualy by bash command via instruction of the app (just some)

**Linux (Ubuntu)**
___________________________

Similar MacOS, Ubuntu has Synaptic Package Manager like App store, you can install the application by GUI.

But you can also install the app by the command line, use `apt` (apt is package manager on Ubuntu)

```sh
# fetch the latest app information for repository
sudo apt update

# INSTALL APP
apt install <app-name>
# ex
apt install default-jre

```

> Similar, in other os systems, we have another Package Manager for that OS.
> such as Windows is [chocolatey](http://chocolatey.org/packages), Centos is `Yum`, etc

[Next: File permission, process and port](./others.md)