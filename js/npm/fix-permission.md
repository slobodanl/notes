_Written by: Reza Shams Amiri_
# Resolving EACCES permissions errors when installing packages globally

Start your content here...

1. `mkdir ~/.npm-global`
1. `npm config set prefix '~/.npm-global'`
1. `export PATH=~/.npm-global/bin:$PATH`

Instead of steps 2, you can use the corresponding ENV variable (e.g. if you don’t want to modify ~/.profile):

``` sh
NPM_CONFIG_PREFIX=~/.npm-global
```

Try with:

    npm install -g jshint

[Source][TNE]
* * *
Creation date: _2018-12-26_

[TNE]: https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally