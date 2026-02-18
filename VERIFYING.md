# Verifying Template Integrity

Keystone templates ship with a SHA-256 checksum manifest
(`.keystone/checksums.txt`) and a GPG detached signature
(`.keystone/checksums.txt.sig`). This guide explains how to verify both.

## Public Key

**Fingerprint:** `799D 1DC8 D477 4935 B557 D9EA C634 6E75 5DD4 C21A`

```plain
-----BEGIN PGP PUBLIC KEY BLOCK-----

mDMEaZQL6BYJKwYBBAHaRw8BAQdArL0+f0eQFzWdyHBrHSC+a0wnZ9i5Pv9W/ED0
6sf4pVi0LUtleXN0b25lIFNpZ25pbmcgS2V5IDxzaWduaW5nQGtuaWdodC1vd2wu
ZGV2PoiTBBMWCgA7FiEEeZ0dyNR3STW1V9nqxjRudV3UwhoFAmmUC+gCGyMFCwkI
BwICIgIGFQoJCAsCBBYCAwECHgcCF4AACgkQxjRudV3UwhqvqAEAzTd4SbE4P3qz
70bElYseXYbqCZYQvhg01h7vLgNlTYEA+gPwlTxECX1VTbtXk/SXqWRga7Ti4aUe
IwpuTBEfGhIO
=uxOb
-----END PGP PUBLIC KEY BLOCK-----
```

## Steps

1. **Import the public key** — copy the key block above into a file (e.g.
   `keystone.pub`) and import it:

   ```bash
   gpg --import keystone.pub
   ```

2. **Verify the signature** — from the template root:

   ```bash
   gpg --verify .keystone/checksums.txt.sig .keystone/checksums.txt
   ```

   A successful result shows `Good signature from "Keystone Signing Key"`.

3. **Verify file checksums** — from the template root:

   macOS:

   ```bash
   shasum -a 256 -c .keystone/checksums.txt
   ```

   Linux:

   ```bash
   sha256sum -c .keystone/checksums.txt
   ```

   Every line should report `OK`.

## What These Files Are

| File | Purpose |
| ---- | ------- |
| `.keystone/checksums.txt` | SHA-256 hash of every file in the template |
| `.keystone/checksums.txt.sig` | GPG detached signature over `checksums.txt` |

The signature proves the checksums were produced by the Keystone release
pipeline. The checksums prove no files were modified after assembly.

## Why the Key Is Not Bundled

A public key shipped inside the artifact it verifies creates circular
trust — an attacker who compromises the template repo can replace the key,
re-sign, and pass verification. Distributing the key here, independently
of the template repos, breaks that cycle.
