_Written by: Reza Shams Amiri_
# Pipes
## [I/O Redirection][IOR]
For [background][SDB22DNDNADN21ULSE]:
a **number 1** = standard out (i.e. **STDOUT**)
a **number 2** = standard error (i.e. **STDERR**)
if a number isn't explicitly given, then **number 1** is assumed by the shell (bash)
- `2>/dev/null`: Redirect **STDERR** to `/dev/null` (prevent from showing up on console)
- `|&`: Redirect **STDERR** and **STDOUT** to STDIN of piped command (this is an abbreviation for `2>&1 |`)
   _This operator is quite usefull specially when you want to redirect the output to an intractive editor or viewer. Ex: `,build |& vim -`<br>It prevents the editor from being corrupted_{.info}
- `&>/dev/null`: Redirect both **STDERR** & **STDOUT** to `/dev/null` (nothing shows up on console)
- `>/dev/null 2>&1`: The same as above but portable!
- `>/dev/null`: Redirect **STDOUT** to `/dev/null` (only STDERR shows on console)

## Exampless
_Pipe `jq` to `less`, with colour_{.ct}
``` sh
pinboard bookmarks |jq -C '.' |& less
```

* * *
Creation date: _2019-06-29_

[IOR]: http://www.tldp.org/LDP/abs/html/io-redirection.html
[SDB22DNDNADN21ULSE]: https://unix.stackexchange.com/a/70971/114816