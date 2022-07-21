# Mac Development Laptop

This readme holds my notes for setting up a new development laptop,
using all the tools applicable for my current projects.
All steps are based on Mac machine.

## Install BREW

```bash
xcode-select —-install

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

```

## Install BREW Packages

Run the following command from within the folder of the `Brewfile`

```bash
brew bundle
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

## Install PowerShell Depenencies

<https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-macos?view=powershell-7.1#installing-dependencies>

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
npm install -g aws-sso-cli
```

## Install Python packages

```bash
pip3 install git-remote-codecommit
pip3 install cfn-lint
pip3 install taskcat

```

## Configure GIT

```bash
git config --global user.name "<NAME>"
git config --global user.email "<E-mail>"
git config --global pull.rebase false
git config --global --add --bool push.autoSetupRemote true
```

## Configure Visual Studio Code

Configure VS Code Settings Sync

## .zshrc

```bash
aws-sso-cli() {
  command aws-sso-cli "$@" | while read -r line; do
    if [[ $line =~ ^export ]]; then
      eval $line
    fi
  done
}
```

## TODO

* terraform-docs
* Configure default env. variables

```bash
BROWSER=true
AWS_DEFAULT_REGION=eu-west-1
```
