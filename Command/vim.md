# Vim

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
c w # Change word. Delete a word and type in a new one
d d # Delete entire line
c c # Change line
.   # Repeat last command
y y # Yank line
p   # Paste line
w   # Move forward to start of next word
b   # Move backward to the start of previous word
e   # Move forward to the 'end' of the next word
ge  # Move backward the 'end' of the previous word
0   # Start of the current line
^   # Start of the first word of the current line (More useful)
$   # End of the current line
-   # Start of the previous line
{   # Start of the current paragraph}   # End of the current paragraph
gg  # Top of the buffer
G   # End of the buffer
50% # Take you to the 50% mark
%   # Move between bracket of {}, (), [] pair
```

## In Insert Mode

In insert mode, you can keep on pressing CTRL-Y to duplicates preceding line and CTRL-E for the following line.

* CTRL-T - insert a tab at the start of the line
* CTRL-D - delete a tab
* CTRL-V - inserts the next character verbatim
* CTRL-W - deletes the word preceding the cursor
* CTRL-O - takes you back to normal mode for just one command and jump you back to insert mode

## Delete

* `:%d` to delete whole lines
* `:10,30d` to delete line 10 to 30

```
# Fix your deletions
:set backspace=indent,eol,start
```

## Searching

Because you need to put a slash in front for all Regular Expression search.

```
/\vfoo|bar
/foo\|bar
```

Or you can just automate it using:

`nnoremap / /\v`

Ignore case also:

```
:set ignorecase
:set smartcase
```

## Marking

Go to any line you want to mark and `mk`. The `k` is just any character you chooses. To go to the marked place, use `'k`

## Buffer

* `Ctrl-O` and `Ctrl-I` in normal mode to jump around previously opened buffer even cross terminals.
* `Ctrl-^` to toggle between current and the last buffer
* `:bd` to delete the current buffer
* `:bd!` to delete the current buffer regardless of saved or not
* `:b12` to go to buffer numbered 12

## Plugins

* [Statusline Watchdog](https://github.com/avakarev/vim-watchdog)
* [matchit.vim](http://www.vim.org/scripts/script.php?script_id=39)