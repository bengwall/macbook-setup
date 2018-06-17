# Mac Setup

## INSTALL & SETUP BASH SHELL

Run the following command to change/verify that you are using Bash.
- `chsh -s /bin/bash`

You will need to quit and re-launch your Terminal for the shell change to take effect.

Now you need to verify that you have the correct `bash` configurations in place.

Change to your home directory
- `cd ~`

Make sure you have a ~/.profile
- `touch ~/.profile`

Prefer ~/.profile over ~/.bash_profile
- `[[ -f ~/.bash_profile ]] && cat ~/.bash_profile >> ~/.profile && rm -f ~/.bash_profile`

Make sure you have a ~/.bashrc
- `touch ~/.bashrc`

Make sure ~/.bashrc is being sourced in ~/.profile
- `echo 'source ~/.bashrc' >> ~/.profile`



## INSTALL HOMEBREW, PYTHON, NODE

### Homebrew

Homebrew, by default, installs to /usr/local. Run these commands if you are going to use the default. **DO NOT run these commands if you are customizing the install location**
- `sudo mkdir -p /usr/local`
- `sudo chown -R $(whoami):admin /usr/local/`

Install Homebrew
- `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

Get Homebrew-Cask
- `brew tap caskroom/cask`

#### Python

Install Python 3
- `brew install python3`
- If you get an errors that `brew` cannot be found, then run this to update the patch `export PATH=/usr/local/bin:$PATH`, then reload bash `source ~/.bashrc`.

Add Python tools to PATH in ~/.bashrc
- `echo 'export PATH=/Library/Frameworks/Python.framework/Versions/3.6/bin:${PATH}' >> ~/.bashrc`

Source ~/.bashrc for the update to take effect
- `source ~/.bashrc`

Install pip (pip3) for python3
- `cd ~/Downloads`
- `curl -Lks -o ./get-pip.py -- https://bootstrap.pypa.io/get-pip.py`
- `python3 ./get-pip.py --trusted-host pypi.org --trusted-host files.pythonhosted.org`
- `rm -f ./get-pip.py`

#### nvm

- https://github.com/creationix/nvm
- `curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash`

Source ~/.bashrc for the update to take effect
- `source ~/.bashrc`

#### NodeJS 8.10.0 (AWS version)

If you use Node Version Manager(nvm), it does not make a node binary available on the PATH by default.
Download and install the latest 6.x version from here https://nodejs.org/en/download/

- `nvm install 8.10.0`
- `npm install -g npm`

#### Java9 (Optional???)
    
- Download and install the latest Oracle JDK8 version for macOS from here http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html



## APPLICATIONS

#### iTerm2

#### SourceTree

Optional, setup github ssh keys

- `https://help.github.com/articles/connecting-to-github-with-ssh/`

#### Git for Mac

- (Source tree will prompt you to install it)

#### VSCode

-  `https://code.visualstudio.com/docs/setup/mac`
  - Install ability to open Code in terminal https://code.visualstudio.com/docs/setup/mac 
  - Install plugins
    - Angular Essentials Pack (John Papa's collection for Angular dev)
    - ESLint
    - VSCode Great Icons
    - Python
        



# NVM HELP

List your installed node versions:
- `nvm list`

List the available node versions in the cloud:
- `nvm ls-remote`

You can use the combination of this two commands to see only the last 9 lines from the huge list of versions: 
- `nvm ls-remote | tail -n9`

It is safe if you choose one of the most recent LTS (long time support) version and install it with the following command:
- `nvm install 10.3.0`

Setup this version as the default.
- `nvm use 10.3.0`
- `nvm alias default 10.3.0`

Check your node version with
- `node -v`

You can update your npm to the latest.
- `npm install -g npm`
- After the update, the npm version, npm -v, should be at least 6.1.0 or above.

A little extra tip. Remember for the following command because it simplifies the update process. ;)

Let’s say, you would like to stay on the stable, LTS version and you would like to keep all the global package what you’ve already installed. Here is the solution:
- `nvm install 8 --reinstall-packages-from=8 --latest-npm`
- It updates your Node.js version to the latest version 8 and install the latest npm, plus it setup all your previously installed global packages.





# MAINTENANCE

Update Homebrew
- `brew update && brew upgrade && brew cleanup`

Upgrade pip3
- `pip3 install --upgrade pip setuptools wheel --trusted-host pypi.org --trusted-host files.pythonhosted.org`

Clean npm cache
- `sudo npm cache clean -f`


