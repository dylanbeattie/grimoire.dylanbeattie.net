---
title: Jekyll
layout: home
---

# Jekyll Tips

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

## cannot load such file -- webrick

Running `bundle exec jekyll serve` produces:

```
C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-
4.0.1/lib/jekyll/commands/serve/servlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/lib/jekyll/commands/serve/servlet.rb:3:in `<top (required)>'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/lib/jekyll/commands/serve.rb:179:in `require_relative'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/lib/jekyll/commands/serve.rb:179:in `setup'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/lib/jekyll/commands/serve.rb:100:in `process'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/lib/jekyll/command.rb:89:in `block in process_with_graceful_fail'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/lib/jekyll/command.rb:89:in `each'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/lib/jekyll/command.rb:89:in `process_with_graceful_fail'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/lib/jekyll/commands/serve.rb:86:in `block (2 levels) in init_with_program'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `block in execute'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `each'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `execute'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary/program.rb:42:in `go'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/mercenary-0.3.6/lib/mercenary.rb:19:in `program'
        from C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-4.0.1/exe/jekyll:15:in `<top (required)>'
        from C:/Ruby31-x64/bin/jekyll:25:in `load'
        from C:/Ruby31-x64/bin/jekyll:25:in `<main>'
```

At some point `webrick` became an external dependency, so needs to be explicitly added to the `Gemfile`:

```
gem "webrick"
```



