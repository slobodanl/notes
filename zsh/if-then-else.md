_Written by: Reza Shams Amiri_
# if then else

Depending on the shell the `if-then-else` expression should have different formats:

``` sh
#!/bin/zsh

if [[ -n $ACR ]]; then
   ACR_VALUES="$ACR"
fi

# short form
[[ -n $ACR ]] && ACR="urn:se:curity:authentication:html-form:html"
```

* * *
Creation date: _2019-04-19_
