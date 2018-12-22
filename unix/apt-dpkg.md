_Written by: Reza Shams Amiri_
# Unix Package information

1. **List all files** of an **installed** package  
    ``` sh
    dpkg -L thunar
    ```
1. **Find a package** which provides a **file**   
    ``` sh
    dpkg -S klauncher
    ```
1. **Show** package information for an **installed package**
    ``` sh
    dpkg -s kinit
    ```
1. **Show** package information for an **installed/not installed package**
    ``` sh
    aptitude show viruskiller
    ```

* * *
Creation date: _2018-11-10_
