_Written by: Reza Shams Amiri_
# zathura

## Shortcuts
| Key | Shortcut |
| --- | -------- |
| <kbd>CTRL</kbd>+<kbd>r</kbd> | Reverse color |
| <kbd>s</kbd> | Fit document based on width |
| <kbd>a</kbd> | Fit document based on Height |
| <kbd>d</kbd> | View pages side by side |
| <kbd>+/-</kbd> | Zooming |
| <kbd>f</kbd> | Fullscreen mode |
| <kbd>o</kbd> | Open document |
| <kbd>r</kbd> | Rotate 90 degrees |


## Config
`~/.config/zathura/zathurarc`nn

## Renderers
__epub viewer (mupdf)__{.ct}
``` 
sudo add-apt-repository ppa:spvkgn/zathura-mupdf
sudo apt-get install zathura zathura-pdf-mupdf
```
__normal pdf viewer (poppler)__{.ct}
``` 
sudo apt install zathura-pdf-poppler
```

## References
1. [zathurarc: A document viewer][ZADV]


* * *
Creation date: _2019-06-13_

[ZADV]: https://www.carta.tech/man-pages/man5/zathurarc.5.html