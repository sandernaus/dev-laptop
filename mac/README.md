# Windows Development Laptop

This readme holds my notes for setting up a new development laptop,
using all the tools applicable for my current projects.
All steps are based on Mac machine.

## Install BREW

```bash
xcode-select —-install

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

```

## Install BREW Packages

```bash
brew install bundle
brew install cask
brew install core
brew install --cask firefox
brew install --cask google-chrome
brew install --cask telegram
brew install --cask visual-studio-code
brew install --cask whatsapp
brew install --cask spotify
brew install --cask microsoft-edge
brew install --cask powershell
brew install --cask postman
brew install --cask dotnet
brew install python
brew install azure-cli
brew install awscli
brew install node
brew install docker
brew install --cask iterm2
brew install pyenv
```

## Install Oh My ZSH

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Configure Oh My ZSH Theme and fonts

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k

sed -i "s/ZSH_THEME=.*/ZSH_THEME=powerlevel10k\/powerlevel10k/g" ~/.zshrc

git clone https://github.com/powerline/fonts.git

cd fonts

./install.sh
```

## Install PowerShell Modules

```bash
Install-Module Az -AllowClobber

Install-Module Azure -AllowClobber
Install-Module AzureRM -AllowClobber
```

## Install Node packages

```bash
npm i -g tfx-cli
npm install aws-cdk
```

## Install Python packages

```bash
pip3 install git-remote-codecommit
pip3 install cfn-lint

```

## Configure GIT

```bash
git config --global user.name "<NAME>"
git config --global user.email "<E-mail>"
git config --global pull.rebase false
```

## Configure Visual Studio Code

Configure VS Code Settings Sync

## TODO

* terraform
* terraform-docs
* Configure default env. variables

```bash
BROWSER=true
AWS_DEFAULT_REGION=eu-west-1
```
