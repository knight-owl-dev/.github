# Knight Owl

> Simple things should be simple, and difficult things should be possible.

Crafting tools and systems that help creators think, write, and build
with structure and intent.

**By developers, for creators:**

> Respect your user's time. Every workaround we skip in the
> infrastructure is a hoop the user has to jump through. Do the long,
> proper thing once so users get a zero-friction experience. No hacks,
> no "just run this extra command", no documented workarounds for
> problems we can solve upstream. If a fix requires the user to act,
> the real fix hasn't shipped yet.

## Projects

| Repository | Description |
| ---------- | ----------- |
| [keystone-cli](https://github.com/knight-owl-dev/keystone-cli) | Command-line interface for Keystone |
| [keystone-template-core](https://github.com/knight-owl-dev/keystone-template-core) | Full template with local Docker image build |
| [keystone-template-core-slim](https://github.com/knight-owl-dev/keystone-template-core-slim) | Lightweight template using a prebuilt Docker image |
| [keystone-hello-world](https://github.com/knight-owl-dev/keystone-hello-world) | Sample project using the Keystone template |
| [homebrew-tap](https://github.com/knight-owl-dev/homebrew-tap) | Homebrew tap for Knight Owl tools |
| [apt](https://github.com/knight-owl-dev/apt) | Apt repository for Knight Owl packages |
| [devops](https://github.com/knight-owl-dev/devops) | Shared CI images and infrastructure |

## Signing Key

Keystone templates ship with a SHA-256 checksum manifest
(`.keystone/checksums.txt`) and a GPG detached signature. The public key
is bundled in each template and published here for independent verification.

```
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

Verify a template:

```bash
.keystone/verify.sh            # report results, always exit 0
.keystone/verify.sh --strict   # exit 1 on any failure
```

Learn more at [knight-owl.dev](https://knight-owl.dev).
