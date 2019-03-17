# Using git-crypt

Installation:
```bash
sudo apt install git-crypt 

brew install git-crypt
```

## Using a shared key [ref][SDIYRWGCSTP]
1. `sudo apt install git-crypt`
2. enter your repo and type: `git-crypt init`
3. `git-crypt export-key ~/gitcrypt.key`
4. (Share this file with collaborators)
5. On the collaborator machine run: `git crypt unlock ~/gitcrypt.key`

## Adding encrypted files
1. Inside repo: `vim .gitattributes`
2. __.gitattributes__{.ct}
    ``` sh
    .key filter=git-crypt diff=git-crypt
    ```
3. As a result of the above all files with extension `.key` will be encrypted.
4. To check which files are encrypted run: `git-crypt status -e`   
    ``` sh
    encrypted: .mutt/aliases.key
    ```
5. Commit the file and it will be automatically encrypted and decrypted!

## Using GPGs (need rewising) [ref][GANGKGH]
1. generate a gpg key**
    ``` bash
    # for local generation
    gpg --gen-key

    # for remote generation without access to gui:
     gpg --gen-key --pinentry-mode loopback --passphrase <passphrase>
    ```
1. list gpg keys**
    ``` bash
    gpg --list-secret-keys --keyid-format LONG
    ```
1. from the list of gpg keys, copy gpg key ID. see example below**
    ``` bash
    gpg --list-secret-keys --keyid-format LONG

    /Users/hubot/.gnupg/secring.gpg
    ------------------------------------
    sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
    uid                          Hubot
    ssb   4096R/42B317FD4BA89E7A 2016-03-10
    ```
    here the key id is `3AA5C34371567BD2`

1. extract the key. see the example below:**
    ```bash
    gpg --armor --export 3AA5C34371567BD2

    # Prints the GPG key ID, in ASCII armor format
    ```
1. Copy your GPG key,   
    **beginning with** `-----BEGIN PGP PUBLIC KEY BLOCK-----`
    and **ending with** `----END PGP PUBLIC KEY BLOCK-----.`   
    or simply either use:

    ```bash
    gpg --armor --export 3AA5C34371567BD2 | xclip
    ```
    or:

    ```bash
    gpg --armor --export 3AA5C34371567BD2 > /tmp/key.acs
    ```

1. On server machine [Encrypting secrets in a Git repository using git-crypt · Robert Knight][ESIAGRUGCRK]



-----------------------------------------
2018-02-19 20:23:49

[GANGKGH]: https://help.github.com/articles/generating-a-new-gpg-key/
[ESIAGRUGCRK]: https://robertknight.me.uk/posts/git-crypt-intro/
[SDIYRWGCSTP]: https://www.schibsted.pl/blog/devops/securing-data-with-git-crypt/