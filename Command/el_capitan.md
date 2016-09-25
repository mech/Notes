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

▶ brew install vim --override-system-vi

▶ rbenv install 2.3
▶ rbenv rehash
▶ rbenv global 2.3

▶ rbenv install 1.9.3-p551
```

For rbenv, put:

`if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi` into your `.zshrc` or `.bashprofile`

**Install databases**

```
▶ brew install homebrew/versions/mysql56
▶ brew install postgres
▶ brew install redis

▶ brew search mongodb
▶ brew install homebrew/versions/mongodb26

// For eventmachine
▶ brew link openssl --force
```

**Configure and restore databases**

```
▶ mysqladmin -u root password PASSWORD

▶ mysql -u root -p jobline_dev < backup.sql
```

