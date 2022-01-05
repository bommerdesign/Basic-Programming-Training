# Install java
## Install on Windows
Just download the `exe` find and execute to install [from here](https://www.java.com/en/download/help/windows_manual_download.xml)

## Install on MacOS
> Using [Homebrew](../../tools/docs/linux-commands/readme.md)
```
brew update
brew install homebrew/cask/java 

# verify it
brew cask info java

```

> [Using dmg file](https://docs.oracle.com/javase/10/install/installation-jdk-and-jre-macos.htm#JSJIG-GUID-F9183C70-2E96-40F4-9104-F3814A5A331F)

## Install on Ubuntu (version 18.04)
```sh
sudo apt update
sudo apt install default-jdk

# Verify 
java -version
```
