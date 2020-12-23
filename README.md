# Development Laptop

This readme holds my notes for setting up a new development laptop,
using all the tools applicable for my current projects.
All steps are based on Windows 10 machine.

## Install Chocolatey

```powershell
Set-ExecutionPolicy AllSigned
Set-ExecutionPolicy Bypass -Scope Process -Force; `
  [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol `
  -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

## Install Packages

* Microsoft ToDo

```cmd
choco install git -y --params "/NoAutoCrlf"
choco install vscode -y --params "/NoDesktopIcon"
choco install microsoft-windows-terminal -y
choco install whatsapp -y
choco install telegram -y
choco install spotify -y
choco install microsoft-edge -y
choco install 7zip -y
choco install python -y
choco install postman -y
choco install rsat -y -params '"/AD /GP /DNS /FS"'
choco install azure-cli -y
choco install virtualbox -y --params "/NoDesktopShortcut /ExtensionPack"
choco install vagrant -y
choco install awscli -y
choco install nodejs -y

vagrant plugin install vagrant-rsync-back
vagrant plugin install vagrant-serverspec
vagrant plugin install vagrant-vbguest

git config --global user.name "My Name"
git config --global user.email "my@email.com"

ssh-keygen -t rsa -C  "my@email.com"

Install-Module Az -AllowClobber
Install-Module Azure -AllowClobber
Install-Module AzureRM -AllowClobber

pip install git-remote-codecommit
pip install cfn-lint
```

## Configure Visual Studio Code

Configure VS Code Settings Sync plugin

## Installing WSL

Check the Windows version by executing following command from command prompt

```cmd
winver
```

WSL 2 requires: Windows 10, updated to version 2004, Build 19041 or higher.

Install WSL

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux `
  /all /norestart
```

Install WSL2 by enabling VirtualMachinePlatform feature, restart and changing to
default version 2

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
shutdown -f -r -t 0
wsl --set-default-version 2
```

Download the Linux distribution

```powershell
Invoke-WebRequest -Uri https://aka.ms/wslubuntu2004 -OutFile ubuntu_2004.appx -UseBasicParsing
Add-AppxPackage .\ubuntu_2004.appx
```

Launch Ubuntu from start menu for username and password configuration

For configuring a proxy in WSL, refer to this [document](cntlm.md)

### TODO: Section for installing packages in WSL

* Ansible
* ansible-lint
* Python 3
* yamllint

## Configure Windows Terminal

### Configure settings

Copy `settings.json` from this directory to:
`C:\Users\%USERNAME%\AppData\Local\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json`

### Style windows terminal for PowerShell and WSL

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Clone Powerline Fonts
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts

# Download monoki fonts
Invoke-WebRequest -Uri `
  https://github.com/ryanoasis/nerd-fonts/releases/download/v2.0.0/Mononoki.zip `
  -Outfile Mononoki.zip -UseBasicParsing

7z e Monoki.zip

.\install.ps1


Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser

# Start the default settings (might not work so optional)
Set-Prompt
# To enable the engine edit your PowerShell profile, run
notepad $PROFILE
# and append the following lines to the profile file you just opened (or created
# in case the file was not there already):
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme Paradox
```

WSL Configuration in Windows Terminal:

```sh
sudo apt-get install zsh curl git

# When prompted to set zsh as your default shell say Yes
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k

sed -i "s/ZSH_THEME=.*/ZSH_THEME=powerlevel10k\/powerlevel10k/g" ~/.zshrc

# Restart and follow configuration
```

Source: <https://medium.com/@hjgraca/style-your-windows-terminal-and-wsl2-like-a-pro-9a2e1ad4c9d0>
