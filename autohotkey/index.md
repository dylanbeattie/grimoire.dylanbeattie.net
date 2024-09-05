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

Here's the script that listens for Ctrl-S and if the active window has "autohotkey" in the title (i.e. you're in VS code editing something in the `/autohotkey` folder/workspace) it'll reload the active script, and beep to let you know it worked:

```autohotkey
~^s::
{
    If WinActive("autohotkey") {
        SoundBeep
        Sleep 200      
        Reload
        SoundPlay "*16"
    }
    return
}
```