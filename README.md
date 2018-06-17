# Mac Setup

## INSTALL & SETUP BASH SHELL

Run the following command to change/verify that you are using Bash.

> `chsh -s /bin/bash`

You will need to quit and re-launch your Terminal for the shell change to take effect.

Now you need to verify that you have the correct `bash` configurations in place.

Change to your home directory

`cd ~`

Make sure you have a ~/.profile

`touch ~/.profile`

Prefer ~/.profile over ~/.bash_profile

`[[ -f ~/.bash_profile ]] && cat ~/.bash_profile >> ~/.profile && rm -f ~/.bash_profile`

Make sure you have a ~/.bashrc

`touch ~/.bashrc`

Make sure ~/.bashrc is being sourced in ~/.profile

`echo 'source ~/.bashrc' >> ~/.profile`



## INSTALL HOMEBREW & PYTHON

Homebrew, by default, installs to /usr/local. Run these commands if you are going to use the default. **DO NOT run these commands if you are customizing the install location**

`sudo mkdir -p /usr/local`
`sudo chown -R $(whoami):admin /usr/local/`

Install Homebrew

`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

Get Homebrew-Cask

`brew tap caskroom/cask`

Install Python 3

`homebrew install python3`

Add Python tools to PATH in ~/.bashrc

`echo 'export PATH=/Library/Frameworks/Python.framework/Versions/3.6/bin:${PATH}' >> ~/.bashrc`

Source ~/.bashrc for the update to take effect

`source ~/.bashrc`

Install pip (pip3) for python3

`cd ~/Downloads`
`curl -Lks -o ./get-pip.py -- https://bootstrap.pypa.io/get-pip.py`
`python3 ./get-pip.py --trusted-host pypi.org --trusted-host files.pythonhosted.org`
`rm -f ./get-pip.py`

Install Xcode Command Line Tools -- https://developer.apple.com/library/content/technotes/tn2339/_index.html

`xcode-select --install`


## APPLICATIONS

#### iTerm2

#### SourceTree

Optional, setup github ssh keys

`https://help.github.com/articles/connecting-to-github-with-ssh/`

#### Git for Mac

(Source tree will prompt you to install it)

#### VSCode

`https://code.visualstudio.com/docs/setup/mac`

 - Install ability to open Code in terminal https://code.visualstudio.com/docs/setup/mac 
 - Install plugins
    - Angular Essentials Pack (John Papa's collection for Angular dev)
    - ESLint
    - VSCode Great Icons
    - Python
        
#### Java9 (Optional???)
    
- Download and install the latest Oracle JDK8 version for macOS from here http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

#### NodeJS 8.x

If you use Node Version Manager(nvm), it does not make a node binary available on the PATH by default.
Download and install the latest 6.x version from here https://nodejs.org/en/download/

#### nvm

https://github.com/creationix/nvm




# MAINTENANCE

Update Homebrew
`brew update && brew upgrade && brew cleanup`

Upgrade pip3
`pip3 install --upgrade pip setuptools wheel --trusted-host pypi.org --trusted-host files.pythonhosted.org`

Upgrade Node
`here`

Upgrade npm
`npm install npm@latest -g`



