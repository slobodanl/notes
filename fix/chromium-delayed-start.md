_Written by: Reza Shams Amiri_
# chromium delayed start

After investigating with:

``` sh
strace chromium-browser 2>&1 | lnav
```

Found out that after accessing `libsecret-1.so.0` it waits for a long time. Searched it and ended up here: [16.04 - Chrome and Chromium are taking a long time to load - Ask Ubuntu][10CACATALTTLAU]

I realized that running

``` sh
$ gnome-keyring-daemon
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
```

Will fix the issue, but I need to see if this was a one time thing or I need to do this at startup.

* * *
Creation date: _2019-02-16_

[10CACATALTTLAU]: https://askubuntu.com/questions/911877/chrome-and-chromium-are-taking-a-long-time-to-load