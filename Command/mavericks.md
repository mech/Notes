# System Installation with Mavericks

Only use wkhtmltopdf 0.9.9 or else will have Mac OS X Dock issue. See https://github.com/blueheadpublishing/bookshop/wiki/Installing-wkhtmltopdf

```
curl -O http://wkhtmltopdf.googlecode.com/files/wkhtmltopdf-0.9.9-OS-X.i368
mv wkhtmltopdf-0.9.9-OS-X.i368 /usr/local/bin/wkhtmltopdf
chmod +x /usr/local/bin/wkhtmltopdf
```

For Old CP development on Mavericks, use `CC=gcc-4.8.3 rbenv install 1.8.7-p374` to install Ruby 1.8.7

For installing Sphinx, you need to:

```
brew versions sphinx

# Then pick
# 2.0.9    git checkout 9d8f899 /usr/local/Library/Formula/sphinx.rb

brew install sphinx --mysql

# The SHA is wrong, so you just need to correct it.
resource 'stemmer' do
  url 'http://snowball.tartarus.org/dist/libstemmer_c.tgz'
  # sha1 '69056075b9fa1382e07cec6c32c8e82f3f35677b'
  sha1 'bbe1ba5bbebb146575a575b8ca3342aa3b91bf93'
end
```

The above SHA changes might not work. We will get stem_ISO_8859_1_hungarian issues, so we need edit the Makefile.in of the libstemmer_c folder. See https://github.com/Homebrew/homebrew/pull/32064/files

For installing ImageMagick, you need to:

```
cd /usr/local/Cellar/imagemagick/6.8.9-1/lib
ln -s libMagick++-6.Q16.dylib  libMagick++.dylib                                                                                
ln -s libMagickCore-6.Q16.dylib libMagickCore.dylib                                                                            
ln -s libMagickWand-6.Q16.dylib libMagickWand.dylib
```

See http://stackoverflow.com/questions/13942443/error-installing-rmagick-on-mountain-lion

---

1. Install Xcode
2. `xcode-select --install` to install Xcode Command Line Tools. Sometimes it is not available, so you need to go to the Developer site to download it.
3. To make sure, type `gcc --version`
4. Install `oh-my-zsh` via `curl`
5. Install Homebrew. `brew update` and `brew doctor` first.
6. Because we still have Ruby 1.8 application, we need to use GCC 4.2.

	```
   brew tap homebrew/dupes
   brew install autoconf automake apple-gcc42
   sudo ln -s /usr/local/bin/gcc-4.2 /usr/bin/gcc-4.2
   ```

7. If you need X11, you can install it [here](http://xquartz.macosforge.org/landing/). You will want to `sudo ln -s /opt/X11 /usr/X11` also.
8. Preparing for Git installation. Mavericks come with git, but we want to install it via `brew install git` which will reside at `/usr/local/bin/git`. Edit `.zshrc` to move that path forward: `export PATH="/usr/local/git/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin"`

   Configure git with:
	
	```
   git config --global user.name "mech"
   git config --global user.email "mech@me.com"
   git config --global alias.co checkout
   git config --global alias.st status
   git config --global alias.br branch
   git config --global apply.whitespace nowarn
   git config --global color.branch auto
   git config --global color.diff auto
   git config --global color.interactive auto
   git config --global color.status auto
   git config --global core.editor "vim"
   git config --global push.default simple
   git config --global --bool pull.rebase true
   ```

9. Includes these at `.zshrc`

	```
   export EDITOR=vi
   export LC_CTYPE=en_US.UTF-8
   export LC_ALL=en_US.UTF-8
   export LANG=en_US.UTF-8
   export CPPFLAGS=-I/opt/X11/include
   
   RPROMPT='%{$fg[white]%} $(rbenv version | sed -e "s/ (set.*$//")%{$reset_color%}'
   ```

10. Now is time to generate SSH, and always give a passphrase!

        ssh-keygen -t rsa -C "mech@me.com"
        ssh-add id_rsa
        ssh-copy-id -i ~/.ssh/id_rsa.pub administrator@58.185.193.188

    Paste the `id_rsa.pub` to GitHub and test it `ssh -T git@github.com`

11. Install rbenv: `brew install rbenv ruby-build`. All of your rubies will be stored in `~/.rbenv/versions`

    Some useful command for rbenv:
    
        rbenv install -l
        rbenv install 2.1.2
        rbenv install 1.9.3-p125
        rbenv global 2.1.2
        rbenv versions
        rbenv version
        rbenv rehash
        rbenv local 1.9.3-p125
        
        gem update --system
        gem install bundler
        rbenv rehash
        
        rbenv shell system => If you need to have system Ruby
        
In case you want to upgrade Ruby version, you need to:

```
brew upgrade rbenv ruby-build
rbenv install 2.2.2
rbenv rehash
rbenv uninstall 2.2.1
rbenv global 2.2.2
```

If you have RVM already, you can remove it as such:

    echo $PATH | grep rvm => Test to see if there is RVM
    rvm implode           => Remove RVM
    which -a ruby         => Test to see if there is any Rubies left
    yes | sudo gem uninstall -a --ignore-dependencies `gem list --no-versions` => Uninstall all gems from system ruby

# oh-my-zsh

Aliases:

    alias k='clear'
    alias q='exit'
    alias e='subl . &'

    alias remote='ssh administrator@58.185.193.188'
    alias mini='ssh administrator@58.185.193.185'
    alias cp_home='cd /path/to/careerpacific.com'
    alias jobline='cd /path/to/jobline.com.sg'
    alias ats='cd /path/to/ats.careerpacific.com'
    alias cp_db='psql cp_development'

Theme:

    PROMPT='%{$fg[green]%}%p%{$fg[cyan]%}%c %{$fg[yellow]%}$(git_prompt_info)%{$fg[green]%}$%{$reset_color%} '

    ZSH_THEME_GIT_PROMPT_PREFIX="(%{$fg[yellow]%}"
    ZSH_THEME_GIT_PROMPT_SUFFIX="%{$reset_color%}"
    ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[yellow]%})%{$fg[red]%}⚡ %{$reset_color%}"
    ZSH_THEME_GIT_PROMPT_CLEAN="%{$fg[yellow]%}) "


