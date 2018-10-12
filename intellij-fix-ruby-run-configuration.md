_Written by: Reza Shams Amiri_
# intellij fix ruby run configuration

To be able to run Ruby files from intelliJ, make sure that first both these folders are writable?

``` sh
s chmod -R a+rw /var/lib/gems/2.5.0 

# **Maybe** this is also required, maybe!
s chmod -R a+rw /usr/local/lib/site_ruby/2.5.0 
```

* * *
Creation date: _2018/10/12_
