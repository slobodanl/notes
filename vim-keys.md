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

## Files and Buffers
| command | description |
| ------- | ----------- |
| <kbd>shift</kbd> + <kbd>right</kbd>/<kbd>left</kbd> arrow | move to next or previous buffer |
| <kbd>shift</kbd> + <kbd>right</kbd>/<kbd>left</kbd> arrow | move to next or previous buffer |
| <kbd>ctrl</kbd>+<kbd>w</kbd><kbd>c</kbd> or <kbd>ctrl</kbd>+<kbd>q</kbd> | close current buffer |
| <kbd>,</kbd><kbd>,</kbd> | toggle previous buffer |
| `:bd` | close current buffer |
| `,q` | delete current buffer and move on |
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
| `:bn` | next buffer |
| `,q` | delete current buffer and move on |

## Window manipulation

| command | description |
| ------- | ----------- |
| `:help CTRL-W` | see also |
| `:help opening-window` | |
| | |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>n</kbd> :new | edit a new buffer |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>s</kbd> :sp | split buffer |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>v</kbd> :vsp | split vertically |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>o</kbd> :only | only this window |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>c</kbd> :close | close window ( close cannot close last window ) |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>q</kbd> :quit | quit window ( quit can also close last window ) |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>H</kbd>,<kbd>J</kbd>,<kbd>K</kbd>, or <kbd>L</kbd> | will move the current window to the far left, bottom, top, or right |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>h</kbd>,<kbd>j</kbd>,<kbd>k</kbd>, or <kbd>l</kbd> | will focus instead of moving the windows |
| <kbd>CTRL</kbd>-<kbd>W</kbd> <kbd>v</kbd> | split current window |
| | |
| #N _ | set height to #N (ex. `50<C-w>_`) |
| \#N \|\_\_\_ | set width to \#N \(ex\. `50<C-w>|`) |
| = | equalize width and height of all windows |
| | |
| | Toggle single mode through ZoomWin plugin (second toggle is slow) |
| | |
## search & replace 
| command | description |
| ------- | ----------- |
| `:%s//new-string/g` | First use <kbd>*</kbd> to highlight the words, then run this for replacing all |
| | This is a shortcut for the above one liner |
| | |
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
| ``|`` Go back to the starting point or jump back |

## visual block mode 
| command | description |
| ------- | ----------- |
| ctrl + v | By pressing ctrl+v you can enter visual block mode, when you are in |
| ════════╕ | visual block mode you can do the following actions: |
| │ | |
| ├─ shift+i | goto insert mode. Any character typed will be inserted at top |
| │ | of the selection and when pressing it would be applied to all |

| │ | |
| ├─ c | change the selected area |
| ├─ r | change the current character |
| ├─ o | move to the begining of the selected box |
| | |

## vim-neosnippets
| command | description |
| ------- | ----------- |
| ctrl + k | Choose snippet |
| tab | Move to the next field of the snippet |
| ctrl + p | Previous item in neocomplete list |
| ctrl + n | Next item in neocomplete list |
| | |

## vim-sorround 

