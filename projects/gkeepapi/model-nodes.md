_Written by: Reza Shams Amiri_
# Nodes


``` uml
skinparam {
    DefaultFontName Aapex
    BackgroundColor FFFFEE
    DefaultFontSize 16
}

class Node{
    + Node parent
    + id
    + server_id
    + parent_id
    + type
    - _sort
    - _version
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
Node "0..*" <- Node: _children
class Root{
    ID = 'root'
    <&eye> dirty :False
}
class TopLevelNode{
    - _TYPE = None
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
    <&pencil> color
    <&pencil> archived
    <&pencil> pinned
    <&pencil> title
    <&eye> url
    <&eye> blobs: [Blob...]
}
class Blob{
    _blob_type_map: NodeBlob
    ID = 'root'
    
    + {static} from_json(raw) : NodeBlob
    - _load(raw)
    + save(clean=True)
}
class ListItem{
    + parent_item
    + parent_server_id
    + super_list_item_id
    + prev_super_list_item_id
    + _checked = False
    - _load(raw)
    + save(clean=True)
    + add(text, checked=False, sort=None) : Node
    + indent(node, dirty=True)
    + dedent(node, dirty=True)
    <&eye> subitems
    <&eye> indented
    <&pencil> checked
    - __str__()
}
Node <|-- Root
Node <|-- Blob
Node <|-- TopLevelNode
Node <|-- ListItem
Node "0..*" <-- ListItem: _subitems
```

* * *
Creation date: _2019-06-05_
