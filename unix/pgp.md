_Written by: Reza Shams Amiri_
# pgp
1. **List all keys**
    List all your pgp keys
    ``` 
    gpg --list-secret-keys

    /home/existme/.gnupg/pubring.kbx
    --------------------------------
    sec   rsa2048 2018-06-09 [SC]
          D7XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX1B
    uid           [ultimate] Reza <existme@gmail.com>
    ssb   rsa2048 2018-06-09 [E]
    ```
1. **Export & import key**
    ``` sh
    gpg --export-secret-keys D7XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX1B > ~/my-private-key.asc
    ```
    Copy the file to your other machine
    ``` sh
    gpg --import my-private-key.asc
    gpg: key 040XXXXXXXXXXXXB: public key "Reza <existme@gmail.com>" imported
    gpg: key 040XXXXXXXXXXXXB: secret key imported
    gpg: Total number processed: 1
    gpg:               imported: 1
    gpg:       secret keys read: 1
    gpg:   secret keys imported: 1
    ```
1. **Encrypt a file using one of your keys**
    ``` sh
    gpg --encrypt ~/gmail-pass
    ```
    And you will get
    ``` sh
    You did not specify a user ID. (you may use "-r")

    Current recipients:

    Enter the user ID.  End with an empty line: reza

    Current recipients:
    rsa2048/EXXXXXXXXXXXXX41 2018-06-09 "Reza <existme@gmail.com>"

    Enter the user ID.  End with an empty line: 
    ```
    by pressing enter again
    An encrypted file named `~/gmail-pass.gpg` will be created
1. **Decrypting an encrypted gpg file**
    ``` sh
    gpg -q --for-your-eyes-only --no-tty -d ~/gmail-pass.gpg
    ```

## Troubleshooting
### incase you get `gpg: no writable keyring found: eof`
``` sh
sudo ls -al ~/.gnupg
```

* * *
Creation date: _2019-07-28_
