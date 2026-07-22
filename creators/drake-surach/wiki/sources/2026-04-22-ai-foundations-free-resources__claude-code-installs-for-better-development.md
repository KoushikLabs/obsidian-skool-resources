---
title: "Claude Code Installs for Better Development"
date: 2026-04-22
creator: drake-surach
course: AI Foundations Free Resources
source_url: https://aifoundations.io/resources/claude-code-installs-for-better-development
has_resource: false
type: source
concepts:
  - trading-bots
  - cloud-deployment
entities:
  - anthropic
  - claude-code
  - github
---

# Claude Code Installs for Better Development

> Course: **AI Foundations Free Resources**

## Links
- Lesson: https://aifoundations.io/resources/claude-code-installs-for-better-development
- Creator: [[drake-surach-profile]]

## Cross-references
**Concepts:** [[trading-bots]], [[cloud-deployment]]
**Entities:** [[anthropic]], [[claude-code]], [[github]]

## External links
- [https://www.skool.com/ai-foundations](https://www.skool.com/ai-foundations) — `external`
- [https://vimeo.com/1160544954](https://vimeo.com/1160544954) — `external`

## Page content

🔴 April Hackathon Live in Ai Foundations! ($350 cash prizes)
Learn more
Products
Resources
K
Koushik Raghavan
Back to Resources
CLAUDE
CLAUDE CODE
Claude Code Installs for Better Development
7 min read
Copy as Markdown
mandatory installs
Get started using Claude Code
Before development begins, let's install the necessary things in order to get up and running.
Above is a sneak-peak module from our flagship:
Claude Code Mastery Course!
This will get you set-up and ready to begin developing with Claude whether you are on Windows or Mac!
Installations Required
Watch the guide above and the stuff below will make more sense.
Attention Windows Users!
Scroll down this page to the windows installation.
Mandatory Installs on Mac
Open your terminal on Mac to run these commands.
1.) XCode Command Line Tools
Check if it's installed
Terminal
Copy
xcode-select -p
Install it if needed
Terminal
Copy
xcode-select --install
Make sure you have Git now
Terminal
Copy
git --version
2.) Homebrew
Check if it's installed
Terminal
Copy
which brew
Install it if needed
Terminal
Copy
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
Option 1: Add PATH for (Apple Silicon Macs)
Terminal
Copy
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
Source it
Terminal
Copy
source ~/.zshrc
Option 2: Add PATH for (Intel Macs)
Terminal
Copy
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zshrc
Source it
Terminal
Copy
source ~/.zshrc
3.) VS Code
Check if it's installed
Terminal
Copy
which code
Install it if you don't have it
Terminal
Copy
brew install --cask visual-studio-code
Verify that it's installed
Terminal
Copy
code --version
4.) Github CLI
Check if it's installed
Terminal
Copy
which gh
Install it if you don't have it
Terminal
Copy
brew install gh
Authenticate your Github account
Terminal
Copy
gh auth login
Verify that it's installed
Terminal
Copy
gh --version
Verify that your authentication worked
Terminal
Copy
gh auth status
5.) Node.js
Check if node and npm are installed
Terminal
Copy
node --version
Terminal
Copy
npm --version
Install them if not
Terminal
Copy
brew install node
Verify that they are installed
Terminal
Copy
node --version
Terminal
Copy
npm --version
6.) Claude Code
Check if it's installed
Terminal
Copy
claude --version
Install it if not
Terminal
Copy
npm install -g @anthropic-ai/claude-code
Verify it's installed
Terminal
Copy
claude --version
Troubleshooting if it still doesn't show up...
First try sourcing, then check the version again after this command:
Terminal
Copy
source ~/.zshrc
If it still doesn't work you'll have to check your path for the npm install
Terminal
Copy
npm config get prefix
Then use the portion of the install to add it to your shell
Terminal
Copy
echo 'export PATH="$(npm config get prefix)/bin:$PATH"' >> ~/.zshrc
Restart your terminal, and source it again
Terminal
Copy
source ~/.zshrc
Verify it's installed
Terminal
Copy
claude --version
Login if you haven't yet (Sometimes I've noticed it logs in using your Claude Desktop account automatically so you may not have to do this)
Terminal
Copy
claude login
7.) Python
Try python3 and python to see if they are installed, also check pip and pip3
Terminal
Copy
python3 --version
Terminal
Copy
pip3 --version
If python3 doesn't work try these ones
Terminal
Copy
python --version
Terminal
Copy
pip --version
If it still doesn't appear to be found you'll have to install python
Terminal
Copy
brew install python@3.12
Then verify if it's working again... it should now work.
Source Command
This command is useful to refresh the paths to your tools, you can always use this command if you install something and it doesn't show up, then try again. Restarting your terminal and running this command after a restart can also be helpful in some cases.
Terminal
Copy
source ~/.zshrc
Troubleshooting for Installations using VISI Protocol
(Version, Install, Source, Iterate)
When installing tools, remember the VISI protocol:
1.) Check the version. --version or -v
2.) Install if the version doesn't exist.
3.) Source your shell.
4.) Iterate (Start from step one and if it's installed the version should appear)
Step 5... if it's still not working make a comment on the support thread below this module with your questions and a clear problem statement and we will get you help asap.
Mandatory Installs on Windows
Step 1: Open PowerShell How to open PowerShell on Windows:
Option 1 (Easiest):
Press Windows key + X
Click "Windows PowerShell" or "Terminal"
Option 2:
Click Start Menu
Type "PowerShell"
Click "Windows PowerShell"
Option 3:
Press Windows key + R
Type "powershell"
Press Enter
Important: For some installations, you'll need Administrator access:
Right-click on PowerShell
Select "Run as Administrator"
Click "Yes" when prompted
Step 2: Check Your Windows Version Once PowerShell is open, check your Windows version to know which package manager to use
Powershell
Copy
winver
A popup will show your Windows version (Windows 10, Windows 11, etc.)
Step 3: Package Manager Setup
For Windows 11 Users: Windows 11 comes with winget pre-installed. Check if you have it:
Powershell
Copy
winget --version
If this works, skip to step 4. You'll use winget for all installations.
For Windows 10 and Earlier: You need to install Chocolatey as your package manager.
Check if Chocolatey is already installed
Powershell
Copy
choco --version
Install Chocolatey if needed (Run PowerShell as Administrator)
Powershell
Copy
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
Restart PowerShell and verify
Powershell
Copy
choco --version
Step 4: Git for Windows Check if it's installed
Powershell
Copy
git --version
Install it if needed
Windows 11 (using winget):
Powershell
Copy
winget install Git.Git
Windows 10 and earlier (using Chocolatey):
Terminal
Copy
choco install git
Or download from git-scm.com and install it.
Verify that it's installed
Terminal
Copy
git --version
Step 5: VS Code Check if it's installed
Powershell
Copy
code --version
Install it if you don't have it
Windows 11 (using winget):
Powershell
Copy
winget install Microsoft.VisualStudioCode
Windows 10 and earlier (using Chocolatey):
Powershell
Copy
choco install vscode
Verify that it's installed
Powershell
Copy
code --version
Step 6: GitHub CLI Check if it's installed
Powershell
Copy
gh --version
Install it if you don't have it
Windows 11 (using winget):
Powershell
Copy
winget install GitHub.cli
Windows 10 and earlier (using Chocolatey):
Powershell
Copy
choco install gh
Authenticate your GitHub account
Powershell
Copy
gh auth login
Verify that it's installed
Powershell
Copy
gh --version
Verify that your authentication worked
Powershell
Copy
gh auth status
Step 7: Node.js Check if node and npm are installed
Powershell
Copy
node --version
Powershell
Copy
npm --version
Install them if not
Windows 11 (using winget):
Powershell
Copy
winget install OpenJS.NodeJS
Windows 10 and earlier (using Chocolatey):
Powershell
Copy
choco install nodejs
Restart PowerShell, then verify that they are installed
Powershell
Copy
node --version
Powershell
Copy
npm --version
Step 8: Claude Code Check if it's installed
Powershell
Copy
claude --version
Install it if not
Powershell
Copy
npm install -g @anthropic-ai/claude-code
Verify it's installed
Powershell
Copy
claude --version
Troubleshooting if it still doesn't show up... First try refreshing your environment, then check the version again after this command:
Powershell
Copy
refreshenv
If it still doesn't work you'll have to check your path for the npm install
Powershell
Copy
npm config get prefix
Then add the npm bin folder to your PATH:
1. Press Windows key + X, select "System"
2. Click "Advanced system settings"
3. Click "Environment Variables"
4. Under "User variables", find and select "Path", click "Edit"


_(truncated — see source URL for full content)_

## Notes

_Hand-editable. Preserved across re-runs._