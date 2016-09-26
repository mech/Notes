# El Capitan

**Install Xcode**

```
▶ xcode-select --install
```

**Setup `locale`**

In your `.zshrc`

```
export EDITOR=vi
export LC_CTYPE=en_US.UTF-8
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
```

**Install Homebrew**

```
▶ brew update
▶ brew doctor
▶ brew install wget tree httpie
▶ brew install rbenv ruby-build

▶ brew install vim --with-override-system-vim

▶ rbenv install 2.3
▶ rbenv rehash
▶ rbenv global 2.3

▶ rbenv install 1.9.3-p551
```

For rbenv, put:

`if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi` into your `.zshrc` or `.bashprofile`

**How to make Jobline Legacy work**

If you are using Bundler v1.13.1, you will encounter "git source which transmits data without encryption". Please see https://github.com/bundler/bundler/pull/2569

```gemfile
gem "mysql2", "~> 0.3.20"
gem "eventmachine", "1.0.9"

gem "will_paginate", git: "https://github.com/mech/will_paginate.git"
gem "smbglobal-sms", git: "https://github.com/mech/smbglobal-sms.git"
```

**Install databases**

```
▶ brew install homebrew/versions/mysql56
▶ brew install postgres
▶ brew install redis

▶ brew search mongodb
▶ brew install homebrew/versions/mongodb26

// For eventmachine
// See https://github.com/eventmachine/eventmachine/pull/668 and https://github.com/eventmachine/eventmachine/issues/643
▶ brew link openssl --force
```

**Configure and restore databases**

If MySQL is fresh install, you can use `mysql_secure_installation` to set root password.

```
// You are better off using mysql_secure_installation to reset root password
▶ mysqladmin -u root password PASSWORD

▶ mysql -u root -p jobline_dev < backup.sql
```

