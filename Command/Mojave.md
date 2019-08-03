# Mojave

defaults write -g CGFontRenderingFontSmoothingDisabled -bool NO

## Install Xcode

After installing Xcode, launch Xcode to install some software first. Then we need to install Command Line Tools to make Homebrew work:

```
▶ xcode-select --install
```

## Install Homebrew

```
▶ brew update
▶ brew doctor
▶ brew install git
▶ brew install fish
▶ brew install wget tree httpie diff-so-fancy
```

We need to install Git first since it will give us osxkeychain helper.

## Install fish shell

Create `~/.config/fish/config.fish` and write your aliases. Create `functions` folder. 

```
function q
  exit
end
```

## Locale

In your `~/.config/fish/config.fish` or your bash profile:

```
set -gx LANG en_US.UTF-8
```

## Git

For **development**, cloning using [HTTPS](https://help.github.com/articles/which-remote-url-should-i-use/) is preferred than using SSH. `osxkeychain` is a helper to remember your username and password when using HTTPS.

However to remote in server, you also need to setup SSH.

```
git config --global user.name <your-name>
git config --global user.email <your-email>

git config --global alias.co checkout
git config --global alias.st "status -sb"
git config --global alias.br branch
git config --global alias.di diff

git config --global apply.whitespace nowarn

git config --global color.branch auto
git config --global color.diff auto
git config --global color.interactive auto
git config --global color.status auto
git config --global color.ui true

git config --global color.diff-highlight.oldNormal    "red bold"
git config --global color.diff-highlight.oldHighlight "red bold 52"
git config --global color.diff-highlight.newNormal    "green bold"
git config --global color.diff-highlight.newHighlight "green bold 22"

git config --global color.diff.meta       "yellow"
git config --global color.diff.frag       "magenta bold"
git config --global color.diff.commit     "yellow bold"
git config --global color.diff.old        "red bold"
git config --global color.diff.new        "green bold"
git config --global color.diff.whitespace "red reverse"

git config --global core.editor vim
git config --global core.excludesfile "/Users/<name>/.gitignore"
git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"

git config --global credential.helper osxkeychain
```

macOS Sierra 10.12.2 require UseKeychain. Edit `~/.ssh/config` file:

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

Copy SSH file to remote

```
▶ ssh-copy-id -p PORT USER@IP
```

## Git Log

```
▶ chmod +x /usr/local/bin/color-git-log
```

## Visual Studio Code

* [code-settings-sync](https://gist.github.com/mech/6e894325d87d9a910a9996dba694a9ed)

## Java 8

Do not install Java 11. Use JDK 8.

## Ruby

Do this only after setting up fish.

```
▶ brew install rbenv ruby-build

▶ rbenv install -l
▶ rbenv install 2.5.1
▶ rbenv rehash
▶ rbenv global 2.5.1

▶ gem update --system
▶ rbenv rehash
```

Setup rbenv:

```
set PATH $HOME/.rbenv/shims $PATH
rbenv rehash >/dev/null ^&1
status --is-interactive; and . (rbenv init -|psub)
```

~/.gemrc

```yaml
---
:verbose: true
:update_sources: true
:sources:
- https://rubygems.org
gem: --no-rdoc --no-ri
:bulk_threshold: 1000
:backtrace: false
:benchmark: false
```

~/.irbrc

```ruby
require 'rubygems'
require 'awesome_print'
require 'irb/completion'

AwesomePrint.irb!

IRB.conf[:AUTO_INDENT] = true
IRB.conf[:SAVE_HISTORY] = 1000
IRB.conf[:EVAL_HISTORY] = 200

class Object
  def local_methods
    (methods - Object.instance_methods).sort
  end
end

alias q exit
```

~/.pryrc

```ruby
Pry.commands.alias_command 'q', 'exit'
```

## Install databases

* [Install MySQL 5.7 on macOS](https://gist.github.com/operatino/392614486ce4421063b9dece4dfe6c21)

```
// Do not install MySQL 8
▶ brew install mysql@5.7
▶ brew services start mysql@5.7
▶ brew link mysql@5.7 --force

▶ brew install postgres
▶ brew install redis

// See what services you have
▶ brew services list
```

### Configure and restore databases

```
▶ mysql_secure_installation
▶ mysql -u root -p jobline_dev < backup.sql
```

## mysql2

Use this as of Aug 2019 with Mojave 10.14.6:

```
// This works on Aug 2019, with Mojave 10.14.6
▶ bundle config --local build.mysql2 "--with-ldflags=-L/usr/local/opt/openssl/lib"
```

See: https://github.com/brianmario/mysql2/issues/1045
See: 

<span style="color:red">BELOW ARE OUT-OF-DATE</span>

If you can't install mysql2 gem for MySQL@5.7

* [#1005](https://github.com/brianmario/mysql2/issues/1005)

```
// This works on Ruby 2.5.1 only
▶ bundle config --local build.mysql2 "--with-ldflags=-L/usr/local/opt/openssl/lib --with-cppflags=-I/usr/local/opt/openssl/include"

// For Ruby 2.5.3
▶ brew install openssl

// For bash shell
▶ gem install mysql2 -- --with-opt-dir="$(brew --prefix openssl)"

// or for fish shell
▶ gem install mysql2 -- --with-opt-dir="(brew --prefix openssl)"
```

## Apps

* [MWeb for Markdown writing - Use External mode](https://www.mweb.im)
