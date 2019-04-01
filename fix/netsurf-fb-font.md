_Written by: Reza Shams Amiri_
# netsurf fb font

`netsurf-fb` might give you the following error:
> Unable to initialise the font system
 
In such a scenario, according to this [thread][N36WBREAB] there are fonts missing in your system, if you run:

``` sh
 $ strace netsurf-fb 2>&1 G font
 
stat("/usr/share/fonts/truetype/ttf-dejavu", 0x7fff8165f780) = -1 ENOENT (No such file or directory)
stat("/usr/share/fonts/truetype/msttcorefonts", 0x7fff8165f780) = -1 ENOENT (No such file or directory)
write(2, "Unable to initialise the font sy"..., 37Unable to initialise the font system
```

So the problem is that `ttf-dejavu` fonts are not present in `/usr/share/fonts/truetype/`. 
1. First download the fonts from [this page][FD]
2. Extract them and put them inside `/usr/share/fonts/truetype/ttf-dejavu`       
    __It's important to have it in the exact same folder__{.info .warn}    
3. Run the following commands:
   ``` sh
   cd /usr/share/fonts/truetype/ttf-dejavu
   sudo fc-cache -rfv .
   ```

Now you should be able to run `netsurf-fb`!
* * *
Creation date: _2019-04-01_

[N36WBREAB]: http://eab.abime.net/showthread.php?t=84862
[FD]: https://fonts2u.com/download/dejavu-sans-oblique.family