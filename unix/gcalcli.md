_Written by: Reza Shams Amiri_

# gcalcli

## Configuration
Config file is located at: `~/.gcalclirc`

__`~/.gcalclirc`__{.ct}
``` sh
--defaultCalendar=existme@gmail.com
```

## arguments

| Command | Description |
| ------- | ----------- |
| gcalcli --refresh list | Refresh gcalcli calendars |
| calcli list | List calendars |
| gcalcli agenda | Shows week agenda |
| gcalcli calw | Show calendar for the week |
| gcalcli calw 4 | Show calendar for 4 weeks |
| gcalcli calm | Show calendar for the month |
| gcalcli search <searchphrase> | Search calendar for the event |
|  |  |

## Samples

``` sh
$ gcalcli quick 'test from gcalcalendar'
$ gcalcli quick 'Dinner with Eric 7pm tomorrow'
$ gcalcli quick 'Call Sokrati at 12:00 tomorrow'
$ gcalcli quick '03/15 7:00am Standup'
$ gcalcli agenda
Wed Mar 13   9:38pm  test from gcalcalendar -> Reza A
Thu Mar 14  12:00pm  Call Sokrati
Thu Mar 14   7:00pm  Dinner with Eric
Fri Mar 15   7:00am  Standup
```

__complete add sample__{.ct}
``` sh
gcalcli --calendar 'Eric Davis'
        --title 'Analysis of Algorithms Final' 
        --where UCI 
        --when '12/14/2012 10:00' 
        --who 'foo@bar.com' 
        --who 'baz@bar.com' 
        --duration 60 
        --description 'It is going to be hard!' 
        --reminder 30 
        add
```
        
References:

- [GitHub - insanum/gcalcli: Google Calendar Command Line Interface][GIGGCCLI]

- - -

Creation date: _2019-03-13_
[GIGGCCLI]: https://github.com/insanum/gcalcli