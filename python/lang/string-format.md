_Written by: Reza Shams Amiri_

# String formats ([ref][61SCSOP349D])
``` 
format_spec ::=  [[fill]align][sign][#][0][width][,][.precision][type]
fill        ::=  <any character>
align       ::=  "<" | ">" | "=" | "^"
sign        ::=  "+" | "-" | " "
width       ::=  integer
precision   ::=  integer
type        ::=  "b" | "c" | "d" | "e" | "E" | "f" | "F" | "g" | "G" | "n" | "o" | "s" | "x" | "X" | "%"
```


| Type | Meaning |
| ---- | ------- |
| s | String format. This is the default type for strings and may be omitted. |
| None | The same as 's'. |
| b | Binary format. Outputs the number in base 2. |
| c | Character. Converts the integer to the corresponding unicode character before printing. |
| d | Decimal Integer. Outputs the number in base 10. |
| o | Octal format. Outputs the number in base 8. |
| x | Hex format. Outputs the number in base 16, using lower- case letters for the digits above 9. |
| X | Hex format. Outputs the number in base 16, using upper- case letters for the digits above 9. |
| n | Number. This is the same as `'d'`, except that it uses the current locale setting to insert the appropriate number separator characters. |
| None | The same as `'d'`. |


## Samples
``` python
name = "bob"
err = 1237898
a = 10
b = 23

print("Hello, %s" % name)
# Hello, bob

print("Error, %x" % err)
# Error, 12e38a

print("Hello %s, there is a 0x%x error" % (name, err))
# Hello bob, there is a 0x12e38a error

print('Hey {name}, there is a 0x{errno:x} error!'.format(name=name, errno=err))
# Hey bob, there is a 0x12e38a error!

print(f"Hello {name}, there is a 0x{err} error, sum = {a + b}")
# Hello bob, there is a 0x1237898 error, sum = 33

print(f"Hey {name}, there's a {err:#x} error!")
# Hey bob, there's a 0x12e38a error!


print('{:<30}'.format('left aligned'))
print('{:>30}'.format('right aligned'))
print('{:^30}'.format('centered'))
print('{:*^30}'.format('centered'))  # use '*' as a fill char
# left aligned
#                  right aligned
#            centered
# ***********centered***********


print('{:+f}; {:+f}'.format(3.14, -3.14))
print('{: f}; {: f}'.format(3.14, -3.14))  # show a space for positive numbers
print('{:-f}; {:-f}'.format(3.14, -3.14))  # show only the minus -- same as '{:f}; {:f}'
# +3.140000; -3.140000
#  3.140000; -3.140000
# 3.140000; -3.140000

print("int: {0:d};  hex: {0:x};  oct: {0:o};  bin: {0:b}".format(42))
# int: 42;  hex: 2a;  oct: 52;  bin: 101010
print("int: {0:d};  hex: {0:#x};  oct: {0:#o};  bin: {0:#b}".format(42))
# int: 42;  hex: 0x2a;  oct: 0o52;  bin: 0b101010

print('{:,}'.format(1234567890))
# 1,234,567,890

print('Correct answers: {:.2%}'.format(19 / 22))
# Correct answers: 86.36%

d = datetime.datetime(2010, 7, 4, 12, 15, 58)
print('{:%Y-%m-%d %H:%M:%S}'.format(d))
# 2010-07-04 12:15:58

for align, text in zip('<^>', ['left', 'center', 'right']):
    print('{0:{fill}{align}16}'.format(text, fill=align, align=align))
# left<<<<<<<<<<<<
# ^^^^^center^^^^^
# >>>>>>>>>>>right

octets = [192, 168, 0, 1]
print('{:02X}{:02X}{:02X}{:02X}'.format(*octets))
# C0A80001

width = 5
for num in range(5, 12):
    for base in 'dXob':
        print('{0:{width}{base}}'.format(num, base=base, width=width), end=' ')
    print()

#  5     5     5   101
#  6     6     6   110
#  7     7     7   111
#  8     8    10  1000
#  9     9    11  1001
# 10     A    12  1010
# 11     B    13  1011
```

- - -

Creation date: _2019-02-25_

[61SCSOP349D]: https://docs.python.org/3.4/library/string.html