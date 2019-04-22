_Written by: Reza Shams Amiri_
# if then else

Depending on the shell the `if-then-else` expression should have different formats:

## Single test
_sample single test_{.ct}
``` sh
#!/bin/zsh

if [[ -n $ACR ]]; then
   ACR_VALUES="$ACR"
fi

# short form
[[ -n $ACR ]] && ACR="urn:se:curity:authentication:html-form:html"
```
## Comparision
_sample equality_{.ct}
``` sh
#!/bin/zsh

if [[ $1 = "--wait" ]]; then
   echo "wait supplied"
fi
```
Please note that `=` is preferred over `==`, the later is used for pattern matching

## Arithmatic comparision
Use `-eq`, `-ne`, `-lt`, `-le`, `-gt`, or `-ge` only for arithmatic comparisions and when you are comparing numbers.
_these will not work with strings_{.info .warn}
* * *
Creation date: _2019-04-19_
