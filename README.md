# Quick-start guide to GPG

## Creating new keys

First create a new keypair (private and public key):
```bash
$ gpg --full-gen-key
```

The user will be prompted to answer the following questions:
1. **Keypair:** RSA and RSA.
2. **Keysize:** 4096.
3. **Expiration date:** A period of years is enough most of the time. 
4. **Name and email address.**
5. **Comment:** Add a comment for the key's purpose.
6. **Passphrase**.


## Get information about keys

List all public keys:
```bash
$ gpg --list-keys
$ gpg --list-sigs   # list signatures
$ gpg --fingerprint # list fingerprints
```

List private (secret) keys:
```bash
$ gpg --list-secret-keys
```

## Import and export public keys

You can use one of the following methods to import Everstake's public key:
```bash
$ gpg --import everstake-public-gpg.asc

$ gpg --keyserver hkps://keyserver.ubuntu.com --recv-keys dc4086e9056c17234d62a44e302f408b14f95372
```
You can find the 'everstake-public-gpg.asc' file at https://everstake.one/gpg/everstake-public-gpg.asc


Export your public key to an ASCII file:
```bash
$ gpg -a -o your-public-gpg.asc --export <key-id>
```
If no `<key-id>` has been entered, all present keys will be exported.

In order to encrypt a documents for another user as well as to verify their
signatures, we need their public key.


## Encrypting and decrypting

After a public key has been imported, you can encrypt a file for us:
```bash
$ gpg -r security@everstake.one -e <some-file>
```

Decrypt a file that has been encrypted with our own public key:
```bash
$ gpg -o somefile.txt -d somefile.txt.gpg
```
