# Windows Devops Tools

This repository contains configuration files and scripts enabling engineers to consistently setup their Windows 10 22H2/11 workstation for continuous delivery oriented development.

## Install Chocolatey package manager

Chocolatey has been prefered to WinGet because as it usually is up-to-date with version released by upstream projects.

Start a Windows Powershell prompt **as an Administrator**, then run the following command line to install [Cholatey Package Manager](https://chocolatey.com)

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

## Install Application packages

The [`chocolatey/packages.config`](/chocolatey/packages.config) XML file contains the list of software packages to be installed.
To install a specific version of a package.
Run first `choco list --exact 'package_name' --all` to identify available versions, then amend the version to the appropriate line in [`chocolatey/packages.config`](/chocolatey/packages.config) file.

Start a _New_ Windows Powershell prompt **as an Administrator**, then run the following command line to install all packages recored in the inventory file.

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/fjudith/windows-devops-tools/main/chocolatey/install.ps1'))
```

## Install Visual Studio Code extensions

The [`visual-studio-code/extensions.txt`](/visual-studio-code/extensions.tx) TXT file contains the list of Visual Studio Code (VsCode) extensions to be installed.

From a Windows Powershell prompt, run the following command line to install all extensions recorded in the inventory file.

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/fjudith/windows-devops-tools/main/visual-studio-code/install.ps1'))
```
