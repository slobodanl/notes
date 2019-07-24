# vim keys

_Written by: Reza Shams Amiri_

# vim keys

## 1.1. vim

to open several files in split mode use:

`vim -O *.txt`

or

`vim -O ~/.zshrc ~/zshrc.local.sh`

to enable plugin docs (help), you need to run

`:helptags ALL`

Commands

## Normal vim keys

| command | description |
| ------- | ----------- |
| b | Goto the begining of the previouse word |
| B | Goto the begining of the previouse word (space separated) |
| w | Goto the begining of the next word |
| W | Goto the begining of the next word (space separated) |

## Files and Buffers

| command | description |
| ------- | ----------- |
| `:vert help e` | show help in vertical mode |
| `:vsp` | open another file in vertical |
| `:vsp ~/.zshrc` | open another file in vertical |
| `:e ~/.zshrc` | open another file in a new buffer |
| `:set splitright` | set files to open in right |
| `:vsp#2` | vertical split |
| `:h tag` | open help page for tag vertically |
| `:e!` | reload current file |

## Buffer manipulation

| command | description |
| ------- | ----------- |
| <kbd>ctrl</kbd>+<kbd>q</kbd> |  _close current buffer_{.hl} |
| <kbd>ctrl</kbd>+<kbd>wc</kbd> |  close current window |
| `:bd` |  close current buffer |
| `,q` |  delete current buffer and move on |
|||
| <kbd>,,</kbd> |  _toggle previous buffer_{.hl} |
| <kbd>shift</kbd> + <kbd></kbd>/<kbd></kbd> arrow |  _move to next or previous_{.hl} buffer |
| `:bn` |  next buffer |

## Window manipulation

| command | description |
| ------- | ----------- |
| `:help CTRL-W` | see also |
| `:help opening-window` |  |
|  |  |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>n</kbd> :new | edit a new buffer |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>s</kbd> :sp | split buffer |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>v</kbd> :vsp | split vertically |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>o</kbd> :only | only this window |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>c</kbd> :close | close window ( close cannot close last window ) |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>q</kbd> :quit | quit window ( quit can also close last window ) |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>H</kbd>,<kbd>J</kbd>,<kbd>K</kbd>, or <kbd>L</kbd> | will move the current window to the far left, bottom, top, or right |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>h</kbd>,<kbd>j</kbd>,<kbd>k</kbd>, or <kbd>l</kbd> | will focus instead of moving the windows |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>v</kbd> | split current window |
|  |  |
| #N _ | set height to #N (ex. `50<C-w>_`) |
| \#N \|\_\_\_ | set width to #N (ex. `50<C-w>|`) |
| = | equalize width and height of all windows |
|  |  |
|  | Toggle single mode through ZoomWin plugin (second toggle is slow) |
|  |  |

## Copy & Paste
| command | description |
| ------- | ----------- |
|Copy and then paste in command bar|Select the block in visual mode, <kbd>y</kbd> to yank, press <kbd>:</kbd> then press <kbd>Ctrl</kbd>+<kbd>r</kbd> and press <kbd>"</kbd>

## Search & Replace

| command | description |
| ------- | ----------- |
| <kbd>/</kbd><kbd>q</kbd>| will unselect/unhighlight what ever you have selected or searched for|
| <kbd>/</kbd><kbd>/</kbd> followd by <kbd>Ctrl</kbd>+<kbd>n</kbd>| Select visually some text and in vmod press <kbd>/</kbd><kbd>/</kbd> to search the whole document for it. After selection is made use <kbd>Ctrl</kbd>+<kbd>n</kbd> to replace|
| `:%s//new-string/g` | First use <kbd>*</kbd> to highlight the words, then run this for replacing all |
|  <kbd>Ctrl</kbd> + <kbd>n</kbd>| This is a shortcut for the above one liner |
|  |  |
| `:%s/foo/bar/g` | replaces foo with bar in all lines |
| `:s/foo/bar/g` | replaces foo with bar only in current line |
| `:%s/foo/bar/gc` | replaces all foos with bar but asks each time |
| `:%s/\<foo>/bar/gc` | replaces all exact "foo"s with "bar" with confirmation |
| `:%s/foo/bar/gci` | (case insensitive) replaces all "foo"s with "bar" with confirmation |
| `:set ignorecase` | make all searches case insensitive |

## Key mapping

| command | description |
| ------- | ----------- |
| `:verbose imap` | Show where the keymap is defined and in which file/plugin |
| `:scripts` | Shows all effective scripts |
| `:map` | Show all keymaps |
| `F9` `:call ExportMap()` | Exports all keymapping to /tmp/vi_maps.txt and opens it in vim |

## Syntax Highlighter

| command | description |
| ------- | ----------- |
| `:set syntax=yaml` | for wrong or unknown types you can manually set syntax |

## spell checker

| command | description |
| ------- | ----------- |
| `,s` | toggle spell checker |
| `z=` | show the suggestions |
| `zg` | add to dictionary |

## white space

| command | description |
| ------- | ----------- |
| `set list` | show listchars including tab |
| `set nolist` | hide listchars including tab |
| `:w !sudo tee %` | save file with sudo privileges |

## function key mapping

| command | description |
| ------- | ----------- |
| <kbd>F2</kbd> | toggle paste ~/paste |
| <kbd>F3</kbd> | Toggle nerd tree |
| <kbd>F4</kbd> | Toggle highlight |
| <kbd>F5</kbd> | Toggle list invisible characters like tabs |
| <kbd>F6</kbd> | Toggle showing the line numbers (set norelativenumber for absolute) |
| <kbd>F7</kbd> | Toggle showing undo tree |
| <kbd>F8</kbd> | Toggle wrap and its indicator |
| <kbd>F9</kbd> | Show all keybindings |
| <kbd>F10</kbd> | Trim all white spaces in the current file |
| <kbd>ctrl</kbd> + <kbd>l</kbd> | Preview markdown page using `bat` |
| <kbd>ctrl</kbd> + <kbd>F5</kbd> | Save and run the current file |

