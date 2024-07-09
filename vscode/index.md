---
title: "VS Code"
layout: home
has_children: true
---
VS Code stuff

### Color Customisations

Shift-Ctrl-P, search "settings", Preferences: Open User Settings (JSON)

(or open `C:\Users\dylan\AppData\Roaming\Code\User\settings.json`)

Add this:

```
    "workbench.colorCustomizations": {
        "[*Dark*]": {
            "editor.background": "#110011"
        }
    },
```

To build and install a local preview of a VS Code extension package:

```
vsce package -o my-package.vsix
code --install-extension presentation-buddy.preview.vsix
```



