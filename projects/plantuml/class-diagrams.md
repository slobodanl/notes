_Written by: Reza Shams Amiri_
# Class Diagrams

1. [Class Diagram syntax and features][CDSAF]

__class diagrams__{.ct}
``` sh
enum BlobType{
    Audio
    Image
    Drawing
}

class Element{
    - _find_discrepancies(raw)
    + load(raw)
    - _load(raw)
    + save(clean=True) : {}
    <&eye> dirty
}
class NodeBlob{
    - _TYPE: BlobType
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
    <&pencil> category:Category
    <&eye> links: [WebLink...]
    + {static} from_json(raw) : NodeBlob
}
class Item{
    + itemName
}
BlobType <- NodeBlob: _TYPE
NodeBlob ->"0..*" Item : items
Element <|-- NodeBlob
```

``` uml
skinparam {
    DefaultFontName Aapex
    BackgroundColor FFFFEE
    DefaultFontSize 16
}
enum BlobType{
    Audio
    Image
    Drawing
}

class Element{
    - _find_discrepancies(raw)
    + load(raw)
    - _load(raw)
    + save(clean=True) : {}
    <&eye> dirty
}
class NodeBlob{
    - _TYPE: BlobType
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
    <&pencil> category:Category
    <&eye> links: [WebLink...]
    + {static} from_json(raw) : NodeBlob
}
class Item{
    + itemName
}
BlobType <- NodeBlob: _TYPE
NodeBlob ->"0..*" Item : items
Element <|-- NodeBlob

```

* * *
Creation date: _2019-06-05_

[CDSAF]: http://plantuml.com/class-diagram