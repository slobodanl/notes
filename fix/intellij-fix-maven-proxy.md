_Written by: Reza Shams Amiri_
# intellij fix maven proxy

According to this [Stack Overflow question][JICCTUHPFMSO]:

Inside the IntelliJ IDEA `Settings`(which is found under File > Settings)
1. Navigate to `Maven` > `Importing`
   1. "VM options for importer". Append the following to whatever already exists there:
    ``` sh
    -DproxySet=true -DproxyHost=http://wwwproxy.axis.com -DproxyPort=3128
    ```
1. Do the same under `Maven` > `Runner`


* * *
Creation date: _2019-07-25_

[JICCTUHPFMSO]: https://stackoverflow.com/a/26483623/161312