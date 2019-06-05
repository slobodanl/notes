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
class NodeLabels{
    - _labels
    - _load(raw)
    + save(clean=True)
    + add(label)
    + remove(label)
    + get(label_id)
    + all()
}
class NodeAnnotations{
    - _annotations
    - __len__()
    + {static} from_json(cls, raw) : Annotation
    + all():[Annotation...]
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
    - _get_category_node():Category
    <&pencil> category:Category
    <&eye> links: [WebLink...]
    + append(annotation): Annotation
    + remove(annotation)
    <&wrench> dirty
}
Element <|-- NodeBlob
Element <|-- NodeAnnotations
Element <|-- NodeLabels
NodeBlob <|-- NodeAudio
NodeBlob <|-- NodeImage
NodeBlob <|-- NodeDrawing

```

* * *
Creation date: _2019-06-05_
