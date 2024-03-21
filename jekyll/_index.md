---
title: Jekyll
layout: home
has_children: true
---

### Jekyll on Windows, wdm, and GitHub Actions

The first time you run `bundle exec jekyll serve` on Windows, it'll say:

```
  Please add the following to your Gemfile to avoid polling for changes:
    gem 'wdm', '>= 0.1.0' if Gem.win_platform?
```

So you do, and it works, and you push it to GitHub, and it fails:

```
You are trying to install in deployment mode after changing your Gemfile. Run `bundle install` elsewhere and add the
updated Gemfile.lock to version control.

If this is a development machine, remove the /home/runner/work/grimoire.dylanbeattie.net/grimoire.dylanbeattie.net/Gemfile
freeze by running `bundle config unset deployment`.

You have deleted from the Gemfile:
* wdm (>= 0.1.0)
Error: The process '/opt/hostedtoolcache/Ruby/3.1.4/x64/bin/bundle' failed with exit code 16
```

The problem is the line you need to add is *actually*:

```
gem 'wdm', '>= 0.1.0', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```

