---
title: "Windows Terminal Nutzer"
description: "Eine Sammlung von Handgriffen, die das Leben einfacher machen."
tags:
    - Windows
    - Terminal App
    - PowerShell
    - CLI Befehle
---

## Starte Edge Browser und öffne Url

```pwsh
Start-Process microsoft-edge:https://github.com/M2vH/garagelab-dus -WindowStyle maximized
```

## Öffne Url des Repository im Edge Browser

```pwsh
Start-Process microsoft-edge:$(gh repo view --json url -q .url) -WindowStyle maximized
```
