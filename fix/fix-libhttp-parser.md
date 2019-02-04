_Written by: Reza Shams Amiri_
# fix libhttp parser

If you get :   

    libhttp_parser.so.2.7.1: cannot open shared object file

Do the following workarounds:
1. Get it from [Ubuntu – Package Search Results -- libhttp-parser2.1][UPSRLP1]
    1. Install it
2. Update your ruby environment   
    ``` sh
    sudo gem install rubygems-update
    sudo update_rubygems
    sudo gem update --system
    sudo gem update
    ```
3. 


* * *
Creation date: _2019-02-04_

[UPSRLP1]: https://packages.ubuntu.com/search?keywords=libhttp-parser2.1&searchon=names