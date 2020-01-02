_Written by: Reza Shams Amiri_
# keyring password prompt

If you are getting prompted for password when running `gnome-key-daemon`, one possible (not safe) workaround is to remove the key ring password by resetting the password in the two following application to empty:

1. `gnome-keyring-daemon`
2. `kwalletmanager5`

For more information visit: [GNOME/Keyring - ArchWiki][GKA]

* * *
Creation date: _2020-01-02_

[GKA]: https://wiki.archlinux.org/index.php/GNOME/Keyring