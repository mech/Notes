# Vim

* [More instantly better Vim](http://www.youtube.com/watch?v=aHm36-na4-4)

## Buffers

Open a file into hidden buffer: `:badd` or `:bad`. Buffer add.

List all buffers, hidden or active: `:ls`

Press `Control-6` to access your alternate buffer (the one indicated by `#`)

* `:bp` - Switch to the previous buffer
* `:bn` - Switch to the next buffer
* `:ball` - Open all buffers into windows
* `:brew` - Go back to the first buffer in the list - Buffer REWing
* `:bd` - Delete the buffer, takes buffer numbers as argument
* You can delete an array of buffer: `:bd 1 2 3`
* Open multiple files in horizontal splits: `vi -o file1 file2`
* Open multiple files in vertical splits: `vi -O file1 file2`
* `:sp` - Horizontal split
* `:vsp` or `Control-w v` - Vertical split

## Windows

* `Control-w h` - Switch to the window to the left
* `Control-w j` - Switch to the window below
* `Control-w k` - Switch to the window above
* `Control-w l` - Switch to the window to the right

Moving Windows

* `Control-w H` - Move current window the far left and use the full height of the screen
* `Control-w J` - Move current window the far bottom and use the full width of the screen
* `Control-w K` - Move current window the far top and full width of the screen
* `Control-w L` - Move current window the far right and full height of the screen

Resizing Windows

* `Control-w =` - Resize windows equally
* `Control-w 20 >` - Incrementally increase the window to the right by 20
* `Control-w 20 <` - Incrementally increase the window to the left by 20
* `Control-w -` - Incrementally decrease the window's height
* `Control-w +` - Incrementally increase the window's height




## New file

`Control-w n` to create a new file.

## Movement

* Use `(` to move to the beginning of a sentence