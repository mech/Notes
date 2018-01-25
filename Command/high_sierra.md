# macOS Sierra

## Install Xcode

After installing Xcode, we need to install Command Line Tools also:

```
▶ xcode-select --install
```

## Locale

In your `~/.config/fish/config.fish` or your bash profile:

```
set -gx LANG en_US.UTF-8
```

## Install Homebrew

```
▶ brew update
▶ brew doctor
▶ brew install wget tree httpie git diff-so-fancy
▶ brew install rbenv ruby-build

▶ rbenv install -l
▶ rbenv install 2.5.0
▶ rbenv rehash
▶ rbenv global 2.5.0

▶ rbenv install 1.9.3-p551

▶ gem update --system
▶ gem install bundler
▶ rbenv rehash
```

## Install fish shell

Create `~/.config/fish/config.fish` if it does not exist

```
▶ function q
    exit
  end

▶ funcsave q
```

## Git

Cloning using [HTTPS](https://help.github.com/articles/which-remote-url-should-i-use/) is preferred than using SSH. `osxkeychain` is a helper to remember your username and password when using HTTPS.

```
git config --global user.name "<your-name>"
git config --global user.email "<your-email>"

git config --global alias.co checkout
git config --global alias.st "status -sb"
git config --global alias.br branch

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

**.gemrc, .irbrc, .pryrc**

.gemrc

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

.irbrc

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

.pryrc

```ruby
Pry.commands.alias_command 'q', 'exit'
```

**How to make Jobline Legacy work**

If you are using Bundler v1.13.1, you will encounter "git source which transmits data without encryption". Please see https://github.com/bundler/bundler/pull/2569

```ruby
gem "mysql2", "~> 0.3.20"
gem "eventmachine", "1.0.9"

gem "will_paginate", git: "https://github.com/mech/will_paginate.git"
gem "xeroizer", git: "https://github.com/mech/xeroizer.git", branch: "bank_transfers"

# You can delete this
gem "smbglobal-sms", git: "https://github.com/mech/smbglobal-sms.git"

# Not sure why need this one
gem "public_suffix", "1.4.6"
```

Note: You may need to `rm Gemfile.lock` first. (Probably not)

## Install databases

```
▶ brew install mysql
▶ brew install postgres
▶ brew install redis
▶ brew install mongodb@3.0

// See what services you have
▶ brew services list
```

### Configure and restore databases

```
▶ mysql_secure_installation
▶ mysql -u root -p jobline_dev < backup.sql

▶ mongorestore --db jobline_dev --drop /backup/Mongo/jobline_pro
```
