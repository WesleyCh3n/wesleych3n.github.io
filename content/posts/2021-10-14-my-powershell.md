---
title: "My Bash/Zsh-like PowerShell Journey"
date: 2021-10-13
categories:
  - note
tags:
  - powershell
  - bash
toc: true
toc_label: "Outline"
toc_icon: "box-open"
---

**TL;DR**

This is a note that I found out Microsoft PowerShell can act like Bash/Zsh which
I much familiar with. Because of the work, pretty much whole operating system
move to windows. It is so much pain to work without using any shell. The main
reason is that I so much used to use (neo)vim as my code editor. But luckily
(neo)vim built for windows (phew~). Ok, back to the title, this is a step by step
note that I dig into PowerShell and Windows.

- Create `$PROFILE` for PowerShell if not exist (like `.bashrc` or `.zshrc`)

    1. Test if Profile exist
        ```powershell
        Test-Path $PROFILE
        ```
    > ❗If return is false meaning there is NO profile found then jump to step 2. <br>
    > ❗If return is true meaning there IS profile found then jump to step 3.

    2. Create Profile
        ```powershell
        New-Item -Type File -Force $PROFILE
        ```
    > ⚠ (Caution) these will erase the exist profile with new empty one.

    3. Varify Profile path
        ```powershell
        echo $PROFILE
        ```
    It normally locate in `~/Documents/WindowsPowerShell/Microsoft.PowerShell_profile.ps1`

- Install `oh-my-posh` Theme like powerlevel10k

    1. Installation
        ```powershell
        Install-Module oh-my-posh -Scope CurrentUser
        ```

    2. List all themes and remember the name of theme you like
        ```powershell
        Get-PoshThemes -list
        ```

    3. Add theme to Profile
        ```powershell
        Set-PoshPrompt -Theme <Theme name>
        ```
    Personally I use `honukai` for the simplicity.

    4. Source the Profile or restart the Terminal to take effect.
        ```powershell
        . $PROFILE
        ```

- Install Autosuggestion

    1. Installation
        ```powershell
        Install-Module PSReadLine
        ```

    2. Add the following configurations
        ```powershell
        # autocompletion
        Import-Module PSReadLine
        Set-PSReadLineOption -PredictionSource History
        Set-PSReadLineKeyHandler -Chord Shift+Tab -Function AcceptSuggestion # Accept Suggestion

        # Autocompletion for arrow keys
        Set-PSReadlineKeyHandler -Key Tab -Function MenuComplete # Iterate through autocompletion
        Set-PSReadlineKeyHandler -Key UpArrow -Function HistorySearchBackward
        Set-PSReadlineKeyHandler -Key DownArrow -Function HistorySearchForward

        # Bash like movement
        Set-PSReadlineKeyHandler -Chord ctrl+d -Function ViExit
        Set-PSReadlineKeyHandler -Chord ctrl+w -Function BackwardDeleteWord
        Set-PSReadlineKeyHandler -Chord ctrl+e -Function EndOfLine
        Set-PSReadlineKeyHandler -Chord ctrl+a -Function BeginningOfLine
        ```

- Tab Completion [Ref](https://github.com/bergmeister/posh-cli)

