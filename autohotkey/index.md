---
title: AutoHotkey
layout: home
---
# {{ page.title }}

AutoHotkey macro stuff.

Here's how to KeyWait for a virtual key that isn't actually a key - the Contour ShuttleXpress sends artificial keystrokes, which don't work with AHK's KeyWait function, but you can use an InputHook to wait until the artificial keystroke happens:
```ahk



WaitForRightArrow() {
    ih := InputHook("")
    ih.KeyOpt("{Right}", "E")  ; End
    ih.Start()
    ih.Wait()
}
```