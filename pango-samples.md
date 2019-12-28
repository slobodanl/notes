# Pango-Samples

# colors
Pango supports named colors as well as normal RGB colors. See the following reference for named colors:
[Web colors - Wikipedia][WCW]

``` sh
<span color='Beige' background='LightSlateGray'>A text in Beige</span>
```

# markup renderer
use `pango-view tmp/pango-test.markup --hinting full --markup`

``` sh
dunstify -a "beeper" "Test #$RANDOM" "Here goes Pango Markup:<br><span bgcolor='#00FF007F' foreground='#00FF00'><small>http://www.google.com</small></span>"
```

* * *
2018-01-28 12:24:59

[WCW]: https://en.wikipedia.org/wiki/Web_colors