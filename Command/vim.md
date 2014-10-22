# Vim

```
v # Visual mode
0 # Beginning of the line
$ # End of the line
I # Insert mode at the beginning of the line
a # Append mode
A # Start typing at the end of the line
n # Search forward
N # Search backward
u # Undo, use Ctrl + r to Redo
x # Delete text inline
d w # Delete word.
c w # Change word. Delete a word and type in a new one
d d # Delete entire line
c c # Change line
. # Repeat last command
y y # Yank line
p # Paste line
```

## Delete

* `:%d` to delete whole lines
* `:10,30d` to delete line 10 to 30

## Marking

Go to any line you want to mark and `mk`. The `k` is just any character you chooses. To go to the marked place, use `'k`