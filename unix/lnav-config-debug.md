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
1. Since we are debugging `server log format`, open `~/.lnav/formats/installed/curity.json` and fomd `curity_server_log` section:
   _curity.json_{.ct}
   ``` json
   {
       "curity_server_log" : {
        "title" : "Curity server log format",
        "description" : "The format for Cuirty Identity Server logs",
        "regex" : {
            "std-2.0" : {
                "pattern" : "(?<timestamp>\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}:\\d{3}[-+]\\d{4}) +(?<alert_level>(TRACE|DEBUG|INFO|WARN|ERROR)) {1,2}((?<request_id>[^ ]{8,})?| ) ((?<session_id>([^ ]+))?| ) {(?<thread>[-\\w]+)} +(?<class>[\\w.]+)(:(?<line>\\d+))? +(?<body>.*)"
            }
        },
        "json" : false,
        "timestamp-format" : [ "%Y-%m-%d %H:%M:%S", "%Y-%m-%dT%H:%M:%S:%L%z" ],
        "multiline" : true,
        "level-field" : "alert_level",
        "opid-field" : "request_id",
        "level" : {
            "error" : "ERROR",
            "warning" : "WARN",
            "info" : "INFO",
            "debug" : "DEBUG",
            "trace" : "TRACE"
        },        
        "value" : {
            "alert_level" : {
                "kind" : "string",
                "identifier" : true
            },
            "request_id" : {
                "kind" : "string",
                "identifier" : true
            },
            "session_id" : {
                "kind" : "string",
                "identifier" : true
            },
            "thread" : {
                "kind" : "string"
            },
            "class" : {
                "kind" : "string",
                "identifier" : true
            },
            "line" : {
                "kind" : "integer",
                "identifier" : true
            },
            "body" : {
                "kind" : "string"
            }
        },
        "sample" : [
            {
                "line" : "2017-05-08T16:03:48:038+0200 WARN    {conf-Thread-3-30} se.curity.identityserver.config.data.JDBISqlDataAccessConfigurationSetting:65 Running with connection pool disabled. This will severely impact performance, and is only recommended for tested and debugging purposes"
            },
            {
                "line" : "2017-05-08T16:04:42:728+0200 TRACE 76ff899e  {req-61} se.curity.identityserver.util.resources.FileSystemResourceLocator:85 Looking for file system resource at path: assets/images/favicon-normal.png"
            },
            {
                "line" : "2017-05-08T16:04:42:006+0200 DEBUG e6683295 38763868 {req-51} se.curity.identityserver.web.RouteHandler:140 Selected Locale: 'en'. Default Locale: 'en'."
            }
        ]
    }
   ```


# References:
1. [www.debuggex.com][HWDC]
2. [GitHub - curityio/lnav: Lnav add-ons for the Curity Identity Server][GCLLAOFTCIS]
* * *
Creation date: _2019-06-21_

[HWDC]: https://www.debuggex.com/

[GCLLAOFTCIS]: https://github.com/curityio/lnav
[GCLLAOFTCIS]: https://github.com/curityio/lnav