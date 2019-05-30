_Written by: Reza Shams Amiri_
# classes

## Properties
``` python
class Person:
    def __init__(self, name):
        self._name = name

    @property
    def name(self):
        print('Getting name')
        return self._name

    @name.setter
    def name(self, value):
        print('Setting name to ' + value)
        self._name = value

    @name.deleter
    def name(self):
        print('Deleting name')
        del self._name

p = Person('Adam')
print('The name is:', p.name)

p.name = 'John'

del p.name
```

## References:
1. [Python's Class Development Toolkit - YouTube][PSCDTY]

* * *
Creation date: _2019-05-30_

[PSCDTY]: https://youtu.be/HTLu2DFOdTg