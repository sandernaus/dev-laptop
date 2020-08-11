# Laptop setup

## Install Chocolatey

```powershell
Set-ExecutionPolicy AllSigned
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

## Install packages

* Windows Terminal
* Microsoft ToDo
* Spotify
* Edge Chromium
* Whatsapp

```cmd
choco install git
choco install vscode
```

## Installing WSL

Check the Windows version by executing following command from command prompt

```cmd
ver
```

WSL 2 requires: Windows 10, updated to version 2004, Build 19041 or higher.

Install WSL

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
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



## Installing Windows Terminal

```powershell
choco install microsoft-windows-terminal
```

## Style windows terminal for PowerShell and WSL

https://medium.com/@hjgraca/style-your-windows-terminal-and-wsl2-like-a-pro-9a2e1ad4c9d0

settings.json

## Install VS Code

```powershell
choco install vscode
```

## Get VS Code config


## Vagrant plugins

```cmd
vagrant plugin install vagrant-rsync-back
vagrant plugin install  vagrant-serverspec
vagrant plugin install  vagrant-vbguest
```

## Git config

```cmd
git config user.name "My Name" --global
git config user.email "my@email.com" --global
