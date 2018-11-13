_Written by: Reza Shams Amiri_
# scratch

## Hacking rugged adapter

``` ruby
gitrepo = wiki.repo.git.instance_variable_get(:@repo)
gitrepo.fetch('origin','master')
origin_master = gitrepo.branches['origin/master']
last_commit = origin_master.target
gitrepo.reset(origin_master.target, :hard)
```

* * *
Creation date: _2018-11-13_
