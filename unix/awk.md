_Written by: Reza Shams Amiri_
# awk

## Samples:

_sample 1_{.ct}
``` sh
#! /usr/bin/awk -f
# This line is a comment

{ 
   if (length($0) > max) max = length($0) 
   # for (i = 1; i <= 7; i++) print int(101 * rand())
   print "Current Line: " NR
}
END {
   print max 
   print "Last line number (total lines):" NR
}
```


## Rules

1. The first block runs for each line
2. `$0`,`$1`,... are variables pointing to field nth of the line (like bash args)
3. The code associated with `END` executes after all input has been read; it’s the other side of the coin to `BEGIN`.


* * *
Creation date: _2019-01-29_
