_Written by: Reza Shams Amiri_
# Dumping python objects

## Using a dump function
``` python
def dump(obj):
    for attr in dir(obj):
        print("obj.%s = %r" % (attr, getattr(obj, attr)))

dump(myobj)
```
## pprint
``` python
from pprint import pprint
pprint(vars(your_object))
```

* * *
Creation date: _2019-02-24_
