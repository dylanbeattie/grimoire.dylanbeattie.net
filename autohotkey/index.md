---
title: AutoHotkey
layout: home
---
# {{ page.title }}

AutoHotkey macro stuff.

Here's how to KeyWait for a virtual key that isn't actually a key - the Contour ShuttleXpress sends artificial keystrokes, which don't work with AHK's KeyWait function, but you can use an InputHook to wait until the artificial keystroke happens:

```autohotkey

#Requires AutoHotkey v2.0
InstallKeybdHook

FileEncoding "UTF-8"

F13::{
    FirstLine := true
    SendMode "Event"
    SetKeyDelay 35
    Loop read, "gmail.smtp" {
        if (FirstLine) {
            FirstLine := false
        } else {
            KeyWait "Enter", "D"
            KeyWait "Enter"
        }
        Loop Parse A_LoopReadLine {
            WaitForRightArrow()
            SendText A_LoopField
        }
    }
}

WaitForRightArrow() {
    ih := InputHook("")
    ih.KeyOpt("{Right}", "E")  ; End
    ih.Start()
    ih.Wait()
}
```

Here's the script that hooks into 