# Sublime Text

User settings:

    {
      "color_scheme": "Packages/User/sublime-xoria (SL).tmTheme",
	   "font_face": "Source Code Pro Light",
	   "font_size": 18,
	   "highlight_line": true,
	   "highlight_modified_tabs": true,
	   "ignored_packages":
	     [
	       "Vintage"
	     ],
	     "rulers":
	     [
	       80
	     ],
	   "scroll_past_end": true,
	   "tab_size": 2,
	   "theme": "Soda Light.sublime-theme",
	   "trailing_spaces_include_current_line": false,
	   "translate_tabs_to_spaces": true,
	   "trim_trailing_white_space_on_save": true,
	   "word_wrap": "false"
	 }

Key bindings:

    [
      {"keys": ["ctrl+super+r"], "command": "reveal_in_side_bar"}
    ]


List of plugins:

* AdvancedNewFile
* Alignment
* CTags
* Emmet
* Git
* GitGutter
* Sidebar
* Table Editor
* Trailing Spaces
* Word Count
* Sublime Linter

# Vim

Get Janus Vim distribution at https://github.com/carlhuda/janus

.vimrc.before

    let mapleader=","

.vimrc.after

    colorscheme xoria256

    set nocompatible

    command! W :w
    command! Q :q

    syntax on
    filetype plugin indent on
    set autoindent
    set ts=2
    set shiftwidth=2
    set expandtab
    set showmatch
    set smartcase
    set incsearch
    set ttimeoutlen=100
    set vb
    set ruler
    set cursorline
    set cmdheight=2
    set history=10000
    set colorcolumn=80

    highlight ColorColumn ctermbg=11
    highlight Visual ctermbg=3 ctermfg=0
    highlight Folded ctermbg=237 ctermfg=white
    highlight FoldColumn ctermbg=237 ctermfg=white

    if version >= 700
      au InsertEnter * hi StatusLine ctermfg=235 ctermbg=2
      au InsertLeave * hi StatusLine ctermbg=240 ctermfg=white
    endif

    let g:ctrlp_max_height = 30
    let g:ctrlp_working_path_mode = 0
    let g:ctrlp_match_window_reversed = 0

    " Making rvm work
    set shell=bash

    autocmd FileType ruby setlocal foldmethod=syntax
    autocmd FileType javascript setlocal foldmethod=syntax
    autocmd FileType eruby setlocal foldmethod=indent shiftwidth=2 tabstop=2
    autocmd FileType css setlocal foldmethod=indent shiftwidth=2 tabstop=2
    set nofoldenable " Have fold, but do not do it when I open the file

    " Space is zz
    nmap <space> zz

    " Clear the search buffer when hitting return
    :nnoremap <CR> :nohlsearch<cr>
    nnoremap <leader><leader> <c-^>

    " Status line
    :set statusline=%<%f\ (%{&ft})\ %{fugitive#statusline()}\ %-4(%m%)%=%-19(%3l,%02c%03V%)

    " Arrow keys are unacceptable
    map <Left> :echo "HJKL only!"<cr>
    map <Right> :echo "HJKL only!"<cr>
    map <Up> :echo "HJKL only!"<cr>
    map <Down> :echo "HJKL only!"<cr>

    " Open files in directory of current file
    cnoremap %% <C-R>=expand('%:h').'/'<cr>
    map <leader>e :edit %%
    map <leader>v :view %%

    " Switch between test and production code (Non-Rails)
    function! OpenTestAlternate()
      let new_file = AlternateForCurrentFile()
      exec ':e ' . new_file
    endfunction
    function! AlternateForCurrentFile()
      let current_file = expand("%")
      let new_file = current_file
      let in_spec = match(current_file, '^spec/') != -1
      let going_to_spec = !in_spec
      let in_app = match(current_file, '\<controllers\>') != -1 || match(current_file, '\<models\>') != -1 || match(current_file, '\<views\>') != -1
      if going_to_spec
        if in_app
          let new_file = substitute(new_file, '^app/', '', '')
        end
        let new_file = substitute(new_file, '\.rb$', '_spec.rb', '')
        let new_file = 'spec/' . new_file
      else
        let new_file = substitute(new_file, '_spec\.rb$', '.rb', '')
        let new_file = substitute(new_file, '^spec/', '', '')
        if in_app
          let new_file = 'app/' . new_file
        end
      endif
      return new_file
    endfunction
    nnoremap <leader>. :call OpenTestAlternate()<cr>

    " Running tests
    map <leader>t :call RunTestFile()<cr>
    map <leader>T :call RunNearestTest()<cr>
    map <leader>a :call RunTests('')<cr>
    map <leader>c :w\|:!script/features<cr>
    map <leader>w :w\|:!script/features --profile wip<cr>

    function! RunTestFile(...)
      if a:0
        let command_suffix = a:1
      else
        let command_suffix = ""
      endif

      " Run the tests for the previously-marked file.
      let in_test_file = match(expand("%"), '\(.feature\|_spec.rb\)$') != -1
      if in_test_file
        call SetTestFile()
      elseif !exists("t:grb_test_file")
        return
      end
      call RunTests(t:grb_test_file . command_suffix)
    endfunction

    function! RunNearestTest()
      let spec_line_number = line('.')
      call RunTestFile(":" . spec_line_number . " -b")
    endfunction

    function! SetTestFile()
      " Set the spec file that tests will be run for.
      let t:grb_test_file=@%
    endfunction

    function! RunTests(filename)
      " Write the file and run tests for the given filename
      :w
      :silent !echo;echo;echo;echo;echo;echo;echo;echo;echo;echo
      :silent !echo;echo;echo;echo;echo;echo;echo;echo;echo;echo
      :silent !echo;echo;echo;echo;echo;echo;echo;echo;echo;echo
      :silent !echo;echo;echo;echo;echo;echo;echo;echo;echo;echo
      :silent !echo;echo;echo;echo;echo;echo;echo;echo;echo;echo
      :silent !echo;echo;echo;echo;echo;echo;echo;echo;echo;echo
      if match(a:filename, '\.feature$') != -1
        exec ":!script/features " . a:filename
      else
        if filereadable("script/test")
          exec ":!script/test " . a:filename
        elseif filereadable("Gemfile")
          exec ":!bundle exec rspec --color " . a:filename
        else
          exec ":!rspec --color " . a:filename
        end
      end
    endfunction

# Database

Homebrew makes installing Redis, MySQL, Postgres, MongoDB all very straightforward. Most of the time you just need to symlink the launch script will do.

    brew install redis
    brew install postgres
    brew install mongodb
    brew install mysql
    brew install elasticsearch

Use https://github.com/jimbojsb/launchrocket at the PreferencePane.

## Restore

    create database jobline_dev;
    mysql -uroot -p jobline_dev < mysql_bak.sql
    select email from users where type='Candidate' limit 10;
    update users set email=CONCAT("sample_", email) where type='Candidate';
    update users set email=CONCAT("jlxyz_", email) where type='Employer';
    
    mongorestore --db jobline_dev --drop ~/Desktop/mongodb_bak_with_timestamp/jobline_pro
    
# FileMaker and VMWare Fusion

* [Change VMWare Fusion 6 NAT IP space](https://coderwall.com/p/mjbryq)

Go to `/Library/Preferences/VMware Fusion` and look for `vmnet8/dhcpd.conf` and `vmnet8/nat.conf`.

## .railsrc

```
--skip-bundle
--skip-test-unit
--database=postgresql
```

## .irbrc

```
require 'rubygems'
require 'awesome_print'

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

## .gemrc

```
---
:backtrace: false
:benchmark: false
:sources:
- https://rubygems.org
:update_sources: true
:verbose: true
install: --no-ri --no-rdoc
update: --no-ri --no-rdoc
```

# Tips

```
// Show or hide .hidden files
defaults write com.apple.Finder AppleShowAllFiles YES
defaults write com.apple.Finder AppleShowAllFiles NO
```

# Resources

* http://robots.thoughtbot.com/the-hitchhikers-guide-to-riding-a-mountain-lion
* http://blog.55minutes.com/2013/09/rails-os-x-install-guide/
* http://www.mitchchn.me/2014/os-x-terminal/
* http://antigen.sharats.me/
* http://shvets.github.io/blog/2014/04/19/configure_macbook.html
* http://lapwinglabs.com/blog/hacker-guide-to-setting-up-your-mac