## vim-sneak

| command | description |
| ------- | ----------- |
| sab | Type sab to move the cursor to next instance of "ab" |
| ; | Go to the next match (or s agin if s_next is enabled) |
| `` | `` Go back to the starting point or jump back |

## visual block mode

| command | description |
| ------- | ----------- |
| <kbd>ctrl</kbd> + <kbd>v</kbd> | By pressing ctrl+v you can enter visual block mode, when you are in |
|  | visual block mode you can do the following actions: |
|  |  |
| <kbd>shift</kbd>+<kbd>i</kbd> | goto insert mode. Any character typed will be inserted at top |
|  | of the selection and when pressing it would be applied to all |
|  <kbd>c</kbd> | change the selected area |
|  <kbd>r</kbd> | change the current character |
|  <kbd>o</kbd> | move to the begining of the selected box |

## vim-neosnippets

| command | description |
| ------- | ----------- |
| ctrl + k | Choose snippet |
| tab | Move to the next field of the snippet |
| ctrl + p | Previous item in neocomplete list |
| ctrl + n | Next item in neocomplete list |
|  |  |

## vim-sorround

| command | description |
| ------- | ----------- |
| **visual mode** |  |
|  |  |
| <kbd>S"</kbd> | Sorround selection with " |
|  |  |
| **normal mode** |  |
|  |  |
| <kbd>cs'"</kbd> | Change Sorround ' -> " (do it inside 'test') |
| <kbd>cs'</kbd> then <kbd>q</kbd> | Change Sorround ' -> <q>(do it inside 'test')</q> |
| <kbd>ds'</kbd> | Remove delimiter sorrounding of ' (do it inside 'test') |
| <kbd>di'</kbd> | Remove inside sorrounfing of ' (do it inside 'test') |
| <kbd>vlllls'</kbd> | Sorround virtual selection with ' (go to V then 4left and s) |
|  |  |
| **insert mode** |  |
|  | **sorround** |
| ysiw( | Sorround word with ( ex: ( sneak ) |
| ysiW( | Sorround whole word with ( ex: ( g:sneak#s-next = 1 ) |
| ysw( | Sorround word with ( ex: ( sneak ) |
| ysW( | Sorround whole word with ( ex: ( g:sneak#s-next = 1 ) |
|  |  |
|  | The difference between ysiw and ysw is that with i(nner text) |
|  | the whole word would be modified however without it from the |
|  | cursor position to the end of the word will be sorrounded |
|  |  |
| yss | yss operates on the current line ignoring the leading space |
| yssB | Sorround current line with block: {Hello world!} |
| yssb | Sorround current line with parantesis: (Hello world!) |
|  |  |
| ySS | Sorrounds the current line but puts delimters in separate lines |
|  | and idents the current line |
|  |  |
|  | In insert mode starts writing in a block |
| vS | In visual mode a capital S will result in sorrounding lines |
| vS" | Sorround selection with " |

| command | description |
| ------- | ----------- |
| **MISCELLANEOUS** |  |
| / | Toggle comment for the selected text or block #comment #toggle |
| gc | Toggle comment for the selected text or block |
| g> | Toggle comment for the selected text or block |
|  |  |
| set nonumber | Hide line numbers #hide #line #lineno |
| set number | Show line numbers |
| set tm=0 | Set timeout to 0, causes faster response and no waiting |
| set tm=1000 | Set timeout to 1000, good for cases that leader shortcuts dont work |
|  |  |
| . | Auto compilation |
| :w!! | Vim sudo trick or :w !sudo tee > /dev/null % |
| o | Vim sudo trick or :w !sudo tee > /dev/null % #force #write |
| :red | Redo #redo |
| r | Reload (notifies if file has been changed) #reload |
| r | Force reload :e! #force #reload |
| gx | In normal mode, if you stand on a link and enter `g` then `x` |
|  | the link will be opened in a browser window #browser #link |
| <kbd>CTRL</kbd> + <kbd>f</kbd> | (only in insert mode) call rofi to select an email address from mutt aliases |

| command | description |
| ------- | ----------- |
| **CLI** | **These can be used when calling vim from command line** |
|  | **ex:** `vim +/^$ ++1 -c "noh" my-mail.txt` |
| +/^$ | Search and jump to empty lines (will highlight them as well) |
| ++1 | move one line down |
| -c "noh" | `:noh` or no highligh, removes already highlighted matches |
|  |  |

| command | description |
| ------- | ----------- |
| **FILETYPES** | **This is how to set vim syntax highlighting** |
| `# vim: fdm=marker` |  |
| `# vim: filetype=muttrc` |  |
| `set ft=bash` | temporary set filetype to `bash` |

| command | description |
| ------- | ----------- |
| **installing plugins** |  |
| vim ~/.vimrc | edit `vimrc` and in the section which begins with: (circa 338) |
|  | `call plug#begin('~/.vim/plugged')` |
|  | --> Plug 'https://github.com/PotatoesMaster/i3-vim-syntax.git' |
|  | or --> Plug 'PotatoesMaster/i3-vim-syntax.git' |
|  |  |
|  | then inside vim run: |
|  |  |
|  | `:PlugInstall` or |
|  | `:PlugUpdate` |
|  |  |

- - -

Creation date: _2018/09/03_