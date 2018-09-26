# Filters
# Filters

The gollum pattern extraction works like this based on `/var/lib/gems/2.5.0/gems/gollum-lib-4.2.7/lib/gollum-lib/filter/emoji.rb`

``` uml
collections filter_chain as fc
entity "Gollum::Filter::Emoji" as emoji
fc -> emoji: extract(data)
emoji -> emoji: mark data to be replaced
== After all filters extracted their data ==
fc -> emoji: process(data)
emoji -> emoji: replace marked data with html
```

* * *
Creation date: _2018/09/27_
