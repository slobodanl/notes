_Written by: Reza Shams Amiri_
# Scratch Pad

## Hacking rugged adapter

``` ruby
gitrepo = wiki.repo.git.instance_variable_get(:@repo)
gitrepo.fetch('origin','master')
origin_master = gitrepo.branches['origin/master']
last_commit = origin_master.target
gitrepo.reset(origin_master.target, :soft)
```

Some other thigs that were tried:

``` ruby
repo.checkout(repo.head.name,:strategy => :force)
repo.checkout('origin/master',:strategy => :force).inspect
repo.refs.first.inspect 
reference=origin_master.resolve
commit=origin_master.target
repo.checkout_index(origin_master.resolve)
repo.checkout_tree(origin_master.target)
repo.reset(origin_master.target,:hard)
```
* * *
Creation date: _2018-11-13_
