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

# [docopt](https://github.com/docopt/docopt) : Pythonic command line arguments parser
Installation:
``` python
sudo -H pip install docop
```
Using
``` python
"""Example of program with many options using docopt.
Usage:
  options_example.py [-hvqrf NAME] [--exclude=PATTERNS]
                     [--select=ERRORS | --ignore=ERRORS] [--show-source]
                     [--statistics] [--count] [--benchmark] PATH...
  options_example.py (--doctest | --testsuite=DIR)
  options_example.py --version
Arguments:
  PATH  destination path
Options:
  -h --help            show this help message and exit
  --version            show version and exit
  -v --verbose         print status messages
  -q --quiet           report only file names
  -r --repeat          show all occurrences of the same error
  --exclude=PATTERNS   exclude files or directories which match these comma
                       separated patterns [default: .svn,CVS,.bzr,.hg,.git]
  -f NAME --file=NAME  when parsing directories, only check filenames matching
                       these comma separated patterns [default: *.py]
  --select=ERRORS      select errors and warnings (e.g. E,W6)
  --ignore=ERRORS      skip errors and warnings (e.g. E4,W)
  --show-source        show source code for each error
  --statistics         count errors and warnings
  --count              print total number of errors and warnings to standard
                       error and set exit code to 1 if total is not null
  --benchmark          measure processing speed
  --testsuite=DIR      run regression tests from dir
  --doctest            run doctest on myself
"""

arguments = docopt(__doc__, version='1.0.0rc2')
print(arguments)

```


* * *
Creation date: _2019-02-22_
