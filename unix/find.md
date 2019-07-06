# Unix find

1. Find by **name**:
   1. exact name
      ``` sh
      find . -name testfile.txt
      ```
   1. partial name
      ``` sh
      find /home -name *.jpg
      ```
   1. **ignore case**
      ``` sh
      find . -iname ".db"
      ```
1. Find by **filetype**
   1. **empty files**
       ``` sh
       find . -type f -empty
       ```
   1. **directories**
      ``` sh
      find . -type d
      ```
   1. **symbolic links**
      ``` sh
      find . -type l
      ```
1. Find by **owner**
   ``` sh
   find . -owner root
   ```
1. **Delete**
   ``` sh
   find . -name "*.bak" -delete
   find . -name ".DS_Store" -delete
   ```
1. **Size**
   ``` bash
   find . -xdev -type f -size +100M
   ```
1. **print**
   When using it with `-exec` if you supply `-print`, the filename will be also printed after running the exec
   ``` sh
   find . -type f -exec grep "example" '{}' \; -print
   ```

## find `-exec`
It's important to include `\;` at the end of exec if you want to supply more arguments to `find`
``` sh
find . -exec echo 'File is: {}' \;
find . -name "rc.conf" -exec chmod o+r '{}' \;
```
## find xargs
``` sh
find . -type f -print | xargs -I{} echo "[{}]"
find . -type f -print X echo "[{}]"
```
-----------------------------------------
2018-05-27 01:03:53
