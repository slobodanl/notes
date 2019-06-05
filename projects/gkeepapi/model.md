_Written by: Reza Shams Amiri_
# model

``` uml
skinparam {
    DefaultFontName Aapex
    BackgroundColor FFFFEE
    DefaultFontSize 16
}
class Element{
    - _find_discrepancies(raw)
    + load(raw)
    - _load(raw)
    + save(clean=True) : {}
    <&eye> dirty
}
enum BlobType{
    Audio
    Image
    Drawing
}
class NodeBlob{
    - _TYPE: BlobType
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
}
BlobType <- NodeBlob: _TYPE
class NodeAudio{
    _TYPE = BlobType.Audio
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
}
class NodeImage{
    _TYPE = BlobType.Image
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
}
class NodeDrawing{
    _TYPE = BlobType.Drawing
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
}
Element <|-- NodeBlob
NodeBlob <|-- NodeAudio
NodeBlob <|-- NodeImage
NodeBlob <|-- NodeDrawing
class Node{
    + Node parent
    + id
    + server_id
    + parent_id
    + type
    - _sort
    - _version
    - _children
    + timestamp
    + settings
    + annotations
    - _generateId(cls, tz)
    - _load(raw)
    + save(clean=True)
    <&pencil> sort
    <&pencil> text
    <&pencil> trashed
    <&pencil> children
    + get(node_id)
    + append(node, dirty=True)
    + remove(node, dirty=True)
    <&eye> new
    <&eye> dirty
}
class Root{
    ID = 'root'
    <&eye> dirty :False
}
class Blob{
    _blob_type_map: NodeBlob
    ID = 'root'
    
    + {static} from_json(raw) : NodeBlob
    - _load(raw)
    + save(clean=True)
}

Node <|-- Root
Node <|-- Blob
```

* * *
Creation date: _2019-06-05_
