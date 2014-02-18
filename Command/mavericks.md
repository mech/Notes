# System Installation with Mavericks

1. Install Xcode
2. `xcode-select --install` to install Xcode Command Line Tools
3. To make sure, type `gcc --version`
4. Install `oh-my-zsh` via `curl`
5. Install Homebrew. `brew update` and `brew doctor` first6. 
6. Because we still have Ruby 1.8 application, we need to use GCC 4.2.

       brew tap homebrew/dupes
       brew install autoconf automake apple-gcc42

7. If you need X11, you can install it [here](http://xquartz.macosforge.org/landing/). You will want to `sudo ln -s /opt/X11 /usr/X11` also.
8. Preparing for Git installation. Mavericks come with git, but we want to install it via `brew install git` which will reside at `/usr/local/bin/git`. Edit `.zshrc` to move that path forward: `export PATH="/usr/local/git/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin"`

   Configure git with:
   
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
       git config --global --bool pull.rebase true

9. Includes these at `.zshrc`

       export EDITOR=vi
       export LC_CTYPE=en_US.UTF-8
       export LC_ALL=en_US.UTF-8
       export LANG=en_US.UTF-8
       export CPPFLAGS=-I/opt/X11/include

10. Now is time to generate SSH, and always give a passphrase!

        ssh-keygen -t rsa -C "mech@me.com"
        ssh-add id_rsa
        ssh-copy-id -i ~/.ssh/id_rsa.pub administrator@58.185.193.188
        
    Paste the `id_rsa.pub` to GitHub and test it `ssh -T git@github.com`

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

    PROMPT='%{$fg[green]%}%p%{$fg[cyan]%}%c %{$fg[yellow]%}
    (git_prompt_info)%{$fg[green]%}$%{$reset_color%} '
    
    ZSH_THEME_GIT_PROMPT_PREFIX="(%{$fg[yellow]%}"
    ZSH_THEME_GIT_PROMPT_SUFFIX="%{$reset_color%}"
    ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[yellow]%})%{$fg[red]%}⚡ %{$reset_color%}"
    ZSH_THEME_GIT_PROMPT_CLEAN="%{$fg[yellow]%}) "


# Sublime

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

# Resources

* http://robots.thoughtbot.com/the-hitchhikers-guide-to-riding-a-mountain-lion