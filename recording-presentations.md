---
title: Recording Code
layout: home
---

Open a new terminal.

Terminal defaults to `~/Projects`

Projects already contains:

* A `global.json` specing which version of .NET I need for the session
* A `.editorconfig` file with the code format settings for this session

```dotnetcli
dotnet new console -o MailDemo
cd MailDemo
code .
```

OK, now the fun part. I want a hotkey that will fire up Presentation Buddy and start typing stuff into this folder.

So... Presentation Buddy needs to read code from **somewhere else**.

So I'll create this folder structure in advance:

```Projects
Projects
  /.presentation-buddy
    /MailDemo
      /instructions.json
```



