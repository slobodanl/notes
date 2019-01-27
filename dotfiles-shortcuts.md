_Written by: Reza Shams Amiri_

# Existme-dotfiles scripts, aliases and shortcuts

## Help Pages

| aliases | Desc |
| ------- | ---- |
| help | Displays this help page. |
| h | Grep history for a specific keyword |
| zdoc | Opens zsh pdf document. |
| y | uses `yelp` for displaying man page |
|  | `y i3` |
| mann | uses `https://www.manned.org/$1` |
| mank | uses `https://www.mankier.com/1/$1` |
| manm | uses `https://manpages.org/$1/$page` |
| manc | uses `https://linux.cn/man$page/$1.$page.html` |

## App Openers

| aliases | Desc |
| ------- | ---- |
| ~~idea~~ | Opens a file or folder in IntelliJ Idea |
| ii | Opens a file or folder in IntelliJ Idea |
| subl | Opens a file or folder in sublime texteditor |
| atom | Opens a file or folder in atom texteditor |

## Operations

| aliases | Desc |
| ------- | ---- |
| ds        | Calculates subfolder sizes in a directory |
|           | **EQ:** to `du -hd 1` |
| vf        | find the file in `$PATH` and open it in bim |
|           | **EX:** `vf ,build` |
| yesno     | Simple yes no function  |
|           | **EX:** `yesno "Wanna quit?"` |
| ex        | Make a file executable |
|           | **EQ:** eq. to `chmod u+x` |
| elocate   | Searches for executable files using locate |
|           | **EX:** `elocate vim` |
| rgrep     | Search current folder for a specific keyword |
|           | including all subfolders |
|           | **Usage:** `$ rgrep alias` |
|           | **EQ:** `grep --color=always -R -i "$1" ‖ less;` |
| rfind     | Finds a file in path, if path is not mentioned uses current folder|
|           | **Usage:** `rfind mac.sh` |
|           | **Usage:** `rfind mac.sh /home/existme` |
|           | **EQ:** `find $2 -iname "*$1*" | grep -i "$1" --color=always` |
| extract   | extracts a file into the destination folder using `tar` |
|           | **Usage:** `$ extract x.tar "/your/destination"` |
|           | **EQ:Usage:** `tar xf $1 -C $2;` |

## Web Search

| Command | Desc |
| ------- | ---- |
| google | Search Google for a specific term |
| ddg | Search DuckDuckGo for a specific term |
| ducky | Search DuckDuckGo for a specific term (I'm feeling lucky) |
| bing | Search Bing for a specific term |
| wiki | Search Wikipedia for a specific term |
| youtube | Search Youtube for a specific term |
| news | Search Google news for a specific term |
| map | Search Google maps for a specific term |
| image | Search images.google.com for a specific term |

##  Commands for working with Packages!

| Command | Desc |
| ------- | ---- |
| ,pkg-graph |  Visualizes thedependency graph for a package |
|  | `,dpkg-graph ssh` |
| ,pkg-info |  Shows information about a not installed package |
|  | `,pkg-info wmpinboard` |
| asf | Uses `fzf` to list all files installed by packages |
|  | `asf` and search for `_apt` |
| aps | Alias for `aptitude search`, can search in package names |
| dq | query installed packages and list their files |
|  | **Usage:** `dq yelp` |

## Browser lunch commands
| Command | Desc |
| ------- | ---- |
| ,chromium-presentation | Lunches Chrome brower using `/.config/chromium-presentation` data dir|
| ,browser              | Lunch new tab in the current browser |
|                       | **Usage:** `,browser google.com` |
| **Specific Apps**     |  |
| ,a-gmail              | Lunch browser for `gmail.com` |
| ,a-soundcloud         | Lunch browser for `soundcloud.com` |
| ,a-twitter            | Lunch browser for `twitter.com` |
| ,a-whatsapp           | Lunch browser for `web.whatsapp.com` |
| ,a-youtube            | Lunch browser for `youtube.com` |
| **Translation**         |  |
| ,es                   | `EN-SE` translation using surf |
| ,se                   | `SE-EN` translation using surf |

## Misc commands

| Command | Desc |
| ------- | ---- |
| ,build | download, pull, and build some popular packages from Github.|
| |examples: i3, dunst, surf... **Usage:** `,build i3`  |
| ,fonts | Show all installed fonts in a rofi dialog |
|  | **Usage:** `,fonts i3` |
| ,font-test | Print out all supported codepages for the current font |
| ,font-c2u | Converts a character to it's unicode equivalent |
|  | **Usage:** `,font-c2u ` |
| ,emoji | Show emojis in a rofi dialog |

- - -

Creation date: _2018-10-28_