# Todotxt.Md

## Apps:

1. [Todour | nerdur.com][TNC]
    ``` sh
    ﰲ Todour    
    ```

# Internal commands:

``` sh
ﰲ t lsa
ﰲ t ls
ﰲ t ls +queue

ﰲ t rm <item number>
ﰲ t del <item number>

ﰲ t edit <item number>

ﰲ t done <item number>

ﰲ t undo
ﰲ t undo <item number>

ﰲ t archive

#  List all tasks by project 
ﰲ t lsgp

# Project view
ﰲ t pv
```

__aa__{.ct}
``` sh
ﰲ t aa +queue "document todo txt"

    107 2019-06-03 +queue document todo txt
    TODO: 107 added.
    107 (A) 2019-06-03 +queue document todo txt
    TODO: 107 prioritized (A).
```

__lsprj__{.ct}
``` sh
ﰲ t lsprj
    ...
    +tothink
    +unix
    +userapi
    +wiki
    +work
```
__last__{.ct}
``` sh
ﰲ t last
    ...
    102 2019-06-03 Why have you eaten!!!! :<  +queue
    103 2019-06-03 2019-05-06   +queue get an ebike
    104 (A) 2019-06-03 +wiki Add a blob reference link to the pages
    --
    TODO: 10 of 104 tasks shown
```
# [Todo.sh Add on Directory · todotxt/todo.txt-cli Wiki · GitHub][TSAODTTTCWG]:
List your Todo.sh add-ons here. Include a short description and a link to the 
GitHub repository or other location.

## [inkarkat](https://github.com/inkarkat/todo.txt-cli-ex/tree/master/actions): inkarkat actions

### browse: Searches for URLs of web resources in the task text and
``` sh
t browse
t browse 17
```
### latest: Displays the last added open (all with -a) tasks"
Tasks without a date are ignored.
``` sh
t latest
t latest wiki
``` 
### projectview/pv: Show taks grouped by projects
``` sh
t pv
t projectview
t pv read
```
## [addp](https://github.com/todotxt/todo.txt-cli/tree/addons/.todo.actions.d): add with priority or marked as done
It allows to add an item with priority, aa, ab, ac, ad aliases are added as
shortcuts to addp:
``` sh
t aa +wiki "(#__) add service builder/remover/disabler for specific git repo"
t ab +wiki "this task would be prioritized as B"
t ac +wiki "this task would be prioritized as C"
t ad +wiki "this task would be prioritized as D"
```

## [graph](https://github.com/timpulver/todo.txt-graph): Visualize done tasks
Graph displays bar charts showing the number of completed tasks per day.

``` sh
t graph 
t graph 23 # visualize last 123 days
```

## [cd](http://github.com/dhein/todo.txt-cli/blob/pub-addons/cd): display directory paths
Outputs the command necessary to change the current directory to the directory 
holding the todotxt files, the directory holding add-ons or the directory holding 
the configuiration file.

``` sh
t cd
cd /home/existme/Dropbox/Apps/todotxttdi
```

## [due](http://github.com/rebeccamorgan/due): list tasks by due date
Lists tasks by due date; by default tasks that are overdue or due today. Optionally 
add an argument to display tasks due in the next n days. 
Assumes tasks are added with the key `due:YYYY-MM-DD`.

``` sh
t due
t due 7
```

## [birdseye/be](http://github.com/ginatrapani/todo.txt-cli/tree/addons): your productivity report
A Python script birdseye.py (called with the birdseye action) analyzes the 
todo.txt and done.txt files to generate a report of completed and incomplete 
items in every context and project. (Requires Python and both birdseye.py and 
birdseye files to run.)
``` sh
t birdseye
t be
```
## [mit](https://github.com/codybuell/mit): Most Important Task
addon to help you track your Most Important Tasks.

```
$ todo.sh mit today go do something    # use today or tomorrow to create a mit
$ todo.sh mit friday stash millions    # use a day of week to create a mit
$ todo.sh mit mon water the garden     # use an abbreviated day of week to create a mit
$ todo.sh mit 2012.09.17 buy github    # use specific date to create a mit
$ todo.sh mit -h                       # get some help
$ todo.sh mit                          # display all mits
  Past Due:
    do something @home (12)
  Today:
    fix something @work (14)
$ todo.sh mit @home                    # display all mits in specified context
  Past Due:
    do something @home (12)
```
MIT now has support for adding MIT’s to a month, quarter or year! See the project page for details

## [pomodoro](https://github.com/metalelf0/pomodori-todo.txt)
``` bash
t pom ls
t pom log

t pom plan 2 3
t pom add 2
t pom start 2
```

## [xp](https://github.com/gr0undzer0/xp)
print a readable guide of your accomplishments.
```
  todo.sh xp [-oh] days
          days: Number of days ago.

    Options:
          o : Omit days on which no tasks were commited.
          h : Print this help message.

t xp 2
```

## cli-plugins [todo-cli-plugins](https://github.com/Thann/todo-cli-plugins)

### view/v
Show todo items containing TERM, grouped by OPTION, and displayed in priority 
order. If no TERM provided, displays entire todo.txt. The original idea and 
script is derived from projectview by Paul.

``` sh
t v project
t v project wiki
t v context
t v date +wiki
t v 4weeks
t v -3days
```
### top : Lists as many items as can fit in the terminal, no wrapping or scrolling.
works just like list but truncates the list to fit in the terminal without scrolling or wrapping.
say you have 20 lines visible at a time in your terminal run `todo.sh top` and you’ll see the top 16 tasks.
most useful when set as the default command with: `TODOTXT_DEFAULT_ACTION`

``` sh
t top
```

### lately
lately [days]
Generate a list of recently completed tasks. Per default lately lists tasks that
were completed during the last seven days. With an optional argument, 
number of days, that can be overridden to show more or less.

``` sh
t lately
t lately 10
```

### edit: A simple tool to quickly edit one task in todo.txt.  
If ITEM given, edits the task. (Requires Bash 4+)
Otherwise Edits SRC with $EDITOR 
Optional argument (file name) specify the source file.

``` sh
t edit 44
```

## [donow](https://github.com/clobrano/todo.txt-cli/tree/master/todo.actions.d)
Donow add-on allows to keep track of the total time spent on an activity

``` sh
t ls
t donow 44
```

## [chcon:](https://github.com/kunkku/todo.txt-cli-chcon) change context
Chcon allows fast replacement or deletion of the context tag (and whatever follows that in the task description).

``` sh
$ t chcon 56 @office
56 upgrade servers @waiting
TODO: Replaced task with:
56 upgrade servers @office

$ t chcon 56
56 upgrade servers @office
TODO: Replaced task with:
56 upgrade servers
```

## [rmf:](https://github.com/samuelsnyder/rmf-todo.txt) remove from file
Plugin for todo.sh for applying the "rm" action, which either removes a specified line, or a term within that line, to any file in the todo directory

``` sh
t rmf todo.txt 01
Delete '(C) 2016-02-12 Why we drop our passions @tothink'?  (y/n)
n
TODO: No tasks were deleted.
```

* * *
2018-08-25 14:51:14

[TNC]: https://nerdur.com/todour-pl/
[TSAODTTTCWG]: https://github.com/todotxt/todo.txt-cli/wiki/Todo.sh-Add-on-Directory