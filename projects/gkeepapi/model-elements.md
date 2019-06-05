_Written by: Reza Shams Amiri_
# Elements

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
class NodeCollaborators{
    - _collaborators
    - __len__()
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
    + add(email)
    + remove(email)
    + all()

}
class NodeTimestamps{
    + TZ_FMT = '%Y-%m-%dT%H:%M:%S.%fZ'
    - _created
    - _deleted
    - _created
    - _updated
    - _edited
    <&wrench> _load(raw)
    <&wrench> save(clean=True)
    + {static} str_to_dt(cls, tzs) : datetime
    + {static} int_to_dt(cls, tz) : datetime
    + {static} dt_to_str(cls, dt) : string
    + {static} int_to_str(cls, tz) : string
    <&pencil> created
    <&pencil> deleted
    <&pencil> trashed
    <&pencil> updated
    <&pencil> edited
}
class Annotation{
    + id
    <&wrench> _load(raw)
    <&wrench> save(clean=True) : Annotation
    + {static} _generateAnnotationId(cls)
}
class NodeSettings{
    - _new_listitem_placement
    - _graveyard_state
    - _checked_listitems_policy
    <&wrench> _load(raw)
    <&wrench> save(clean=True) : Annotation
    <&pencil> new_listitem_placement
    <&pencil> graveyard_state
    <&pencil> checked_listitems_policy
}
Element <|-- NodeBlob
Element <|-- NodeAnnotations
Element <|-- NodeLabels
Element <|-- NodeCollaborators
Element <|-- NodeTimestamps
Element <|-- Annotation
NodeBlob <|-- NodeAudio
NodeBlob <|-- NodeImage
NodeBlob <|-- NodeDrawing

```

* * *
Creation date: _2019-06-05_
