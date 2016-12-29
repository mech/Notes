# macOS Sierra

**Install Xcode**

```bash
▶ xcode-select --install
```

**Setup `locale`**

In your `.zshrc` or your bash profile:

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
▶ rbenv install 2.4
▶ rbenv rehash
▶ rbenv global 2.4

▶ rbenv install 1.9.3-p551

▶ gem update --system
▶ gem install bundler
▶ rbenv rehash
```

For rbenv, put the following on the last line:

```bash
eval "$(rbenv init -)"
```

**Git**

macOS Sierra 10.12.2 require UseKeychain. Edit `~/.ssh/config` file:

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
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
▶ brew install mysql@5.6
▶ brew install postgres
▶ brew install redis

// BEWARE! Use the Docker option to install MongoDB instead of Homebrew since SCons Error is persistent
// As of Dec 2016, Homebrew no longer provide mongodb26
▶ brew search mongodb
▶ brew install homebrew/versions/mongodb26

// For eventmachine, edit the Gemfile to v1.0.9
// See https://github.com/eventmachine/eventmachine/pull/668
// See https://github.com/eventmachine/eventmachine/issues/643
```

You can see [this article for problem with OpenSSL](http://stackoverflow.com/questions/38670295/brew-refusing-to-link-openssl)

If we cannot installed Mongo 2.6 due to "SCons Error", you can use [Docker for Mac](https://www.docker.com/products/docker#/mac) for Mongo.

With Docker for Mac installed, you can run an instance of the container using:

```bash
// To restore backup as well as having an instance
▶ docker run -d -v ~/Desktop/backup:/backup -p 27017:27017 mongo:2.6

// Don't do this! Just for reference!
▶ docker run -d -p 27017:27017 mongo:2.6
```

With that container, you need to restore the backup, you can:

```bash
▶ docker ps
▶ docker exec -it <container-id> bash -l
```

**Configure and restore databases**

If MySQL is fresh install, you can use `mysql_secure_installation` to set root password.

```bash
// Don't do this! You are better off using mysql_secure_installation to reset root password
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

```ruby
Candidate.all.each { |ca| ca.password='password'; ca.save 
Employer.all.each { |emp| emp.password='password'; emp.save }
```
