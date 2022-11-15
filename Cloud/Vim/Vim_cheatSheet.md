# VIM

- The purpose of vim is to make your coding experience easier and efficient.
- we can start vim by doing "vim" in your terminal IDE , or Command prompt.

- There are different modes in vim. Theres the normal mode where you execute commands and insert mode where you insert characters into the file.

### COMMAND mode(esc to get to the mode):

- e jump to end of line
- dd to delete a line
- x to delete a character
- w to delete a word
- :qa , exits out of all buffers and warns you to save unsaved changes
- :q! , exits out of the file and doesnt warn you about unsaved changes
- :wq, saves changes and then exits out of file
- :w, write to the file

- 7 up: go up 7(same concept with going down to the right and left)
- I to go to the beginning of the line
- A to go to the end of the line
- O to start on the top line
- :set number , activates line numbers
- :set tabstop: 4
- :colorscheme slate

### INSERT mode(i to get to the mode):

- Ctrl + t - indent (move right) line one shiftwidth during insert mode
- Ctrl + w - delete a whole word
- Ctrl + u - all values to the left will be deleted

TERMINAL mode:

- vi ~ /.vimrc .. to go to vims config file... ideal to do all configurations in this file

```
set number
set relativenumber
set tabstop=4
set shiftwidth=4
set autoindent

```

Visual Mode(v):
d - deletes
dw- deletes word
y - (yanking) copies
p - pastes
Y - copies the full line
D- deletes the rest of the line
