## VIM REFERENCE MANUAL  
 ```bash
https://vimhelp.org/index.txt.html
```

## Global
```bash
:help keyword # open help for keyword
:o file       # open file
:saveas file  # save file as
:close        # close current pane
```

## Cursor movement
```bash
h        # move cursor left
j        # move cursor down
k        # move cursor up
l        # move cursor right
H        # move to top of screen
M        # move to middle of screen
L        # move to bottom of screen
w        # jump forwards to the start of a word
W        # jump forwards to the start of a word (words can contain punctuation)
e        # jump forwards to the end of a word
E        # jump forwards to the end of a word (words can contain punctuation)
b        # jump backwards to the start of a word
B        # jump backwards to the start of a word (words can contain punctuation)
%        # move to matching character (default supported pairs: '()', '{}', '[]' - use :h matchpairs in vim for more info)
0        # jump to the start of the line
^        # jump to the first non-blank character of the line
$        # jump to the end of the line
g_       # jump to the last non-blank character of the line
gg       # go to the first line of the document
G        # go to the last line of the document
5G       # go to line 5
fx       # jump to next occurrence of character x
tx       # jump to before next occurrence of character x
fx       # jump to next occurrence of character x
tx       # jump to before next occurrence of character x
Fx       # jump to previous occurence of character x
Tx       # jump to after previous occurence of character x
}        # jump to next paragraph (or function/block, when editing code)
{        # jump to previous paragraph (or function/block, when editing code)
;        # repeat previous f, t, F or T movement
,        # repeat previous f, t, F or T movement, backwards
zz       # center cursor on screen
Ctrl + e # move screen down one line (without moving cursor)
Ctrl + y # move screen up one line (without moving cursor)
Ctrl + b # move back one full screen
Ctrl + f # move forward one full screen
Ctrl + d # move forward 1/2 a screen
Ctrl + u # move back 1/2 a screen

Tip Prefix a cursor movement command with a number to repeat it. For example, 4j moves down 4 lines.
```
## Insert mode - inserting/appending text
```bash
i        # insert before the cursor
I        # insert at the beginning of the line
a        # insert (append) after the cursor
A        # insert (append) at the end of the line
o        # append (open) a new line below the current line
O        # append (open) a new line above the current line
ea       # insert (append) at the end of the word
Ctrl + h # delete the character before the cursor during insert mode
Ctrl + w # delete word before the cursor during insert mode
Ctrl + j # begin new line during insert mode
Ctrl + t # indent (move right) line one shiftwidth during insert mode
Ctrl + d # de-indent (move left) line one shiftwidth during insert mode
Ctrl + n # insert (auto-complete) next match before the cursor during insert mode
Ctrl + p # insert (auto-complete) previous match before the cursor during insert mode
Esc      # exit insert mode
```
## Editing
```bash
r        # replace a single character
J        # join line below to the current one
gJ       # join line below to the current one without space in between
gwip     # reflow paragraph
g~       # switch case up to motion
gu       # change to lowercase up to motion
gU       # change to uppercase up to motion
cc       # change (replace) entire line
C        # change (replace) to the end of the line
c$       # change (replace) to the end of the line
ciw      # change (replace) entire word
cw       # change (replace) to the start of the next word
ce       # change (replace) to the end of the next word
cb       # change (replace) to the start of the previous word
c0       # change (replace) to the start of the line
s        # delete character and substitute text
S        # delete line and substitute text (same as cc)
xp       # transpose two letters (delete and paste)
u        # undo
U        # restore (undo) last changed line
Ctrl + r # redo
.        # repeat last command
```
## Marking text (visual mode)
```bash
v        # start visual mode, mark lines, then do a command (like y-yank)
V        # start linewise visual mode
o        # move to other end of marked area
O        # move to other corner of block
aw       # mark a word
ab       # a block with ()
aB       # a block with {}
ib       # inner block with ()
iB       # inner block with {}
Esc      # exit visual mode
Ctrl + v # start visual block mode

Tip Instead of b or B one can also use ( or { respectively.

```
## Visual commands
```bash
>       # shift text right
<       # shift text left
y       # yank (copy) marked text
d       # delete marked text
~       # switch case
u       #- change marked text to lowercase
U       # change marked text to uppercase
```
## Cut and paste
```bash
yy       # yank (copy) a line
2yy      # yank (copy) 2 lines
yw       # yank (copy) the characters of the word from the cursor position to the start of the next word
y$       # yank (copy) to end of line
p        # put (paste) the clipboard after cursor
P        # put (paste) before cursor
dd       # delete (cut) a line
2dd      # delete (cut) 2 lines
dw       # delete (cut) the characters of the word from the cursor position to the start of the next word
D        # delete (cut) to the end of the line
d$       # delete (cut) to the end of the line
d^       # delete (cut) to the first non-blank character of the line
d0       # delete (cut) to the begining of the line
x        # delete (cut) character
```
## Search and replace
```bash
/pattern       # search for pattern
?pattern       # search backward for pattern
\vpattern      # 'very magic' pattern: non-alphanumeric characters are interpreted as special regex symbols (no escaping needed)
n              # repeat search in same direction
N              # repeat search in opposite direction
:%s/old/new/g  # replace all old with new throughout file
:%s/old/new/gc # replace all old with new throughout file with confirmations
:noh           # remove highlighting of search matches
```
## Search in multiple files
```bash
:vimgrep /pattern/ {file} # search for pattern in multiple files
:cn                       # jump to the next match
:cp                       # jump to the previous match
:copen                    # open a window containing the list of matches
```
## Exiting
```bash
:w              # write (save) the file, but don't exit
:w !sudo tee %  # write out the current file using sudo
:wq or :x or ZZ # write (save) and quit
:q              # quit (fails if there are unsaved changes)
:q! or ZQ       # quit and throw away unsaved changes
```
## Working with multiple files
```bash
:e file       # edit a file in a new buffer
:bnext or :bn # go to the next buffer
:bprev or :bp # go to the previous buffer
:bd           # delete a buffer (close a file)
:ls           # list all open buffers
:sp file      # open a file in a new buffer and split window
:vsp file     # open a file in a new buffer and vertically split window
Ctrl + ws     # split window
Ctrl + ww     # switch windows
Ctrl + wq     # quit a window
Ctrl + wv     # split window vertically
Ctrl + wh     # move cursor to the left window (vertical split)
Ctrl + wl     # move cursor to the right window (vertical split)
Ctrl + wj     # move cursor to the window below (horizontal split)
Ctrl + wk     # move cursor to the window above (horizontal split)
```
## Tabs
```bash
:tabnew or :tabnew file # open a file in a new tab
Ctrl + wT               # move the current split window into its own tab
gt or :tabnext or :tabn # move to the next tab
gT or :tabprev or :tabp # move to the previous tab
<number>gt              # move to tab <number>
:tabmove <number>       # move current tab to the <number>th position (indexed from 0)
:tabclose or :tabc      # close the current tab and all its windows
:tabonly or :tabo       # close all tabs except for the current one
:tabdo command          # run the command on all tabs (e.g. :tabdo q - closes all opened tabs)
```


