_Written by: Reza Shams Amiri_
# Argument parser

_Argument Parser_{.ct}
``` python
import argparse

parser = argparse.ArgumentParser(description='Webscraper')
parser.add_argument('-u', '--url', metavar='URL', help='Site to scrap')
parser.add_argument('-s', '--scrap', metavar='NAME:XPATH', help='Scraping pattern', required=True, nargs='+')
parser.add_argument('-v', '--verbose', help='increase output verbosity', action='count', default=0)

args = parser.parse_args()

if args.verbose:
    print('verbosity turned on to %s' % args.verbose)
```
Sample outputs
```
./argpars.py 1
usage: argpars.py [-h] [-u URL] -s NAME:XPATH [NAME:XPATH ...] [-v]
argpars.py: error: the following arguments are required: -s/--scrap
```

``` 
./argpars.py -s test -vv
verbosity turned on to 2
```


* * *
Creation date: _2019-02-22_
