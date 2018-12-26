_Written by: Reza Shams Amiri_
# Intellij Focus Issue

Caret is not returned back after switching focus (i3 wm)

A youtrack [issue][ISSUE] exists as it's suggested there, go to `Help`  `Edit Custom Properties...` and add the following line

``` sh
suppress.focus.stealing=false
```

Then restart IntelliJ.

* * *
Creation date: _2018-12-26_

[ISSUE]: https://youtrack.jetbrains.com/issue/IDEA-194124