## .vimrc **work in progress**
```bash 
My .vimrc file has some pretty great ideas I haven’t seen elsewhere.
This is a minimal vimrc that focuses on three priorities:
adding options that are strictly better (like more information showing in autocomplete)
more convenient keystrokes (like [space]w for write, instead of :w [enter])
a similar workflow to normal text editors (like enabling the mouse)
Installation
Copy this to your home directory and restart Vim. Read through it to see what you can now do (like [space]w to save a file)
Mac users - making a hidden normal file is suprisingly tricky. Here’s one way:
in the command line, go to the home directory
type nano .vimrc
paste in the contents of the .vimrc file
ctrl+x, y, [enter] to save
You should now be able to press [space]w in normal mode to save a file.
[space]p should paste from the system clipboard (outside of Vim).
If you can’t paste, it’s probably because Vim was not built with the system clipboard option. To check, run vim --version and see if +clipboard exists. If it says -clipboard, you will not be able to copy from outside of Vim.
For Mac users, homebrew install Vim with the clipboard option. Install homebrew and then run brew install vim.
then move the old Vim binary: $ mv /usr/bin/vim /usr/bin/vimold
restart your terminal and you should see vim --version now with +clipboard
```
## Plugins
```bash
The easiest way to make Vim more powerful is to use Vintageous in Sublime Text (version 3). This gives you Vim mode inside Sublime. I suggest this (or a similar setup with the Atom editor) if you aren’t a Vim master. Check out Advanced Vim if you are.
Vintageous is great, but I suggest you change a few settings to make it better.
Clone this repository to ~/.config/sublime-text-3/Packages/Vintageous, or similar. Then check out the “custom” branch.
Alternatively, you can get a more updated Vintageous version by cloning the official repository and then copying over this patch.
Change the user settings (User/Preferences.sublime-settings) to include:
"caret_style": "solid"
This will make the cursor not blink, like in Vim.
Sublime Text might freeze when you do this. It’s a bug; just restart Sublime Text after changing the file.
ctrl+r in Vim means “redo”. But there is a handy Ctrl + R shortcut in Sublime Text that gives an “outline” of a file. I remapped it to alt+r by putting this in the User keymap
{ "keys": ["alt+r"], "command": "show_overlay", "args": {"overlay": "goto", "text": "@"} },
Add the ability to toggle Vintageous on and off
Mac users: you will not have the ability to hold down a navigation key (like holding j to go down). To fix this, run the commands specified here: https://gist.github.com/kconragan/2510186
Now you should be able to restart sublime and have a great Vim environment! Sweet Dude.
```

## Switch Caps Lock and Escape
```bash I highly recommend you switch the mapping of your escape keys to caps lock or jj . You’ll love it, promise! Switching the two keys is platform dependent; Google should get you the answer.
```
