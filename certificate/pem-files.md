_Written by: Reza Shams Amiri_
# PEM files
1. Generate key unencrypted
    ``` sh
    openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:4096 -out key.pem
    ```
1. Generate key encrypted with password
    ``` sh
    openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:4096 -out key.pem -pass pass:mypassword123
    ```


## References:
1. [How to use OpenSSL: Hashes, digital signatures, and more | Opensource.com][HTUOHDSAMOC]
2. [Sign and verify text/files to public keys via the OpenSSL Command Line - Raymii.org][SAVTFTPKVTOCLRO]

* * *
Creation date: _2020-02-10_

[HTUOHDSAMOC]: https://opensource.com/article/19/6/cryptography-basics-openssl-part-2
[SAVTFTPKVTOCLRO]: https://raymii.org/s/tutorials/Sign_and_verify_text_files_to_public_keys_via_the_OpenSSL_Command_Line.html