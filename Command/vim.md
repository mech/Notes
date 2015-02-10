# Vim

* [**Learn VimScript the hard way**](http://learnvimscriptthehardway.stevelosh.com/)
* [Cheat Sheet](http://www.lagmonster.org/docs/vi.html)
* [Vim customised to be like SublimeText](https://github.com/subvim/subvim)
* [**Thoughtbot VIM tags**](http://robots.thoughtbot.com/tags/vim)
* Tim Pope - abolish.vim, commentary.vim, dispatch.vim, endwise.vim, eunuch.vim, fugitive.vim, rsi.vim, scriptease.vim, sensible.vim, sleuth.vim, surround.vim, unimpaired.vim
* [Shortcut Foo](http://www.shortcutfoo.com/app/dojos/vim)
* [Best of Vim](http://www.bestofvim.com/)
* [Trailing whitespace](http://www.bestofvim.com/tip/trailing-whitespace/)

```
v   # Visual mode
0   # Beginning of the line
$   # End of the line
I   # Insert mode at the beginning of the line
a   # Append mode
A   # Start typing at the end of the line
n   # Search forward
N   # Search backward
u   # Undo, use Ctrl + r to Redo
x   # Delete text inline
d w # Delete word.
d $ # Delete whatever is end of the line
c w # Change word. Delete a word and type in a new one
d d # Delete entire line
c c # Change line
.   # Repeat last command
y y # Yank line
p   # Paste line
w   # Move forward to start of next word
W   # Move forward for code word
b   # Move backward to the start of previous word
B   # Move backward for code word
e   # Move forward to the 'end' of the next word
E   # Move forward to the 'end' of code word
ge  # Move backward the 'end' of the previous word
0   # Start of the current line
^   # Start of the first word of the current line (More useful)
$   # End of the current line
-   # Start of the previous line
{   # Start of the current paragraph}   # End of the current paragraph
gg  # Top of the buffer
G   # End of the buffer
50% # Take you to the 50% mark
H   # Near top
M   # Middle of the screen text
L   # Near bottom
%   # Move between bracket of {}, (), [] pair
ZZ  # Exit and save changes
:x  # Exit, saving changes
:verbose set wildmode # Query where settings are set
:set # Find all your options
gf  # Jump to the file under cursor. Go to file.
>>  # Indent
Ctrl-d # Indent also while in insert mode
Ctrl-t # Indent also while in insert mode
:set paste   # -- INSERT (paste) --
:set nopaste
```

```
# Associate .es6 file to .js file if you using 6to5
autocmd BufRead,BufNewFile *.es6 setfiletype javascript
```

## Motion

## Mappings

Mimic keystrokes to provide shortcuts to frequently used commands.

Modes of mapping:

* `nmap` - Normal mode
* `imap` - Insert mode
* `vmap` - Visual mode
* `map`  - Normal, Visual, and operating-pending modes
* `map!` - Command and insert modes

```
:vmap # Show all mappings
```

`<leader>` is meant to not conflict with vim's existing mapping.

## Abbreviations

Correct your spelling mistake.

```
:iab ff Firefox # Declare abbreviation for insert mode
:ab teh the
```

## Scrolling

* `Ctrl-b` - Up screen
* `Ctrl-u` - 1/2 screen up
* `Ctrl-y` - Line up
* `Ctrl-e` - Line down
* `Ctrl-d` - 1/2 screen down
* `Ctrl-f` - Down screen
* 
* `zt` - Near top
* `zz` - Middle
* `zb` - Near bottom
* 
* 42gg - Same as 42G
* 
* g Ctrl-g - Will tell you your line status

## Insert Mode

In insert mode, you can keep on pressing CTRL-Y to duplicates preceding line and CTRL-E for the following line.

* CTRL-T - insert a tab at the start of the line
* CTRL-D - delete a tab
* CTRL-V - inserts the next character verbatim
* CTRL-W - deletes the word preceding the cursor
* CTRL-O - takes you back to normal mode for just one command and jump you back to insert mode

## Deleting

* `:%d` to delete whole lines
* `:10,30d` to delete line 10 to 30
* `dap` to delete a un-breaking line

```
# Fix your deletions
:set backspace=indent,eol,start
```

## Registers

Use register `a`, then `yy` to copy current line. `"ap` to paste from register `a`.

```
"ayy
"ap

0p # Paste from the zero register (contents of the last yank command)
```

## Searching

Because you need to put a slash in front for all Regular Expression search.

```
/\vfoo|bar # Very magic regular expression style, see egrep vs grep
/foo\|bar
?useful    # Search backward with question mark
```

* `/` - Search forward
* `?` - Search backward
* `n` - Next match
* `N` - Previous match
* `*` - Next current word (where your cursor is)
* `#` - Previous current word
* `g*` - Next partial match

Or you can just automate it using:

`nnoremap / /\v`

Ignore case also:

```
:set ignorecase
:set smartcase
```

```
" Percent searches all lines
:%s/search/replace/g

" Omit percent to search only current line
:s/search/replace/
```

## Folding

```
:set foldmethod=manual
```

* `indent` - Use spaces or tabs to find foldable blocks
* `syntax` - Fold on language features (methods, classes)
* `marker` - Fold on textual marks
* `diff`   - Fold unchanged text
* `expr`   - Custom, code-driven folding
* `manual` - Select ranges to fold

To close/open:

* `zo` - Open
* `zc` - Close
* `za` - Toggle
* `zM` - All close
* `zR` - All open
* `zk` - Move up
* `zj` - Move down
* `zi` - Toggle all open or close
* `zx` - Reset all except those under cursor

## Marking

Go to any line you want to mark and `mk`. The `k` is just any character you chooses. To go to the marked place, use `'k`

## Window Management

All commands start with `Ctrl-w`

* `<C-w> s` - Split horizontally
* `<C-w> v` - Split vertically
* `<C-w> c` - Close window
* `<C-w> o` - Close all but current window
* 
* `<C-w> j` - Move focus down
* `<C-w> k` - Move focus up
* `<C-w> h` - Focus on left window
* `<C-w> l` - Focus on right window
* `<C-w> J` - Move buffer up one window
* `<C-w> K` - Move buffer down one window
* `<C-w> H` - Move buffer to left
* `<C-w> L` - Move buffer to right
* 
* `<C-w> w` - Cycle focus counterclockwise
* `<C-w> W` - Cycle focus clockwise
* `<C-w> p` - Focus previous window
* `<C-w> t` - Top
* `<C-w> b` - Bottom
* 
* `<C-w> r`
* `<C-w> R`
* 
* `<C-w> x` - Exchanges the windows
* 
* `<C-w> =` - Make all windows equally high and wide
* `<C-w> <` - Decrease current window width by N (default 1)
* `<C-w> >` - Increase current window width by N (default 1)
* `<C-w> -` - Decrease current window height by N (default 1)
* `<C-w> +` - Increase current window height by N (default 1)

A single window can have many buffers.

## Buffer

* `Ctrl-O` and `Ctrl-I` in normal mode to jump around previously opened buffer even cross terminals.
* `Ctrl-^` to toggle between current and the last buffer
* `:ls` to list buffers
* `:bd` to delete the current buffer
* `:bd!` to delete the current buffer regardless of saved or not
* `:b12` to go to buffer numbered 12
* `:bf` to first buffer
* `:bl` to last buffer
* `:ba` open all??

## Tabs

A tab hold one or more windows.

* [Switch between tabs](http://superuser.com/questions/410982/in-vim-how-can-i-quickly-switch-between-tabs)
* For CtrlP, use `<c-t>` or `<c-v>`, `<c-x>` to open the selected entry in a new tab or in a new split.
* `gt` - Next tab
* `gT` - Previous tab
* `<number>gt` - Numbered tab

## Help

* `:helpgrep PATTERN`
* `:vimgrep /PATTERN/`
* `:help normal-index`
* `:help insert-index`

Use `:cnext` to page through

Type `ZZ` or `:q` to get out of help.

## Plugins

* [BufExplorer](https://github.com/jlanzarotta/bufexplorer)
* [vim-better-whitespace](https://github.com/ntpeters/vim-better-whitespace)
* [Statusline Watchdog](https://github.com/avakarev/vim-watchdog)
* [matchit.vim](http://www.vim.org/scripts/script.php?script_id=39)
* [simplefold](http://www.vim.org/scripts/script.php?script_id=1868)