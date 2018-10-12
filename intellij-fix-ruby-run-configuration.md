_Written by: Reza Shams Amiri_
# Intellij - fix Ruby run configuration

To be able to run Ruby projects from intelliJ and enabling debuging, make sure that first both these folders are writable? ([ ref][RNGFEIRCFIRPSO])

``` sh
s chmod -R a+rw /var/lib/gems/2.5.0 

# **Maybe** this is also required, maybe!
s chmod -R a+rw /usr/local/lib/site_ruby/2.5.0 
```

You might also need to uninstall `debase-0.2.3.beta2` and installing `debase-0.2.2` by running the following command: ([ ref][IIDNFI6DDG])
``` sh
gem uninstall --user-install debase
```

* * *
Creation date: _2018/10/12_

[IIDNFI6DDG]: https://github.com/denofevil/debase/issues/64#issuecomment-421379092
[RNGFEIRCFIRPSO]: https://stackoverflow.com/questions/26592049/no-gemfile-found-error-in-run-configurations-for-intellij-ruby-plugin