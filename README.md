# Everstake security PGP key
Use this key to encrypt vulnerability reports sent to **security@everstake.com**.
- [1. Creating new keypair](#creating-new-keypair)
- [2. Import Everstake public key](#import-everstake-public-key)
- [3. Verify the key](#verify-the-key)
- [4. Encrypting your vulnerability report](#encrypting-your-vulnerability-report)
- [5. Key transition](#key-transition)
- [6. Vulnerability reporting guidelines](#vulnerability-reporting-guidelines)
### Creating new keypair
```bash
$ gpg --full-gen-key
```
Choose RSA algorithm and 4096 keysize, or the default ECC (Curve 25519).
Export your public key so we can send you an encrypted reply:
```bash
$ gpg --armor --export you@example.com > my-key.asc
```
### Import Everstake public key
In order to encrypt a file for another user as well as to verify their
signatures, we need their public key. Use one of the following methods:
```bash
$ gpg --import everstake-public-gpg.asc
$ curl -fsSL https://everstake.com/security/everstake-public-gpg.asc | gpg --import
$ gpg --keyserver hkps://keys.openpgp.org --recv-keys 2377CD73030BFC1EF8C5D6DAA5B4CBBB3367F984
```
### Verify the key
Double-check the fingerprint before encrypting -
[**everstake-public-gpg.asc**](https://everstake.com/security/everstake-public-gpg.asc):
```bash
$ gpg --fingerprint security@everstake.com
```
```text
pub   ed25519 2026-10-27 [SC] [expires: 2031-10-26]
      2377 CD73 030B FC1E F8C5  D6DA A5B4 CBBB 3367 F984
uid   Everstake Security <security@everstake.com>
sub   cv25519 2026-10-27 [E] [expires: 2031-10-26]
```
The same fingerprint is published at
[everstake.com/report-vulnerability](https://everstake.com/report-vulnerability)
and in [security.txt](https://everstake.com/.well-known/security.txt).
### Encrypting your vulnerability report
After the public key has been imported, you can encrypt a file for us:
```bash
$ gpg --encrypt --armor -r security@everstake.com report.txt
```
Send the resulting `report.txt.asc` to security@everstake.com.
Attach `my-key.asc` if you want an encrypted reply.
### Key transition
On 2026-10-27 Everstake replaced its previous key:
```text
pub   rsa4096 2022-05-27 [SC]
      DC40 86E9 056C 1723 4D62  A44E 302F 408B 14F9 5372
uid   Everstake <security@everstake.one>
```
The previous key has certified the new key, and the transition statement
[transition-2026.txt.asc](transition-2026.txt.asc) is signed by both keys:
```bash
$ gpg --verify transition-2026.txt.asc
```
Do not use the previous key for new reports.
### Vulnerability reporting guidelines
Please follow the vulnerability reporting guidelines on our
[website](https://everstake.com/report-vulnerability).
