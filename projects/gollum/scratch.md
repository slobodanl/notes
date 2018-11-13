_Written by: Reza Shams Amiri_
# Scratch Pad

## Hacking rugged adapter
The rugged adapter is tricky to work with, since it's a wrapper around a `c` library. To find it look for `git_layer_rugged.rb` file. There are mainly two different gems that you need to understand
1. rugged (`/var/lib/gems/2.5.0/gems/rugged-0.27.4/`)
2. gollum-rugged_adapter (`/var/lib/gems/2.5.0/gems/gollum-rugged_adapter-0.4.4/lib/rugged_adapter/git_layer_rugged.rb`)

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
