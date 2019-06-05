_Written by: Reza Shams Amiri_
# reminders
Syncing reminders
``` uml
skinparam {
    DefaultFontName Aapex
    BackgroundColor FFFFEE
    DefaultFontSize 16
}
actor Utility as u
Participant Keep as keep
Participant ReminderAPI as rapi
autoactivate on
u->keep: sync()
== get all changes from reminder API==
keep->rapi: list()
rapi-->keep: changes
== Pars tasks ==
keep->keep #ff5500: _parseTasks(<b>changes</b>)

```

* * *
Creation date: _2019-06-04_
