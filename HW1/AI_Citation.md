Microsoft Windows [Version 10.0.19045.6466]

(c) Microsoft Corporation. All rights reserved.



C:\Users\jtgal>Powershell

Windows PowerShell

Copyright (C) Microsoft Corporation. All rights reserved.



Try the new cross-platform PowerShell https://aka.ms/pscore6



PS C:\Users\jtgal> ls





Directory: C:\Users\jtgal





Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/3/2026 3:46 PM .arduinoIDE

d----- 8/26/2026 11:09 AM .copilot

d----- 1/8/2025 3:19 PM .dotnet

d----- 1/20/2026 3:10 PM .GMA

d----- 8/26/2026 11:35 AM .local

d----- 8/20/2022 12:24 AM .QtWebEngineProcess

d----- 8/26/2026 11:08 AM .vscode

d----- 8/26/2026 11:07 AM .vscode-shared

d-r--- 1/16/2021 9:24 PM 3D Objects

d-r--- 1/16/2021 9:24 PM Contacts

d----- 1/16/2021 9:26 PM Documents

d-r--- 8/27/2026 11:24 AM Downloads

d-r--- 11/16/2021 9:41 PM Favorites

d----- 9/18/2022 4:46 PM Intel

d-r--- 1/16/2021 9:24 PM Links

d-r--- 6/5/2023 11:23 PM Music

d----- 8/27/2026 12:20 PM OEAS805

dar--l 5/8/2026 3:36 PM OneDrive

d-r--- 1/16/2021 9:24 PM Saved Games

d-r--- 1/16/2021 9:25 PM Searches

d-r--- 6/24/2024 11:48 PM Videos

d----- 8/26/2026 7:59 PM Zotero

-a---- 1/20/2026 3:10 PM 21 .geomapapp-home

-a---- 8/27/2026 11:46 AM 61 .gitconfig

-a---- 8/27/2026 11:55 AM 26 .lesshst

-a---- 7/19/2026 11:00 PM 331 BullseyeCoverageError.txt





PS C:\Users\jtgal> cd OEAS805

PS C:\Users\jtgal\OEAS805> git log

commit 2e14f29aa6ba054519321205c98376c962e3a736 (HEAD -> main, origin/main)

Author: jacobtgallaher <jtgallaher4@gmail.com>

Date: Thu Aug 27 12:26:20 2026 -0400



Initial commit

PS C:\Users\jtgal\OEAS805> ls





Directory: C:\Users\jtgal\OEAS805





Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 8/27/2026 12:08 PM git_exercise

-a---- 8/27/2026 12:20 PM 11 README.md





PS C:\Users\jtgal\OEAS805>

You are inside your Git repository OEAS805 on the main branch, which contains one subfolder (git_exercise) and a README.md file.

Common actions you can run next:

Check status: git status (see untracked or modified files)

View subfolder contents: ls git_exercise or cd git_exercise

Edit or create a file: notepad README.md or code . (if VS Code is installed)

Stage and commit changes:

PowerShell
git add .
git commit -m "Your commit message"
git push
What would you like to do next in this directory?

why did my pushing of OEAS805 to GitHub now not show the git_exercise folder, it just shows the README.md file

This happens for one of two common reasons in Git:

git_exercise contains its own hidden .git folder (Most Likely): If you ran git init inside git_exercise at any point, Git treated it as a separate nested repository (submodule). Main Git repositories will not upload the contents of nested Git repositories directly.

git_exercise is completely empty: Git tracks files, not directories. If a folder contains no files, Git ignores it completely.

How to Fix It (If it contains a nested .git folder)
Run the following commands in PowerShell from your OEAS805 directory to clean up the cached tracking and push the files correctly:

Remove the nested hidden .git folder:

PowerShell
Remove-Item -Recurse -Force git_exercise\.git -ErrorAction SilentlyContinue
Unstage the subfolder index from Git:

PowerShell
git rm --cached git_exercise
Re-add the folder, commit, and push:

PowerShell
git add git_exercise
git commit -m "Add git_exercise folder contents"
git push origin main
How to Fix It (If the folder is empty)
If git_exercise has no files inside it yet, create a placeholder file (like .gitkeep or a text file) so Git has something to track:

PowerShell
New-Item -Path git_exercise\.gitkeep -ItemType File
git add git_exercise
git commit -m "Add git_exercise folder"
git push origin main
PS C:\Users\jtgal\OEAS805> mkdir HW1





    Directory: C:\Users\jtgal\OEAS805





Mode                 LastWriteTime         Length Name

----                 -------------         ------ ----

d-----         8/27/2026   3:58 PM                HW1





PS C:\Users\jtgal\OEAS805> ls





    Directory: C:\Users\jtgal\OEAS805





Mode                 LastWriteTime         Length Name

----                 -------------         ------ ----

d-----         8/27/2026  12:08 PM                git_exercise

d-----         8/27/2026   3:58 PM                HW1

-a----         8/27/2026  12:20 PM             11 README.md





PS C:\Users\jtgal\OEAS805>

You created the HW1 folder, but right now it is empty, so Git will not track it or display it on GitHub yet until you add at least one file inside.

To make HW1 appear on GitHub, add a file to it and push the changes:

Create a file inside HW1 (e.g., a blank file or a script):

PowerShell
New-Item -Path HW1\README.md -ItemType File
Stage, commit, and push to GitHub:

PowerShell
git add HW1
git commit -m "Add HW1 folder"
git push origin main
In my HW1 folder I need to add and commit the new folder to the GitHub repository and add a message to the commit

Run these commands from your OEAS805 directory.

Because Git does not track completely empty directories, you need to create a file inside HW1 first before staging and committing.

Create a file inside HW1 (e.g., a README.md):

PowerShell
New-Item -Path HW1\README.md -ItemType File
Stage the HW1 directory:

PowerShell
git add HW1
Commit with your message:

PowerShell
git commit -m "Add HW1 folder"
Push the changes to GitHub:

PowerShell
git push origin main
create a text file in HW1 that writes "My name is "

Run this command in PowerShell to create a text file named name.txt inside your HW1 folder containing that text:

PowerShell
Set-Content -Path HW1\name.txt -Value "My name is "
To add, commit, and push it to GitHub right after:

PowerShell
git add HW1
git commit -m "Add name.txt to HW1"
git push origin main
How do I take a screenshot of my screen, save it as .png within my HW1 folder, then add and commit it

1. Capture and Save the Screenshot
Option A: Snipping Tool (Recommended)
Press Win + Shift + S to capture your screen.

Click the Snipping Tool notification that pops up in the bottom right corner.

Click the Save icon (floppy disk) in the top right.

Navigate to your folder path:
C:\Users\jtgal\OEAS805\HW1

Name the file (e.g., screenshot.png) and ensure Save as type is set to PNG.

Option B: Entire Screen Shortcut
Press Win + PrtScn (Print Screen). Windows automatically saves the full screen to:
C:\Users\jtgal\Pictures\Screenshots

Move that screenshot into your HW1 folder using PowerShell:

PowerShell
Get-ChildItem "$home\Pictures\Screenshots" | Sort-CreationTime | Select-Object -Last 1 | Move-Item -Destination "C:\Users\jtgal\OEAS805\HW1\screenshot.png"
2. Add, Commit, and Push to GitHub
Run these commands in PowerShell from your OEAS805 folder:

PowerShell
git add HW1/screenshot.png
git commit -m "Add screenshot to HW1"
git push origin main



Gemini is AI and can make mistakes.