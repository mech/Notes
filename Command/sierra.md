# macOS Sierra

**Install Xcode**

```bash
▶ xcode-select --install
```

**Setup `locale`**

In your `.zshrc`

```bash
export EDITOR=vi
export LC_CTYPE=en_US.UTF-8
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
```

**Install Homebrew**

```bash
▶ brew update
▶ brew doctor
▶ brew install wget tree httpie git
▶ brew install rbenv ruby-build

▶ brew install vim --with-override-system-vim

▶ rbenv install -l
▶ rbenv install 2.3.1
▶ rbenv rehash
▶ rbenv global 2.3.1

▶ rbenv install 1.9.3-p551

▶ gem update --system
▶ gem install bundler
▶ rbenv rehash
```

For rbenv, put the following on the last line:

```bash
eval "$(rbenv init -)"
```

**How to make Jobline Legacy work**

If you are using Bundler v1.13.1, you will encounter "git source which transmits data without encryption". Please see https://github.com/bundler/bundler/pull/2569

```ruby
gem "mysql2", "~> 0.3.20"
gem "eventmachine", "1.0.9"

gem "will_paginate", git: "https://github.com/mech/will_paginate.git"
gem "smbglobal-sms", git: "https://github.com/mech/smbglobal-sms.git"
```

**Install databases**

```bash
▶ brew install homebrew/versions/mysql56
▶ brew install postgres
▶ brew install redis

▶ brew search mongodb
▶ brew install homebrew/versions/mongodb26

// For eventmachine
// See https://github.com/eventmachine/eventmachine/pull/668 and https://github.com/eventmachine/eventmachine/issues/643
▶ brew link openssl --force
```

If we cannot installed Mongo 2.6 due to "SCons Error", you can use [Docker for Mac](https://www.docker.com/products/docker#/mac) for Mongo.

```bash
docker run -d -v ~/Desktop/backup:/backup -p 27017:27017 mongo:2.6
```

**Configure and restore databases**

If MySQL is fresh install, you can use `mysql_secure_installation` to set root password.

```bash
// You are better off using mysql_secure_installation to reset root password
▶ mysqladmin -u root password PASSWORD

▶ mysql -u root -p jobline_dev < backup.sql

▶ mongorestore --db jobline_dev --drop ~/Desktop/mongodb_bak_with_timestamp/jobline_pro
```

```sql
select email from users where type='Candidate' limit 10;
update users set email=CONCAT("sample_", email) where type='Candidate';
select email from users where type='Employer' limit 10;
update users set email=CONCAT("jlxyz_", email) where type='Employer';
```