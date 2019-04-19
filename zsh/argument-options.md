_Written by: Reza Shams Amiri_
# Argument options

If you want to optionalize your script one dynamic way of dealing with arguments is using `shift` and a `case` switch, as follows:

``` sh
#!/bin/zsh
while [ $# -gt 0 ]; do    # Until you run out of parameters . . .
   case "$1" in
      "-p")
         PROMPT="${AND}prompt=${cZ}login"
         ;;
      "-acr")
         ACR=1
         ;;
      "-s")
         shift
         server=$1
         ;;
   esac
   shift
done
```

* * *
Creation date: _2019-04-19_
