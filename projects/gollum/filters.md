# Filters
# Filters

The gollum pattern extraction works like this based on `/var/lib/gems/2.5.0/gems/gollum-lib-4.2.7/lib/gollum-lib/filter/emoji.rb`

``` uml
control filter_chain as fc
entity "Gollum::Filter::Emoji" as emoji
collections "other filters: FA,FB,FC,..." as of
fc -> emoji: extract(data)
emoji -> emoji: mark data to be replaced
fc -> of: extract(data)...
of -> of: markTheirOwnData(data)
== After all filters extracted their data ==
fc -> emoji: process(data)
emoji -> emoji: replace marked data with html
fc -> of: process(data)
of -> of: replaceTheirOwnData(data)
== Data now contains the rendered document ==
```
The `filter_chain` itself is initiated within the config file and the filters are executed from left to right:
``` ruby
wiki_options = {
    :filter_chain => [ :Emoji, :FA, :FB, :FC, :Render]
}
```
* * *
Creation date: _2018/09/27_
