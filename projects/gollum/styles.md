_Written by: Reza Shams Amiri_
# Markdown styles

## Are style actually supported in Markdown?
Styles are not yet part of markdown spec and they are still as draft. For more information regarding style support in markdown see [Consistent attribute syntax][CASECD].

## How to define styles?
Both editor and the viewer in this wiki support styles. Styles are defined as follows:

``` sh
{.style1 .style2 ...}
```
You should always put them after the block that you want to style see the following examples:

``` md
This is my style{.hl}
```

This is my style{.hl}

``` md
This is an _inline_{.hl} style
```

This is an _inline_{.hl} style

* * *
## Custom styles defined for this wiki

### Info styles:

####  `{.info}`

Using info style you can gain reader attention and make them to focus on a specific requirement.{.info}

####  `{.info .warn}`

Warnin style, can be used to warn the reader about specific requirement {.info .warn}

####  `{.info .ok}`

To give the reader an affirmation about the current section, you can use the **ok** style.{.info .ok}

####  `{.info .danger}`

To inform the reader about an important step, upi can use the `danger` style.{.info .danger}

### Other styles:
####  `{.hl}`

Use `{.hl}` to _highlight_{.hl} a block.

####  `{.i-danger}`

`{.i-danger}` can be used to show an icon in between of your text... _like this_{.i-danger}. All these decorations can be used to make user see a specific important section!

####  `{.note}`

Note is another type style that can be used for gaining user attention{.note}

#### `{.note .red}`

Also you can use it in red color!{.note .red}

#### `{.note .green}`

Also you can use it with green color!{.note .green}

####  `{.note .pink}`

And pink! I don't know why I added this color!{.note .pink}

* * *
## Using styles with lists
for lists it's important to have one _line break_{.hl} after the list and then use style information. Example:

``` md
1. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam nec lectus odio. Etiam arcu diam, luctus a pellentesque sit amet, volutpat in felis. Ut ac interdum nunc. 
2. Sed ante mi, scelerisque ac bibendum sed, fringilla vel erat. Duis fringilla, odio eget porta fermentum, tortor risus imperdiet leo, ut egestas sapien metus eu 
3. turpis. Proin ac eros diam. In fringilla ante ac felis lobortis, nec dictum lacus condimentum. Suspendisse a odio quis lectus venenatis maximus convallis ac ante.

{.info .ok}
```

1. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam nec lectus odio. Etiam arcu diam, luctus a pellentesque sit amet, volutpat in felis. Ut ac interdum nunc. 
2. Sed ante mi, scelerisque ac bibendum sed, fringilla vel erat. Duis fringilla, odio eget porta fermentum, tortor risus imperdiet leo, ut egestas sapien metus eu 
3. turpis. Proin ac eros diam. In fringilla ante ac felis lobortis, nec dictum lacus condimentum. Suspendisse a odio quis lectus venenatis maximus convallis ac ante.

{.info .ok}
* * *
Creation date: _2018/09/30_

[CASECD]: https://talk.commonmark.org/t/consistent-attribute-syntax/272/119