| command | description |
| ------- | ----------- |
| **visual mode** ||
| | |
| <kbd>S</kbd><kbd>"</kbd> | Sorround selection with " |
| | |
| **normal mode**||
| | |
| `cs'"` | Change Sorround ' -> " (do it inside 'test') |
| `cs'` then <q>| Change Sorround ' -> <q>(do it inside 'test') |</q></q>
| `ds'` | Remove delimiter sorrounding of ' (do it inside 'test') |
| `di'` | Remove inside sorrounfing of ' (do it inside 'test') |
| `vllllllls'` | Sorround virtual selection with ' (go to V then 4left and s) |
| | |
| **insert mode** ||
| | #sorround |
| ysiw( | Sorround word with ( ex: ( sneak ) |
| ysiW( | Sorround whole word with ( ex: ( g:sneak#s-next = 1 ) |
| ysw( | Sorround word with ( ex: ( sneak ) |
| ysW( | Sorround whole word with ( ex: ( g:sneak#s-next = 1 ) |
| | |
| | The difference between ysiw and ysw is that with i(nner text) |
| | the whole word would be modified however without it from the |
| | cursor position to the end of the word will be sorrounded |
| | |
| yss | yss operates on the current line ignoring the leading space |
| yssB | Sorround current line with block: {Hello world!} |
| yssb | Sorround current line with parantesis: (Hello world!) |
| | |
| ySS | Sorrounds the current line but puts delimters in separate lines |
| | and idents the current line |
| | |
| | In insert mode starts writing in a block |

| | |
| vS | In visual mode a capital S will result in sorrounding lines |
| vS" | Sorround selection with " |
╠═════╣ miscellaneous ╠════════╬═════════════════════════════════════════════════════════════════════╣
| | |
| / | Toggle comment for the selected text or block #comment #toggle |

| gc | Toggle comment for the selected text or block |
| g> | Toggle comment for the selected text or block |
| | |
| set nonumber | Hide line numbers #hide #line #lineno |
| set number | Show line numbers |
| set tm=0 | Set timeout to 0, causes faster response and no waiting |
| set tm=1000 | Set timeout to 1000, good for cases that leader shortcuts dont work |
| | |
| . | Auto compilation |
| :w!! | Vim sudo trick or :w !sudo tee > /dev/null % |
| o | Vim sudo trick or :w !sudo tee > /dev/null % #force #write |

| :red | Redo #redo |
| r | Reload (notifies if file has been changed) #reload |

| r | Force reload :e! #force #reload |

| gx | In normal mode, if you stand on a link and enter `g` then `x` |
| | the link will be opened in a browser window #browser #link |
| | |
╠════╣ installing plugins ╠════╬═════════════════════════════════════════════════════════════════════╣
| | |
| vim ~/.vimrc | edit vimrc and in the section which begins with: (circa 338) |
| | call plug#begin('~/.vim/plugged') |
| | --> Plug 'https://github.com/PotatoesMaster/i3-vim-syntax.git'|
| | or --> Plug 'PotatoesMaster/i3-vim-syntax.git' 					 |
| | |
| | then inside vim run: |
| | |
| | :PlugInstall or |
| | :PlugUpdate |
| | |
╚══════════════════════════════╩═════════════════════════════════════════════════════════════════════╝

## 1.2. Vifm

╔══════════════════════════╦═════════════════════════════════════════╗
| command | description |
╠══════════════════════════╬═════════════════════════════════════════╣
| | |
╠═╣ Preview ╠═════╣ |
| | |
| w | Preview on the alternate pane |
| e | Preview on the current pane |
| q | Quit preview |
| CTRL+w z | Quit all preview modes |
| SHIFT+TAB | Switch to preview tab inorder to scroll |
╚══════════════════════════╩═════════════════════════════════════════╝

## 1.3. ZSH tricks

╔═══════════════════════════╦══════════════════════════════════════════════════════════════╗
| aliases | Desc |
╠═══════════════════════════╬══════════════════════════════════════════════════════════════╣
| | |
| **Escape Sequences** | |
| Esc-.(period) | Insert the last argument of the previous command line. |
| . | Repeat to retrieve arguments from earlier lines. |
| man -k randr | List all man pages that include a specific word. |
| look echo ~/.zshrc | Prints only the first word on the matching lines. |
| watch -n 3 ps -aux X | Prints only the first word on the matching lines. |
| stat -c '%n %a' ~/.zshrc | Provides information about the file with ═c you can specify |
| | which fields you want to show: %n name, %a access rights |
| | |
╠═╣ Shortcut keys ╠═════╬═════╣ |
| | |
| ctrl + h | Shows this file using vim |
| | |
╚═══════════════════════════╩══════════════════════════════════════════════════════════════╝

## 1.4. Custom aliases:

╔════════════════════════╦══════════════════════════════════════════════════════════════╗
| aliases | Desc |
╠════════════════════════╬══════════════════════════════════════════════════════════════╣
| **Help Pages** | |
| help | Displays this help page. |
| h | Grep history for a specific keyword |
| zdoc | Opens zsh pdf document. |
| **App Openers** | |
| idea | Opens a file or folder in IntelliJ Idea |
| subl | Opens a file or folder in sublime texteditor |
| atom | Opens a file or folder in atom texteditor |
| **Operations** | |
| ds | Calculates subfolder sizes in a directory |
| . | **EQ:** to 'du ═hd 1' |
| Make a file executable | |
| . | **EQ:** eq. to `chmod u+x` |
| rgrep | Search current folder for a specific keyword |
| . | including all subfolders |
| . | **Usage:** $ rgrep alias |
| . | **EQ:** `grep ══color=always ═R ═i "$1" ‖ less;` |
| rfind | |
| . | **Usage:** `$ rfind mac.sh` |
| . | **EQ:** `find . ═iname "*$1*" ‖ grep ═i "$1" ══color=always` |
| dq | query installed packages and list their files |
| **Usage:** $ dq ls | |
| extract | extracts a file into the destination folder using `tar` |
| . | **Usage:** `$ extract x.tar "/your/destination"` |
| . | **EQ:Usage:** `tar xf $1 ═C $2;` |
| **Web Search** | |
| google | Search Google for a specific term |
| ddg | Search DuckDuckGo for a specific term |
| ducky | Search DuckDuckGo for a specific term (I'm feeling lucky) |
| bing | Search Bing for a specific term |
| wiki | Search Wikipedia for a specific term |
| youtube | Search Youtube for a specific term |
| news | Search Google news for a specific term |
| map | Search Google maps for a specific term |
| image | Search images.google.com for a specific term |
╚════════════════════════╩══════════════════════════════════════════════════════════════╝

## 1.5. zsh shortcuts

╔════════════════════════╦══════════════════════════════════════════════════════════════╗
| Shortcuts | Desc |
╠════════════════════════╬══════════════════════════════════════════════════════════════╣
| ALT + h | Display help(info) on the first word of the line |
| | |
| ALT + . | Cycle through previous parameter in history |
| ALT + p | Cycle through previous statements |
| ALT + n | Cycle through next statements |
| | |
| ALT + f | Complete next word using previous statement/Jump to next wrd |
| ALT + b (+b) | Jump back one word |

| ESC + b (\eb) | Jump back one word |
| META + b (M-b) | Jump back one word |
| ALT + c | [fzf] Show fzf dropdown for all files in the current path |
| CTRL + x + b | Match bracket |
| | |
| Esc + v | Edit command line with vim ( Esacape then v ) |
| CTRL + x + e | Edit command line with vim ( ctrl + x then e ) |
| CTRL + grave | Edit command line with vim ( ctrl + `)` |
| | |
| ALT + SHIFT + r | Go to REPLACE mode |
| ALT + i | Go to INSERT mode |
| | |
| ALT + u | Change next word to upper case |
| ALT + l | Change next word to lower case |
| ALT + SHIFT + m | Insert return without executing |
| ALT + ' | Quote line |
| ALT + " | Quote region ( from start to cursor pos ) |
| | |
| ALT + d | Delete next word |
| CTRL + w | Delete pervious word |
| CTRL + k | Delete from cursor pos to the end of the line |
| CTRL + u or CTRL + _ | Delete the whole line |
| | |
| CTRL + e | Go to the end of the line |
| CTRL + a | Go to the begining of the line |
| CTRL + b | Backward delete char |
| CTRL + h | Backspace! |
| | |
| ALT + ? | Replace and execute `which` for the current starting cv .g |
| ALT + x | execute═named═cmd widget would be called |
| CTRL + j | Accept line |
| CTRL + m | Accept line |
| | |
╠═╣ Custom shortcuts ╠══╬═════╣ |
| | |
| | |
| ALT + s | Git status for the current folder |
| ALT + w | Switch to different theme |
| ALT + k | Kill the whole line |
| ALT + v | Edit the current line in vim |
| | |
╚════════════════════════╩══════════════════════════════════════════════════════════════╝

## 1.6. ZLE :

╔════════════════════════╦══════════════════════════════════════════════════════════════╗
| Commands | Desc |
╠════════════════════════╬══════════════════════════════════════════════════════════════╣
| zle -la | List all available widgets |
| bindkey | List all key mappings |
| bindkey -M vicmd | List all key mappings in vicmd mode |
| bindkey -v | V emulation mode |
| bindkey -e | Emacs emulation mode |
| | |
| bindkey '^m' | Shows a keybinding for a keymap in this case CTRL + m |
| bindkey -M viins 'b' | Shows a keybinding for Vi insert mode |
| bindkey -M vicmd 'b' | Shows a keybinding for Vi command line mode |
| bindkey -M emacs 'b' | Shows a keybinding for Emacs mode |
| | |
| '\e' | Stands for |

| '^' | Stands for |

| | |
╠════════════════════════╩════════════════════════╦═════════════════════════════════════╣
| bindkey -s '\es' '^Ugit status^M' | bind alt+s to git status |
| bindkey "^X^E" edit-command-line | bind c-x x-e to edit by vim (emacs)|
| bindkey "^X^E" edit-command-line | bind c-x x-e to edit by vim (emacs)|
| bindkey -M vicmd v edit-command-line | bind Esc-v to edit by vim (vimode) |
╠════════════════════════╦════════════════════════╩═════════════════════════════════════╣
| Esc-: | Shows execute named command prompt and you can run widgets |
╠════════════════════════╩══════════════════════════════════════════════════════════════╣
| https://github.com/zsh-users/zsh-completions/blob/master/zsh-completions-howto.org |
| |
| |
╚═══════════════════════════════════════════════════════════════════════════════════════╝

## 1.10.1 Other

╔════════════════════════╦══════════════════════════════════════════════════════════════╗
| Commands | Desc |
╠════════════════════════╬══════════════════════════════════════════════════════════════╣
| | |
| help | Displays this help page. |
| h | Grep history for a specific keyword |
| zdoc | Opens zsh pdf document. |
| mann | Opens https://manned.org manual page for the command |

| mank | Opens https://www.mankier.com manual page for the command |

╚════════════════════════╩══════════════════════════════════════════════════════════════╝

## 1.10.2 Useful manual pages

╔════════════════════════╦══════════════════════════════════════════════════════════════╗
| Commands | Desc |
╠════════════════════════╬══════════════════════════════════════════════════════════════╣
| | |
| mann zshexpn | Manual page for zsh expansions |
╚════════════════════════╩══════════════════════════════════════════════════════════════╝

- - -

Creation date: _2018/09/03_