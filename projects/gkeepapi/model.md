_Written by: Reza Shams Amiri_
# model

``` uml
skinparam {
    DefaultFontName Aapex
    BackgroundColor FFFFEE
    DefaultFontSize 16
}
class Node{
    Node parent
    id
    server_id
    parent_id
    type
    _sort
    _version
    _children
    timestamp
    settings
    annotations
    _generateId(cls, tz)
    _load(self,raw)
    save(self, clean=True)
}
class Root{
}

Node <|-- Root
```

* * *
Creation date: _2019-06-05_
