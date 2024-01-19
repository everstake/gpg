## How to encrypt your message for Everstake

- [1. Creating new keypair](#creating-new-keypair)
- [2. Import Everstake public key](#import-everstake-public-key)
- [3. Encrypting your vulnerability report](#encrypting-your-vulnerability-report)
- [4. Vulnerability reporting guidelines](#vulnerability-reporting-guidelines)

### Creating new keypair

```bash
$ gpg --full-gen-key
```

Choose RSA algorithm and 4096 keysize.


### Import Everstake public key
In order to encrypt a file for another user as well as to verify their
signatures, we need their public key.

You can use one of the following methods to import Everstake's [public key](https://keyserver.ubuntu.com/pks/lookup?search=0xdc4086e9056c17234d62a44e302f408b14f95372&fingerprint=on&op=index):
```bash
$ gpg --import everstake-public-gpg.asc

$ gpg --keyserver hkps://keyserver.ubuntu.com --recv-keys dc4086e9056c17234d62a44e302f408b14f95372
```

#### PGP Key info
Double-check the key before encrypting -  [**everstake-public-gpg.asc**](https://everstake.one/security/everstake-public-gpg.asc)

  ```text
  pub   rsa4096 2022-05-27 [SC] [expires: 2027-05-26]
        DC4086E9056C17234D62A44E302F408B14F95372
  uid           [ unknown] Everstake <security@everstake.one>
  sub   rsa4096 2022-05-27 [E] [expires: 2027-05-26]
  ```

### Encrypting your vulnerability report 

After the public key has been imported, you can encrypt a file for us:
```bash
$ gpg -r security@everstake.one -e <some-file>
```

### Vulnerability reporting guidelines 

Please follow vulnerability reporting guidelines on our [website](https://everstake.one/report-vulnerability).
