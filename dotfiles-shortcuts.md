_Written by: Reza Shams Amiri_

# dotfiles shortcuts
## Help Pages
| aliases | Desc |
| ------- | ---- |
| help | Displays this help page. |
| h | Grep history for a specific keyword |
| zdoc | Opens zsh pdf document. |

## App Openers
| aliases | Desc |
| ------- | ---- |
| idea | Opens a file or folder in IntelliJ Idea |
| subl | Opens a file or folder in sublime texteditor |
| atom | Opens a file or folder in atom texteditor |

## Operations
| aliases | Desc |
| ------- | ---- |
| ds        | Calculates subfolder sizes in a directory |
|           | **EQ:** to 'du -hd 1' |
| ex        | Make a file executable |
|           | **EQ:** eq. to `chmod u+x` |
| rgrep     | Search current folder for a specific keyword |
|           | including all subfolders |
|           | **Usage:** $ rgrep alias |
|           | **EQ:** `grep --color=always -R -i "$1" ‖ less;` |
| rfind     |  |
|           | **Usage:** `$ rfind mac.sh` |
|           | **EQ:** `find . -iname "*$1*" | grep -i "$1" --color=always` |
| dq        | query installed packages and list their files |
|           | **Usage:** $ dq ls |
| extract   | extracts a file into the destination folder using `tar` |
|           | **Usage:** `$ extract x.tar "/your/destination"` |
|           | **EQ:Usage:** `tar xf $1 -C $2;` |

## Web Search
| Command   | Desc |
| --------- | ---- |
| google    | Search Google for a specific term |
| ddg       | Search DuckDuckGo for a specific term |
| ducky     | Search DuckDuckGo for a specific term (I'm feeling lucky) |
| bing      | Search Bing for a specific term |
| wiki      | Search Wikipedia for a specific term |
| youtube   | Search Youtube for a specific term |
| news      | Search Google news for a specific term |
| map       | Search Google maps for a specific term |
| image     | Search images.google.com for a specific term |

- - -

Creation date: _2018-10-28_