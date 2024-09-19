# Useful-Windows-Powershell-Power-Commands
Useful powerful Windows PowerShell scripts for everyone.

## Table of Contents _thank you Mistral for this table of contents_

- [PowerShell Command to Download and Extract Google Fonts and Nerd Fonts](#powershell-command-to-download-and-extract-google-fonts-and-nerd-fonts)
- [PowerShell Script to Disable Telemetry and Data Collection in Windows](#powershell-script-to-disable-telemetry-and-data-collection-in-windows)
  - [Script](#script)
  - [Enforce Settings Using Group Policy](#enforce-settings-using-group-policy)
  - [Usage](#usage)
- [PowerShell and Package Managers Setup Guide for Windows](#powershell-and-package-managers-setup-guide-for-windows)
  - [Updating or Installing PowerShell](#updating-or-installing-powershell)
    - [Installing the Stable Version of PowerShell](#installing-the-stable-version-of-powershell)
    - [Installing the Preview Version of PowerShell](#installing-the-preview-version-of-powershell)
  - [Installing Package Managers](#installing-package-managers)
    - [Installing Chocolatey](#installing-chocolatey)
    - [Installing wget](#installing-wget)
    - [Installing Scoop](#installing-scoop)
  - [Getting a Text Version of a Website](#getting-a-text-version-of-a-website)
- [Contributing](#contributing)
- [Acknowledgments](#acknowledgments)

# PowerShell Command to Download and Extract Google Fonts and Nerd Fonts

Certainly! Here is a single-line PowerShell command that downloads the latest master zip files for Google Fonts and Nerd Fonts, and then extracts them to `C:\temp\`:

```powershell
Invoke-WebRequest -Uri "https://github.com/google/fonts/archive/refs/heads/main.zip" -OutFile "C:\temp\google-fonts-main.zip"; Invoke-WebRequest -Uri "https://github.com/ryanoasis/nerd-fonts/archive/refs/heads/master.zip" -OutFile "C:\temp\nerd-fonts-master.zip"; Expand-Archive -Path "C:\temp\google-fonts-main.zip" -DestinationPath "C:\temp\google-fonts-main"; Expand-Archive -Path "C:\temp\nerd-fonts-master.zip" -DestinationPath "C:\temp\nerd-fonts-master"
```

## Disable telemetry, privacy, error reporting, the Customer Experience Improvement Program, and data collection. Additionally, it includes PowerShell commands to enforce these settings using Group Policy:


# PowerShell Script to Disable Telemetry and Data Collection in Windows

This PowerShell script focuses on disabling telemetry, privacy, error reporting, the Customer Experience Improvement Program, and data collection without affecting updates. Additionally, it includes PowerShell commands to enforce these settings using Group Policy.

## Script

```powershell
# Disable telemetry and data collection
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Name "AllowTelemetry" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Name "DoNotShowFeedbackNotifications" -Value 1
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Name "DisableApplicationTelemetry" -Value 1
```
```powershell
# Disable Windows Customer Experience Improvement Program
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\SQMClient\Windows" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\SQMClient\Windows" -Name "CEIPEnable" -Value 0
```
```powershell
# Disable Windows Error Reporting
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Windows Error Reporting" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Windows Error Reporting" -Name "DisableWindowsErrorReporting" -Value 1
```
```powershell
# Disable Windows Feedback
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Name "DoNotShowFeedbackNotifications" -Value 1
```
```powershell
# Disable Windows Defender telemetry
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows Defender" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows Defender" -Name "SpynetReporting" -Value 0
```
```powershell
# Disable Windows Tips
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\CloudContent" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\CloudContent" -Name "DisableWindowsConsumerFeatures" -Value 1
```
```powershell
# Disable Windows Spotlight
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Personalization" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Personalization" -Name "NoLockScreen" -Value 1
```

## Enforce Settings Using Group Policy

To prevent these settings from being reset with future updates, you can use PowerShell to enforce these settings using Group Policy. Here are the commands:

```powershell
# Disable telemetry and data collection
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Name "AllowTelemetry" -Value 0
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Name "DoNotShowFeedbackNotifications" -Value 1
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Name "DisableApplicationTelemetry" -Value 1
```
```powershell
# Disable Windows Customer Experience Improvement Program
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\SQMClient\Windows" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\SQMClient\Windows" -Name "CEIPEnable" -Value 0
```
```powershell
# Disable Windows Error Reporting
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Windows Error Reporting" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Windows Error Reporting" -Name "DisableWindowsErrorReporting" -Value 1
```
```powershell
# Disable Windows Feedback
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection" -Name "DoNotShowFeedbackNotifications" -Value 1
```
```powershell
# Disable Windows Defender telemetry
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows Defender" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows Defender" -Name "SpynetReporting" -Value 0
```
```powershell
# Disable Windows Tips
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\CloudContent" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\CloudContent" -Name "DisableWindowsConsumerFeatures" -Value 1
```
```powershell
# Disable Windows Spotlight
New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Personalization" -Force
Set-ItemProperty -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Personalization" -Name "NoLockScreen" -Value 1
```

## Usage

1. Open PowerShell as an administrator.
2. Copy and paste the script into the PowerShell window.
3. Press Enter to run the script.

_This script disables various telemetry, privacy, and data collection features in Windows 10 and 11 without affecting updates. Additionally, it enforces these settings using Group Policy to prevent them from being reset with future updates._

Certainly! Below is a Windows-only version of the README.md for a GitHub repository that includes instructions for updating or installing the preview or stable version of PowerShell, installing package managers (wget, Chocolatey, and Scoop), and getting a text version of a website.

# PowerShell and Package Managers Setup Guide for Windows

## Updating or Installing PowerShell

### Installing the Stable Version of PowerShell

```powershell
Invoke-Expression "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"
```

### Installing the Preview Version of PowerShell

```powershell
Invoke-Expression "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI -Preview"
```

## Installing Package Managers

### Installing Chocolatey

1. Open PowerShell as Administrator.
2. Run the following command:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

### Installing wget

```powershell
choco install wget
```

### Installing Scoop

1. Open PowerShell as Administrator.
2. Run the following command:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```

## Getting a Text Version of a Website

You can use `Invoke-WebRequest` in PowerShell to get the text version of a website.

```powershell
$url = "https://example.com"
$response = Invoke-WebRequest -Uri $url
$response.Content
```

This command will fetch the HTML content of the specified URL and display it as plain text.


## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## Acknowledgments

- [PowerShell Documentation](https://docs.microsoft.com/en-us/powershell/)
- [Chocolatey Documentation](https://chocolatey.org/docs)
- [Scoop Documentation](https://scoop.sh/)
