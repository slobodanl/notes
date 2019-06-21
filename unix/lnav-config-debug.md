_Written by: Reza Shams Amiri_
# lnav config debug

To debug `lnav` configuration, the best online tool that I found is [debuggerex.com][HWDC]

## _Example_{.f2}: finding out what is not working with curity config
Curity IDP has a [git repo][GCLLAOFTCIS] providing log formats for their software. When I tried it against the logs provided, I couldn't make it work and trouble shooting was realy hard and confusing. Here, I will write a step by step how to, inorder to conquere the problems ahead:

1. Make `lnav` produce debug information when starting up, use :
   _Write lnav logs to `/tmp/lnav.out`_{.ct}
   ``` sh
   lnav /var/log/curity/server.log -d /tmp/lnav.out
   ```
   This will cause a logfile being created at `/tmp/lnav.out` which tells what is happening with `lnav` when it tries to pars the log
1.    

# References:
1. [www.debuggex.com][HWDC]
2. [GitHub - curityio/lnav: Lnav add-ons for the Curity Identity Server][GCLLAOFTCIS]
* * *
Creation date: _2019-06-21_

[HWDC]: https://www.debuggex.com/

[GCLLAOFTCIS]: https://github.com/curityio/lnav
[GCLLAOFTCIS]: https://github.com/curityio/lnav