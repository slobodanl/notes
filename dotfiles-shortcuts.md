_Written by: Reza Shams Amiri_

# Existme-dotfiles scripts, aliases and shortcuts

## Help Pages

| aliases | Desc |
| ------- | ---- |
| help      | Displays this help page. |
| h         | Grep history for a specific keyword |
| zdoc      | Opens zsh pdf document. |
| y         | uses `yelp` for displaying man page |
|           |  `y i3` |
| mann      | uses `https://www.manned.org/$1` |
| mank      | uses `https://www.mankier.com/1/$1` |
| manm      | uses `https://manpages.org/$1/$page` |
| manc      | uses `https://linux.cn/man$page/$1.$page.html` |
| cht       | cheat sheet from [https://cht.sh](https://cht.sh) |
|           |  `cht tar` |
|           |  `cht python read json from file` |
|           |  `cht python random list elements` |
|           |  `cht --shell` <kbd>enter</kbd> `cd python` <kbd>enter</kbd> |

## App Openers

| aliases | Desc |
| ------- | ---- |
| ~~idea~~  | Opens a file or folder in IntelliJ Idea |
| ii        | Opens a file or folder in IntelliJ Idea |
| subl      | Opens a file or folder in sublime texteditor |
| atom      | Opens a file or folder in atom texteditor |

## Operations

| aliases | Desc |
| ------- | ---- |
| ds        | Calculates subfolder sizes in a directory |
|           | **EQ:** to `du -hd 1` |
| vf        | find the file in `$PATH` and open it in bim |
|           |  `vf ,build` |
| yesno     | Simple yes no function  |
|           |  `yesno "Wanna quit?"` |
| ex        | Make a file executable |
|           | **EQ:** eq. to `chmod u+x` |
| elocate   | Searches for executable files using locate |
|           |  `elocate vim` |
| ff        | Search current folder for a partial filename |
|           |  `$ ff .json` |
| rgrep     | Search current folder for a specific keyword |
|           | including all subfolders |
|           |  `$ rgrep alias` |
|           | **EQ:** `grep --color=always -R -i "$1" ‖ less;` |
| rfind     | Finds a file in path, if path is not mentioned uses current folder|
|           |  `rfind mac.sh` |
|           |  `rfind mac.sh /home/existme` |
|           | **EQ:** `find $2 -iname "*$1*" | grep -i "$1" --color=always` |
| extract   | extracts a file into the destination folder using `tar` |
|           |  `$ extract x.tar "/your/destination"` |
|           | **EQ:** `tar xf $1 -C $2;` |
| ,ls       | Show the file permission in numerical format|
| ,lv       | Locate a file, show found files as selection, edit with vim|
| ,s        | Show systemctl services in rofi menu and lets see the logs or|
|           | do other stuff with them|
|           |  `,s NetworkManager.service lnav` |
|           |  `,s` <kbd>enter</kbd> |
|,scan-local| Use nmap to scan local network |
|           | **EQ:** `sudo nmap -sn 192.168.0.0/24` |
| ,speed    | use `aria2c` for speedtest |
|           |  `,speed` <kbd>enter</kbd> |
| ,switch-prompt | Switch the shell prompt to a new theme |
| ,theme    | Switch GTK theme |
| hh        | Hacker news rss |
| kk        | Filter process based on a keyword and let you kill them |
|           |  `kk dunst` <kbd>enter</kbd> |
| latestAccessedFiles | least latest accessed files (can be used for debugging)|
|           |  `latestAccessedFiles -m 40 /var/log`    # latest modified files in /var/log within 40 mins |
| list-desktop-files | search in *.desktop for `categories` and `exec`|
| mem       | Shows free memory |
| net-listout | Shows outgoing connections |
| net-listout | Shows outgoing connections |

## Configuration

| aliases | Desc |
| ------- | ---- |
| ,deploy-config   | Copy the MyDotFiles to a remote machine |
|                   |  `,install-config myserver:` |

## Web Search

| Command | Desc |
| ------- | ---- |
| google    | Search Google for a specific term |
| ddg       | Search DuckDuckGo for a specific term |
| ducky     | Search DuckDuckGo for a specific term (I'm feeling lucky) |
| bing      | Search Bing for a specific term |
| wiki      | Search Wikipedia for a specific term |
| youtube   | Search Youtube for a specific term |
| news      | Search Google news for a specific term |
| map       | Search Google maps for a specific term |
| image     | Search images.google.com for a specific term |

##  Commands for working with Packages!

| Command | Desc |
| ------- | ---- |

## Browser lunch commands
| Command | Desc |
| ------- | ---- |
| ,chromium-presentation | Lunches Chrome brower using `/.config/chromium-presentation` data dir|
| ,browser              | Lunch new tab in the current browser |
|                       |  `,browser google.com` |
| **Specific Apps**     |  |
| ,a-gmail              | Lunch browser for `gmail.com` |
| ,a-soundcloud         | Lunch browser for `soundcloud.com` |
| ,a-twitter            | Lunch browser for `twitter.com` |
| ,a-whatsapp           | Lunch browser for `web.whatsapp.com` |
| ,a-youtube            | Lunch browser for `youtube.com` |
| **Translation**       |  |
| ,es                   | `EN-SE` translation using surf |
| ,se                   | `SE-EN` translation using surf |

## Misc commands

| Command | Desc |
| ------- | ---- |
| ,build        | download, pull, and build some popular packages from Github.|
|               |examples: i3, dunst, surf... **Usage:** `,build i3`  |
| ,font-test    | Print out all supported codepages for the current font |
| ,font-c2u     | Converts a character to it's unicode equivalent |
|               |  `,font-c2u ` |
| ,toggle-notifications | Enable/disable desktop notifications |
|  |  |
| takenote <kbd>tab</kbd> | edit ~/notes/*.md files using vim and fzf  |

## Utility commands
| Command | Desc |
| ------- | ---- |
|_File related_{.f1}||
| `,show-permission` | show access rights of a file/folder in the octal value format |
|||
|_Package_{.f1}||
| `,pkg-graph`    | Visualizes the dependency graph for a package |
|               |  `,dpkg-graph ssh` |
| `,pkg-info`     | Shows information about a **not installed** package |
|               |  `,pkg-info wmpinboard` |
|               |  `,pkg-info` <kbd>enter</kbd> |
| `,pkg-info{.hl}`| Tries to find a file within **not installed** packages |
|               |  `,pkg-find otfinfo` |
|               |  `,pkg-find` <kbd>enter</kbd> (very slow) |
|               | **EQ:** `apt-file search $1` |
| `asf`           | Uses `fzf` to list all files **installed** by packages |
|               |  `asf` <kbd>Enter</kbd> and search for `_apt` |
| `aps`         | Alias for `aptitude search`, searches in not installed packages |
|               |  `aps pinboard`|
| `dq`            | Query an installed package and list its files |
|               |  `dq yelp` |
|||
|_Service_{.f1}||
| `sc`     | `sc` is alias for `sudo PATH=\"$PATH\" -E systemctl --no-pager `|
| `,s`     | Show/rotate logs for different services using a rofi dialog|
| `,ss`     | services state change script |
|||
| _Misc_{.f1}||
| `,se`     | Translate Swedish -> English using Google translate |
| `,es`     | Translate English -> Swedish using Google translate |
|||
| `,speed` | Check the speed of download and upload using speedtest.net|
|||
|_Theme_{.f1}||
| `,fonts`        | Show all installed fonts in a rofi dialog |
|               |  `,fonts i3` |
| `,font-test`        | Show all characters in nerd fonts |
| `,icon`         | Pick and apply a new icon set to WM. If that's not enough change using `lxappearance` (restart thunar)|
| `,switch-prompt` | Switch prompt in a rofi dialog|
|||
| _Symbols_{.f1} ||
| `,symbol-delimeter` | Shows the shell prompt with several delimiters |
| `,dotcolors` |show dots in various colors|
|||
|_Sound related_{.f1}||
| `,select-sound-card` | Select different sound card options in a rofi dialog |
| `toggle-loudness` | Toggle override loudness for headphones |
| `,audible-convert`| Convert audible file to mp3 and store it in Dropbox|
| `,ding` ||
- - -

Creation date: _2018-10-28_