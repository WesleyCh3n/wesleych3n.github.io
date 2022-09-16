---
title: "SSH X server on Windows"
date: 2021-10-14
categories:
  - note
tags:
  - powershell
  - x server
excerpt: ""
header:
  teaser: ./assets/teasers/vcxsrv.jpg
toc: true
toc_label: "Outline"
toc_icon: "box-open"
---

# Installation
## Install VcXsrv

```ps1
scoop install vcxsrv
```

## Setup xLauncher

```ps1
xlaunch.exe
```

`config.launch`

```html
<?xml version="1.0" encoding="UTF-8"?>
<XLaunch
  WindowMode="MultiWindow"
  ClientMode="NoClient"
  LocalClient="False"
  Display="-1"
  LocalProgram="xcalc"
  RemoteProgram="xterm"
  RemotePassword=""
  PrivateKey=""
  RemoteHost=""
  RemoteUser=""
  XDMCPHost=""
  XDMCPBroadcast="False"
  XDMCPIndirect="False"
  Clipboard="True"
  ClipboardPrimary="True"
  ExtraParams="-ac -nowgl"
  Wgl="True"
  DisableAC="False"
  XDMCPTerminate="False"
/>
```

## Add env variable to PowerShell PROFILE

```ps1
# vi $PROFILE, and add below line
$env:DISPLAY='localhost:0.0'
```

## Test out and finish!

```ps1
ssh -Y server
```

```bash
xclock
```
