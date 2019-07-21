_Written by: Reza Shams Amiri_
# network open ports lsof

Use `lsof` for finding who is listening to port 88

``` sh
lsof -i -P -n | grep 8080

# lsof -i -P -n G 8080
```

* * *
Creation date: _2019-07-21_
